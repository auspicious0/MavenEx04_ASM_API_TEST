# MavenEx04_ASM_API_TEST

## 0.	목표
maven을 통해 jar 파일을 생성하여 암호화를 수행해 보고자 한다. 

## 1.	코드

```java 
package org.al.test;

import *;

public class App {
  public static void main(String[] paramArrayOfString) {
    try {
      String str1 = *.encrypt("", "123123123");
      System.out.println(str1);
      String str2 = *.decrypt("", str1);
      System.out.println(str2);
    } catch (Exception exception) {
      exception.printStackTrace();
    }
  }
}
```
```pom.xml 추가 코드
<build>
	    <plugins>
	        <plugin>
	            <groupId>org.apache.maven.plugins</groupId>
	            <artifactId>maven-jar-plugin</artifactId>
	            <version>3.3.0</version>
	            <configuration>
	                <archive>
                    <manifest>
                        <mainClass>org.al.test.App</mainClass>
                    </manifest>
	                </archive>
	            </configuration>
	        </plugin>
	    </plugins>
	</build>
```

```shell
            echo "Shell script created successfully."
            echo "Creating shell script..."
            #!/bin/bash

            # Get current directory of the script
            DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" &> /dev/null && pwd )"

            MY_HOME=$DIR
            MY_LIB_PATH=$MY_HOME/lib
            MY_CLASSPATH=""

            export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$MY_LIB_PATH
            for LIB_NAME in `ls $MY_LIB_PATH | grep jar`; do
                MY_CLASSPATH=$MY_CLASSPATH$MY_LIB_PATH"/"$LIB_NAME
            done


            java -cp "$MY_CLASSPATH:$MY_HOME/test-0.0.1-SNAPSHOT.jar" org.al.test.App

            echo "MY_HOME :: "$MY_HOME
            echo "MY_CLASSPATH :: "$MY_CLASSPATH
            echo "MY_LIB_PATH :: "$MY_LIB_PATH
            # SQL queries

            # Changing permission
            chmod 755 example_script.sh

            echo "Shell script created successfully."
```


## 2.	코드에 관한 설명
- java code는 java_asm_api로 local에 있는 asm server에 접근하여 암복호화를 수행하는 알고리즘이다. 
- pom.xml code는 위의 java 클래스를 jar파일로 maven build (package)를 수행한다.
- shell 파일은 우선 자신의 위치를 dir에 저장한 후 해당 위치의 lib 를 시스템 환경 변수로 등록한다. 또한 암복호화를 위한 jar 파일과 우리가 위 java 코드를 함축하고 있는 jar파일을 classpath로 설정한 후 해당 jar 파일안에 App 클래스를 실행하여 암호화를 수행한다.

## 3.	실행결과
 
![image](https://github.com/auspicious0/MavenEx04_ASM_API_TEST/assets/108572025/9c9cd5fb-412e-4f7c-8543-af195dc5a71f)
암호화가 수행된 것을 확인할 수 있다.


