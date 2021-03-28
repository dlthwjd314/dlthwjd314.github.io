#### [파일 및 디렉토리 생성 복사 이동 삭제 실습]



pwd -- 현재 위치 확인
/root/

##### 1. /etc/sysconfig 복사해서 /root/filetest/ 넣으세요.

```bash
[root@localhost ~]# mkdir /root/filetest/
[root@localhost ~]# cp -r /etc/sysconfig /root/filetest/
[root@localhost ~]# ls /root/filetest/
sysconfig
```

< -r > : 디렉토리 복사 할 때 붙는 옵션.

*디렉토리의 경우 사전에 존재해야만 복사 할 수 있다. (파일의 경우에는 사전에 존재하지 않아도 새로 만들면서 복사 가능.)



##### 2.  /root/filetest/sysconfig/network-scripts/를 이동시켜 /root/filetest1/에 넣으세요.

```bash
[root@localhost ~]# mkdir /root/filetest1
[root@localhost ~]# mv /root/filetest/sysconfig/network-scripts /root/filetest1
[root@localhost ~]# ls /root/filetest1
network-scripts
[root@localhost ~]# ls /root/filetest/sysconfig/network-scripts
ls: cannot access /root/filetest/sysconfig/network-scripts: No such file or directory
```

##### 

##### 3. / root/filetest1/network-scripts 디렉토리에 파일 이름이 testfile을 만드시오.

```bash
[root@localhost ~]# touch /root/filetest1/network-scripts/testfile
[root@localhost ~]# ls /root/filetest1/network-scripts/testfile
/root/filetest1/network-scripts/testfile
```



##### 4. /root/filetest1/network-scripts/testfile 을 복사해서 /root/testfile1을 만드시오

```bash
[root@localhost ~]# cp /root/filetest1/network-scripts/testfile /root/testfile1
[root@localhost ~]# ls /root/testfile1
/root/testfile1
```

*1. 번 에서 디렉토리를 복사 할 때와 달리, 파일은 새롭게 생성하면서 내용 복사를 할 수 있다.



##### 5. /root/testfile1 파일을 /tmp/testfile로 이름을 바꾸시오.

```bash
[root@localhost ~]# mv /root/testfile1 /tmp/testfile
[root@localhost ~]# ls /tmp/testfile
/tmp/testfile 
[root@localhost ~]#  ls /root/testfile1
ls: cannot access /root/testfile1: No such file or directory 
```

-- 파일 이름이  바뀌면서 원본이 삭제 되었음을 알 수 있다.



##### 6. /root/b/bb/bbb/bbbb를 명령어 한줄로 만드시오

```bash
[root@localhost ~]# mkdir /root/b/bb/bbb/bbbb
mkdir: cannot create directory ‘/root/b/bb/bbb/bbbb’: No such file or directory
[root@localhost ~]# mkdir -p  /root/b/bb/bbb/bbbb
[root@localhost ~]# ls -R /root/b
/root/b:
bb

/root/b/bb:
bbb

/root/b/bb/bbb:
bbbb

/root/b/bb/bbb/bbbb:
```

-- 상위 디렉토리가 존재 하지 않으면 하위 디렉토리를 생성할 수 없다.

하지만, < -p > 옵션을 이용하면 한 번에 상위에서 하위 디렉토리까지 생성이 가능하다.



##### 7. /root/filetest/ 의 시간 정보를 현재 시각으로 바꾸시오.

```bash
[root@localhost ~]# ls -la /root/
total 44
drwxr-xr-x.  3 root root   37 Mar 28 21:51 filetest
```

-- /root/filetest 의 시간 정보를 조회한 경우 위와 같았다. 

(< -l > :  자세하게 보고 싶을 때, < -a > : 숨김파일 까지 보고 싶을 때. )

```bash
[root@localhost ~]# touch /root/filetest
[root@localhost ~]# ls -la /root/
total 44
drwxr-xr-x.  3 root root   37 Mar 28 22:43 filetest
```

-- /root/filetest 를 한번 더 생성하면 overwritting 되어 생성시각으로 정보가 바뀐 것을 알 수 있다.

##### 8. rmdir 명령어로 /root/b/디렉토리를 삭제하시오.

```bash
[root@localhost ~]# rmdir -p /root/b/bb/bbb/bbbb
rmdir: failed to remove directory ‘/root’: Device or resource busy
[root@localhost ~]# ls -R /root/b
ls: cannot access /root/b: No such file or directory
```

-- resource가 바쁘다며 디렉토리를 삭제할 수 없다고 나온다. 

하지만, 상위-하위 디렉토리를 한 번에 만들었을 때와 같이 < -p > 옵션을 이용하면, 하위 부터 ''파일이 들어있지 않은'' 상위 디렉토리까지 순차적으로 한 번에 디렉토리 삭제가 가능하다. 

