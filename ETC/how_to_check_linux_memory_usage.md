# 리눅스 서버 메모리 사용량 확인하는 방법
리눅스의 경우 사용되지 않은 메모리 일부를 cache와 buffer 영역에 할당한다. 그래서 여유 메모리를 계산할 때 buffer, cache 부분을 더해줘야 한다.
- buffer: 데이터를 처리할 때(e.g file I/O), 바로 처리하지 않고, 데이터를 buffer에 쌓아두었다가 buffer가 가득 차거나, cpu가 바쁘지 않을 때 이 데이터를 처리한다. 이때 사용되는 공간
- cache: 메모리에 적재되었던 데이터를 일시적을 보관하고 있는 공간. Disk I/O 의 빈도를 줄여준다.

## free
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:            61G         33G         21G         11M        6.4G         27G
Swap:            0B          0B          0B          0           0
```

전체 메모리 크기: 61g
사용 중인 메모리 크기: 33g
사용 가능한 메모리 크기: 21 + 6.4 = 27 (available)