# org.springframework.web.util.NestedServletException:Handler dispatch failed;nested exception is java.lang.Error:Probable fatal error:No fonts found

1. 엑셀 다운로드 기능에 문제 발생
다운로드 후 파일 열기 -> '파일 형식을 찾을 수 없습니다.' 에러 발생
-> 로그 확인 'org.spring ... :No fonts found'

2. 운영서버와 백업서버에서 폰트 목록을 비교
```sh
yum list installed | grep font
```
-> 운영서버에는 폰트가 있으나 백업서버에는 폰트가 없었음

3. 백업서버에 폰트 설치
```sh
sudo yum install fontconfig
sudo yuum stix-fonts // 운영서버와 동일한 폰트 설치
```

4. 서버 재기동

참고
https://catamaranframework.wordpress.com/2012/12/21/solved-java-lang-error-probable-fatal-errorno-fonts-found/
