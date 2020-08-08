# jenkins pipeline background process

- 현상
jar파일을 실행하는 스크립트를
1. jenkins deploy job에서 execute할 경우 -> job이 끝나고 background process가 죽음
2. terminal에서 직접 실행 -> 정상 작동

- 원인
jenkins job 종료 후에 해당 사용자로 실행된 child process를 모두 kill하는 이슈

- 해결
스크립트 실행 시 JENKINS_NODE_COOKIE=dontKillMe 또는 BUILD_ID=dontkillMe 옵션 추가

- 참고
https://medium.com/@jjeaby/jenkins-pipeline-background-process-82af369e0e2d   
https://blog.jiniworld.me/25   
(사내 질문게시판에서 얻은 답변입니다.)
