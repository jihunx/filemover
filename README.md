# 시놀로지 파일 무버(Synology File Mover)
특정 이름이 포함된 파일을 원하는 디렉터리로 이동시키는 스크립트입니다.  
<br><br>
## 주요 기능 소개
1. 특정 키워드와 확장자의 파일을, 경로를 지정하여 원하는 폴더로 이동시킵니다.
2. 특정 키워드와 확장자의 파일을, 경로를 지정하지 않을 경우 기본 지정 폴더로 이동시킵니다.
3. 이동 대상 폴더에 동일한 파일 이름이 존재하는 경우 중복 폴더로 이동시킵니다.
4. 파일 리스트를 가나다순으로 자동 정렬할 수 있습니다. 
5. 시놀로지 스케줄러에 등록하여 주기적으로 실행시킬 수 있습니다.  
<br><br>
## 실행 방법
1. 시놀로지에 파이썬 설치
2. `제어판 > 작업 스케줄러`에 스케줄 등록
```
sh /volume1/homes/jihunx/filemover/start.sh
```
  * `사용자 정의 스크립트`에 위와 같이 등록
  * `/volome1/homes/jihunx/filemover/start.sh` 부분에는 `start.sh` 파일의 절대 경로를 입력합니다.  
<br><br>
## 환경 설정  
### 이동할 파일 키워드 설정
`filelist.txt` 파일에 키워드를 입력합니다(대소문자 상관 없음).
* 한줄씩 입력합니다.
* `키워드, 이동할폴더` 형태로 입력하며, 이동할 폴더는 절대 경로를 입력합니다.
* 키워드만 입력하면 기본 폴더로 이동합니다.  

### 확장자 및 폴더 설정
`filemover.py`에서 설정합니다.
* `file_ext`: 파일 확장자 설정
* `default_dir`: 이동할 폴더를 지정하지 않았을 때, 기본 대상 폴더
* `target_dir`: 대상 폴더 설정. 끝에 슬래시(/)를 붙이지 않습니다.
* `dup_dir`: 이동할 폴더에 동일한 파일 이름이 있을 때 이동할 폴더
* `file_list`: `filelist.txt` 파일의 절대 경로 입력
* `sort_boolean`: `filelist.txt` 리스트를 가나다순으로 정렬할지 선택합니다(기본값은 정렬하지 않음).

### 쉘 스크립트 설정
`start.sh`에 `filemover.py`의 절대 경로를 입력합니다.
<br><br>
## Appendix
이 프로그램은 https://blog.naver.com/binsoore/220936022468 를 기반으로 만들었습니다.  
원작자이신 **빈수레**님에게 감사드립니다.
