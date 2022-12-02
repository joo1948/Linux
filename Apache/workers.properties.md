# workers.properties
  ## 위치
   > ~ /apache/conf <br>
    연결하고자 하는 톰캣에 대한 정의 및 설정
  ## ex
  ``` shell
    worker.list=worker1
    worker.worker1.port=8009
    worker.worker1.host=localhost
    worker.worker1.type=ajp13
  ```
