# 법정동 코드와 관련된 클래스

## 1. 클래스 생성
  * 생성 파라메터는 시도코드이며, 기본값은 '41'(경기도)
>```python
>code_db = DistrictCode('41')
>```

## 2. DB 경로 지정
  * 최초 DB가 없는 경우 행정표준코드관리시스템(code.go.kr)에서 법정동코드 전체자료 다운로드
  * 빠른 접근을 위해 클래스 생성시 만들어진 데이터프레임을 피클(pickle) 형태로 백업
  * 따라서, 이를 저장할 경로를 지정해 주어야 함
>```python
>code_db.set_path('./DB')
>```


## 3. 법정동코드 검색
  * 모든 빈칸을 삭제 후 해당 단어를 포함하는 최초 검색결과 반환
  * 정확한 결과를 위해 상세한 주소 입력(빈칸은 무시됨)
>```python
>cd = code_db.search('팔달구 인계동')  # 411151410
>cd = code_db.search('팔달구인 계동')  # 411151410
>```

## 4. PNU 생성
  * 행정구역명, 지번(지목은 무시됨)으로 PNU 생성
  * 정확한 결과를 위해 상세한 주소 입력(빈칸은 무시됨)
>```python
>pnu = code_db.make_pnu('팔달구 인계동', '산123-4')  # 411151410201230004
>pnu = code_db.make_pnu('팔달구인 계동', '543-1대')  # 411151410105430001
>```

## 5. 법정동코드/PNU 에서 행정구역명 생성
>```python
>nm = code_db.emd('411151410')           # 경기도 수원시 팔달구 인계동
>nm = code_db.emd('411151410105430001')  # 경기도 수원시 팔달구 인계동
>```

