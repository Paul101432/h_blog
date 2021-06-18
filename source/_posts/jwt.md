
---
title: jwt
tags: jwt
categories: web

--- 
```
token 是一串字符串，通常因为作为鉴权凭据，最常用的使用场景是 API 鉴权
结构为 Base64Url 编码的三部分(头部+内容+签名值)
```

### 一般来说 token 主要三种：
+ 自定义的 token：开发者根据业务逻辑自定义的 token
+ JWT：JSON Web Token，定义在 RFC 7519 中的一种 token 规范
+ Oauth2.0：定义在 RFC 6750 中的一种授权规范，但这其实并不是一种 token，只是其中也有用到 token


### 结构
+ header
```
{
  "alg": "HS256",
  "typ": "JWT"
}
```
+ Payload
    + 预定义（Registered）
        + iss (issuer)：签发人
        + sub (subject)：主题
        + aud (audience)：受众
        + exp (expiration time)：过期时间
        + nbf (Not Before)：生效时间，在此之前是无效的
        + iat (Issued At)：签发时间
        + jti (JWT ID)：编号 
    + 公有（public）
    + 私有（private） 
+ Signature
```
 HMACSHA256( //alg
     base64UrlEncode(header) + "." +base64UrlEncode(payload),
     secret // 这里应该是私钥
 )
```