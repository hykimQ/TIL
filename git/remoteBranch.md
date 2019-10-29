# remote branch 가져오기

Git을 사용하다보면 원격 저장소에 있는 branch를 로컬 저장소로 가져와야하는 경우가 있다. 협업하고 있는 다른 팀원의 branch를 가져와서 작업을 해야하는 경우 혹은 혼자서 2대의 PC를 사용하고 작업파일을 Git으로 관리하는데 branch를 따서 작업하는 경우 등이 여기에 해당한다. 저장소를 그대로 clone을 하던지, pull을 하면 원격 저장소의 branch도 같이 받아질 것이라 생각했지만 그렇지 않았다. \$ git checkout -t [원격 저장소의 branch 이름] 명령을 이용하면 원격 저장소의 branch를 가져오는 것과 동일한 기능을 한다.

> https://cjh5414.github.io/get-git-remote-branch/
