#### next-auth 라이브러리를 사용하면 기본적으로 모든방식이
JWT이다

하지만 session 방식으로도 가능

#### DB Adapter 기능을 켜놓으면

1. 첫 로그인시 자동으로 유저를 회원가입 시켜서 DB에 유저 회원정보를 보관해줍니다. 

2. 로그인시 자동으로 유저가 언제 로그인했는지 세션정보를 DB에 보관해줍니다.

3. 서버에서 지금 로그인된 유저정보가 필요하면 JWT가 아니라 DB에 있던 세션정보를 조회해서 가져옵니다. 

1. 로그아웃시 유저 세션정보는 DB에서 삭제됩니다.

그래서 가입된 유저정보를 DB에 저장하는게 필요하거나

유저 로그인상태를 엄격하게 관리하고 싶으면 DB adapter 기능을 사용해봅시다.


# 순서

#### **MongoDB adapter 설정하기**

npm install @next-auth/mongodb-adapter

``` javascript

([...nextauth].js 파일) 

import { connectDB } from "@/util/database"; 
import { MongoDBAdapter } from "@next-auth/mongodb-adapter";
import NextAuth from "next-auth"; 
import GithubProvider from "next-auth/providers/github"; 

export const authOptions = { 

providers: [
GithubProvider({ 
clientId: 'Github에서발급받은ID',
clientSecret: 'Github에서발급받은Secret', }), ],
				
secret : '어쩌구' 

adapter : MongoDBAdapter(connectDB), //추가함 }; export default NextAuth(authOptions);

export default NextAuth(authOptions)
```

로그인해보면 저번 시간과 다르게 MongoDB에 3개의 컬렉션이 생성됩니다. 

**sessions**에는 현재 로그인된 유저 정보가 들어있습니다. 로그인 유효기간도 적혀있음 

**users**는 유저들 보관하는 곳입니다. 유저끼리 구분은 이메일로 합니다. 

**accounts**는 유저계정 보관하는 곳입니다. 

하나의 유저는 여러개의 계정을 가지고 있을 수 있기 때문에 여러 계정마다 이메일이 중복될 수도 있습니다.


**Q. users vs accounts 차이가 뭐임?** 

어떤 1명의 유저가 내 사이트에 Github으로도 가입하고 Google로도 가입을 해버린 경우를 가정해봅시다.

근데 이 사람의 

Github 계정은 test@naver.com

Google 계정도 test@naver.com 으로 되어있는 겁니다.



# **회원기능이 들어간 게시판**

- 글삭제를 할꺼면 요청한사람이 글쓴사람과 일치하는지 검사
- 즉 , 글 발행할때, 글쓴이의 이메일도 같이 저장을하자 (서버에서)
- 대신 이메일도 같이보내라가아니라, getServerSession()을 사용해서
- 현재 로그인된 유저정보를 보고 서버에서 처리

``` javascript
let session = await getServerSession(요청, 응답, authOptions)
```

