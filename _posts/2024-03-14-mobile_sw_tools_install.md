---
title: 모바일 SW(Tizen APP) 개발을 위한 Tool 설치
date: 2024-03-14 00:10:00 +0900
categories: [Dev, Mobile SW]
tags: [Tizen]
---

**기본 환경**

- x64
- Windows11
<br/><br/>

---
## **Tool 설치**

### **1. Microsoft Visual Studio Community 2019**

> **버전: Microsoft Visual Studio Community 2019 버전 16.11.34**
{: .prompt-warning }

- **다운로드 링크:** [https://learn.microsoft.com/ko-kr/visualstudio/releases/2019/release-notes](https://learn.microsoft.com/ko-kr/visualstudio/releases/2019/release-notes)
    - 설치 과정에서 밑의 3개 선택 후 설치 (대략 10~15G 필요)
        - .NET 데스크톱 개발
        - C++를 사용한 데스크톱 개발
        - .NET cross-platform development (out of suppot)
- **호환: Visual Studio** 16.11.XX 버전은 **.NET SDK** 5.0.4XX 버전과 호환
    

    ![VS 설치 확인 이미지](/assets/img/post_img/2024-03-14-1.png){: .light .w-75 .shadow .rounded-10 w='1212' h='668' }

    <br/><br/>
    

### **2. .NET SDK**

> **버전: .NET SDK 5.0.408**
{: .prompt-warning }

- **다운로드 링크**: [https://dotnet.microsoft.com/en-us/download/dotnet/5.0](https://dotnet.microsoft.com/en-us/download/dotnet/5.0)
    - 위의 다운로드 페이지에서 SDK 5.0.408 > Windows > **x64** 다운로드
    
    ![NET SDK 설치 확인 이미지](/assets/img/post_img/2024-03-14-2.png){: .light .w-75 .shadow .rounded-10 w='1212' h='668' }
    <br/><br/>


### **3. JAVA SDK**

> **버전: JAVA SDK 1.8.0.201**
{: .prompt-warning }

- **다운로드 링크**: [https://www.oracle.com/java/technologies/downloads/archive/](https://www.oracle.com/java/technologies/downloads/archive/)
    - 위의 다운로드 페이지에서 Java SE 8 (8u202 and earlier) > Java SE Development Kit 8u201 > **jdk-8u201-windows-x64.exe** 다운로드
    - 다운 받는 대상 폴더 위치 및 폴더 이름 확인 필요
        
        EX) C:\Program Files\Java\jdk1.8.0_201\
        
- **변수 설정**
    
    고급 시스템 설정 > 환경 변수 > 시스템 변수 
    
    - **JAVA_HOME :** C:\Program Files\Java\jdk1.8.0_201
    - **PATH :** %JAVA_HOME%\bin
    - **CLASSPATH :** .;
- **(추가: 변수 설정)** 원래 사용하던 버전이 있어서 해당 버전을 우선 참조하도록 추가 설정했습니다.

    | 시스템 변수 명 | 기존 값 | 변경 값 |
    | :------------ | :----- | :------ | 
    | JAVA_HOME     | C:\Program Files\Java\jdk-11.0.17 | C:\Program Files\Java\jdk1.8.0_201 |
    | PATH          | %JAVA_HOME%\bin | %JAVA_HOME%\bin |
    | CLASSPATH | %JAVA_HOME%\lib |  .;  |

    - **`PATH` 순서 관련**:
    참조하는 java.exe가 여러 개 있어서, 해당 버전을 우선하도록 해당 환경 변수 순서를 밑의 환경 변수 2개 보다 위로 올립니다.
        -  C:\Program Files (x86)\CommonFiles\Oracle\Java\javapath
        -  C:\Program Files\Common Files\Oracle\Java\javapath



![JAVA 버전 확인.png](/assets/img/post_img/2024-03-14-3.png){: .light .w-75 .shadow .rounded-10 w='1212' h='668' }
<br/><br/>


### **4. Tizen Tool for VS**

- **다운로드**:  Visual Studio > 확장 > 확장 관리 선택
    - 밑의 2개 다운로드 (다운로드 클릭 후 VS를 모두 닫아야 다운로드 시작)
        - Visual Studio Tools for Tizen
        - Samsung TV .NET App Templates
<br/><br/>


### **5. Tizen SDK**

- **다운로드**: Visual Studio > 도구 > Tizen > Tizen Package Manager 선택
    - SDK 설치할 폴더 먼저 생성 필요
    EX) C:\Users\HanYeJi\Documents\TizenSDK
- **실행**: Visual Studio > 도구 > Tizen > Tizen Package Manager 선택
    - 밑의 3개 install
        
        Main SDK: 
        
        - Tizen SDK Tools
        - 8.0 Tizen
        
        Extension SDK:
        
        - Extras
<br/><br/>

---
## **Emulator 생성 및 실행**

- **Emulator Manager 실행** : Visual Studio > 도구 > Tizen > Tizen Emulator Manager 선택
- **생성:**
    1. Device: `HD1080 Tizen`, Name: `T-8.0-x86_64`인 애뮬레이터 선택 후 Create 클릭 
    2. Platform: `tizen-8.0-x86_64(basic)` 선택
    3. Template: `HD1080 Tizen` 선택
    4. Properties: 
        - General: VM Name 설정
            - 예시 이름: t-0313-1
                
                타이젠(t) / 날짜(0313) / 번호(1)
                
        - HW Support:  `GPU OFF` 설정
- **Emulator 실행**: 생성한 애뮬레이터 선택 후 Launch 클릭
<br/><br/>

---
## **Visual Studio 빌드 및 실행**

- **프로젝트 위치:** C:\Users\HanYeJi\source\repos\TizenXamlApp7-class
    - Mainpage.xml (초반에는 이 파일을 주로 작업)
- **빌드:** 빌드 > 솔루션 다시 빌드 클릭
    - 프로젝트 2개이므로 성공 2가 출력 되어야 합니다.
- **실행:** 위에서 생성한 애뮬레이터 이름이 띄워져야 합니다.
<br/><br/>

---
## **전체 실행 화면**

![연결 확인 화면.png](/assets/img/post_img/2024-03-14-4.png){: .light .w-75 .shadow .rounded-10 w='1212' h='668' }

- 애뮬레이터 옆의 바에 있는 각 버튼 기능
    - (맨 위의 버튼 2개는 작동하지 않음)
    - 돌아가기 (절전 모드 되었을 때 누름)
    - 전원 끄기
    - 볼륨 업
    - 볼륨 다운
    - 화면 회전
    - 콘솔 열기
    - 도구 막대
    - 화면 캡쳐
<br/><br/>

---
**문제 해결 방법**
> 여러 문제가 발생할 때, 가장 먼저 시도할 간단한 해결 방안: 따로 생성한 애뮬레이터 삭제 후 다시 생성
{: .prompt-tip }

- **문제 상황 1**: CMD 창에 밑의 명령어 입력 >

    ```powershell
    sc query intelhaxm
    ```

    이때 running이 아닌 다른 출력 메시지(EX. stopping)가 나오는 상황

- **해결 방안 1**:
    1. intel haxm 파일 설치 (설치용 zip파일 안의 실행 파일 사용하여 설치)
    2. Hyper-V 기능 끄기 
        - CMD 창에 입력 >
            
            ```powershell
            bcdedit /set hypervisorlaunchtype off 
            ```
            
        - 입력 후 재부팅
<br/><br/>

---
**진행 중인 이슈**

- 전원 버튼을 눌러도 안 꺼집니다. 창 끄기로 강제 종료 해야 꺼지는 상황입니다.