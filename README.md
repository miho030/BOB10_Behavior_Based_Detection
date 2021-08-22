## BEHAVIOR_BASED_DETECTION

### Injector
- 특정 프로세서에 dll을 Injection, Ejection 시켜주는 도구

```
Injection.exe -i <process 명> <dll 명>
```

### detector
- Hooking 한 API를 사용시 발생하는 debug log를 받아서, 특정 프로세스가 시나리오를 만족하는지 비교하여, 악성 키로거라고 판단되면 알림을 통해 차단 여부를 사용자에게 알려주는 프로그램

### globalhook
- global hooking을 수행하는 dll
- CreateProcessA,� CreateProcessW를 후킹하여, 자식 프로세스에 globalhook.dll 와 myhook.dll 이 자동으로 Injection을 시켜주도록 한다.

### myhook
- 행위기반 탐지에 필요한 API를 후킹하는 dll

### Implementation of Scenario Algorithm
- 악성코드 시나리오를 생성할 때 사용

## Requirements
- Windows7 32bit
- Visual studio 2019

## 사용법
- Clone from Github
```
git clone https://github.com/NPclown/BOB10_Behavior_Based_Detection.git
cd BOB10_Behavior_Based_Detection
cd src

Build.sln 실행
```

- Build 수행
```
x86으로 빌드를 수행
```

- dll 파일 이동
```
BOB10_Behavior_Based_Detection\Build\Debugx86
BOB10_Behavior_Based_Detection\Build\Releasex86 

하위에 생성되는 globalhook.dll 과 myhook.dll을 C:\Windows\System32 로 이동
```

- Detector 실행

- Injector 실행
```
# 인젝션을 수행할 때
Injector.exe -i explorer.exe globalhook.dll

# 이젝션을 수행할 때
Injector.exe -e explorer.exe globalhook.dll
```



