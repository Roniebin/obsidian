# 아이디/비번 방식으로 로그인하고 싶다면

- Next-auth 라이브러리 설정에서 Credentials provider를 선택 
- 다만 이 경우 session 방식 말고 강제로 JWT 방식만 사용하도록 셋팅되어있습니다

## **회원가입페이지에서 유저가 아이디/비번 제출하면**


``` javascript
(app/register/page.js)

export default function Register() { return (
<div> <form method="POST" action="/api/auth/signup"> 
<input name="name" type="text" placeholder="이름" /> 
<input name="email" type="text" placeholder="이메일" /> 
<input name="password" type="password" placeholder="비번" />
<button type="submit">id/pw 가입요청</button> 
</form> </div> ) }

```

## **서버는 그걸 DB에 저장**


#### 비번 암호화 할 라이브러리

npm install bcrypt



## 전송된 정보를 DB에 저장하는 서버기능

``` javascript
(pages/api/auth/signup.js)
import { connectDB } from "@/util/database"; 
import bcrypt from "bcrypt"; 
export default async function handler(요청, 응답) {
if (요청.method === "POST") { 
const hash = await bcrypt.hash(요청.body.password, 10);      
요청.body.password = hash;      
let db = (await connectDB).db('forum');      
await db.collection('user_cred').insertOne(요청.body);     
응답.status(200).json('성공'); } };
```



# 로그인을 위해 **Credentials provider 설정하기**

