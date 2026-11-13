# Firebase 安全規則（貼上用，永不過期）

> 活動型 App、無登入；規則設為「可讀可寫但不過期」，並對 group count 做 ≤15 驗證。
> 活動結束後可改回 `.read/.write: false` 關閉。

## 1) Realtime Database 規則
Console → Realtime Database → 規則(Rules) → 貼上 → 發布(Publish)

```json
{
  "rules": {
    ".read": true,
    ".write": true,
    "groups": {
      "$gid": {
        "count": {
          ".validate": "newData.isNumber() && newData.val() >= 0 && newData.val() <= 15"
        }
      }
    }
  }
}
```

## 2) Storage 規則（上傳圖片／PDF 用）
Console → Storage → 規則(Rules) → 貼上 → 發布

```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /uploads/{allPaths=**} {
      allow read: if true;
      allow write: if request.resource.size < 20 * 1024 * 1024
        && (request.resource.contentType.matches('image/.*')
            || request.resource.contentType == 'application/pdf');
    }
  }
}
```

## RTDB 資料結構（規劃）
```
/phase            0..5  主講者/後台控制的當前階段
/groups/{1..10}/count    各組已選人數（上限 15，transaction 搶位）
/players/{pKey}   {name, qu, bie, gender, groupId, title, ts}
/current/group    目前上台組別（階段4）
/scores/{gid}/{pKey}  {q1,q2,q3}  互評星數
/uploads/{gid}/...    作品檔案 URL（Storage）
```
