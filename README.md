
`원래 키 올리면 안되지만, 그냥 테스트용이라서 올림`

# 테스트용 인증 기관

## Certicicate authorith (CA)
 - 디지털 인증서를 발급하는 단위
 - `openssl genrsa -out CA.key 2048`

## Certificate Signing Request (CSR)
 - CA 에 인증서 발급 요청을 하는 파일
 - 공개키와 알고리즘 정보 등을 포함한다.
 - `openssl req -new -key CA.key -out CA.pem`

## crt (CERT 의 약자)
 - 인증서로 보통 .crt 확장자로 사용
 - `openssl x509 -req -in CA.pem -signkey CA.key -out CA.crt`

# 서버 키

## Certicicate authorith (CA)
 - `openssl genrsa -out server.key 2048`

## Certificate Signing Request (CSR)
 - `openssl req -new -key server.key -out server.pem`

## crt (CERT 의 약자)
 - 위 테스트 인증 기관에서 인증 받는 인증서를 생성
 - `openssl x509 -req -sha256 -in server.pem -CA CA.crt -CAkey CA.key -out server.crt`

# 서버 실행

```bash
python server.py
```
