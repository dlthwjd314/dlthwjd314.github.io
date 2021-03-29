---
layout: post
title:  "JDK 8 환경변수 설정 / 명령 프롬프트(cmd)에서 java 컴파일"
---



[ JDK 8 환경변수 설정 / 명령 프롬프트(cmd)에서 java 컴파일 ]





##### < JDK 환경변수 설정하기 >





1. ' 내 PC ' 의 빈 곳을 우클릭 하여 속성에 들어갑니다.  

<img src = "https://user-images.githubusercontent.com/78267103/112850267-d119bc00-90e4-11eb-900d-b1eabe0334b1.jpg" width="300" height="300">









2. 좌측의 '고급 시스템 설정'에 들어갑니다.

![image-20210329212913104](https://user-images.githubusercontent.com/78267103/112850272-d2e37f80-90e4-11eb-9dfe-68e2db1ad848.jpg)











3. 시스템 속성창이 뜨면 하단의 '환경 변수' 에 들어갑니다.

![image-20210329213300567](https://user-images.githubusercontent.com/78267103/112850274-d2e37f80-90e4-11eb-824c-db28d1ab748e.jpg)











4. 환경변수 창에서  시스템 변수 아래의 '새로 만들기'를  클릭하여 변수를 설정합니다.
![image-20210329213503871](https://user-images.githubusercontent.com/78267103/112850276-d37c1600-90e4-11eb-91c7-11bbff87d5ec.jpg)











5. 아래와 같이 변수 이름을 'JAVA_HOME'과 같이 설정하고 'jdk1.8.0_281' 폴더가 존재하는 경로를 변수 값으로 지정해 줍니다. (일반적으로 아래와 같은 경로에 해당 폴더가 존재합니다.)

![image-20210329213626737](https://user-images.githubusercontent.com/78267103/112850278-d37c1600-90e4-11eb-92c5-9c4e66d9aa0b.jpg)











6. 그리고 변수이름을 'CLASSPATH'로 설정하고 변수 값을 '.;' ('.'은 현재경로를 의미)와 같이 지정해줍니다.

![image-20210329214119449](https://user-images.githubusercontent.com/78267103/112850280-d414ac80-90e4-11eb-856b-34adb30fc45f.jpg)











7. 새 시스템 변수 설정 확인 후 시스템 변수에서 'Path'변수를 편집하여 JDK 의 경로를 지정해 주도록 합니다.

![image-20210329214309141](https://user-images.githubusercontent.com/78267103/112850286-d414ac80-90e4-11eb-9418-2531f81f5e0c.jpg)











8.  환경 변수 편집 창에서 새로 만들기를 통해 ' %JAVA_HOME%\bin ' 이라는 경로를 만들어 줍니다.

   (경로지정 시 ' %시스템 변수 이름%\나머지 경로 ' 의 형식으로 생성합니다.)

![image-20210329214516105](https://user-images.githubusercontent.com/78267103/112850289-d4ad4300-90e4-11eb-882c-cfe3733dd9d3.jpg)













##### < 명령 프롬프트(cmd)에서 java 컴파일 하기>





1. 작업하고자 하는 폴더에서 자바확장자(.java)로 파일을 하나 만들어 줍니다. 

![image-20210329215113195](https://user-images.githubusercontent.com/78267103/112850293-d545d980-90e4-11eb-8727-48c4ee266069.jpg)















2. 아래와 같이 실행하고자 하는 자바 클래스를 생성합니다. 

   (자바 클래스명과 클래스를 담은 파일명은 같아야 합니다.)

![image-20210329215241860](https://user-images.githubusercontent.com/78267103/112850296-d545d980-90e4-11eb-94ad-089006989ccc.jpg)














3. 명령 프롬프트창(cmd)에서 해당 자바파일이 존재하는 위치로 이동하고, 해당 위치에서 생성한 자바 파일을 컴파일 해줍니다.

```java
C:\Users\SOJEONG>cd..    
C:\Users>cd..
C:\>cd C:\douzone\workspace     --> 해당 파일이 존재하는 위치로 이동
C:\douzone\workspace>javac HelloJava.java  --> 자바 파일 컴파일
```









4. 하지만, utf-8 인코딩이 제대로 되지않아 한글이 깨져서 나오게 됩니다.

   ```java
   HelloJava.java:7: error: unmappable character for encoding MS949  
                   System.out.print("?뻾蹂듯븯?꽭?슂>_<");  
   HelloJava.java:7: error: unmappable character for encoding MS949
                   System.out.print("?뻾蹂듯븯?꽭?슂>_<");     
   HelloJava.java:7: error: unmappable character for encoding MS949
                   System.out.print("?뻾蹂듯븯?꽭?슂>_<");       
   3 errors    
    
    --> utf-8 인코딩이 되지 않아서 나타나는 오류    
   ```









5. < -encoding utf-8 > 옵션을 이용하여 자바 파일이 제대로 컴파일 되도록 합니다.

```java
C:\douzone\workspace>javac -encoding utf-8 HelloJava.java 

--> 인코딩 후 정상적으로 컴파일  
```









6. 다음과 같이 클래스가 정상적으로 실행되는 것을 볼 수 있습니다.

```java
C:\douzone\workspace>java HelloJava
Hello Java!!
2021
행복하세요>_<       
```
