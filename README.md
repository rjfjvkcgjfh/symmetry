# Local Symmetry Detection for Crystals and symmetry Molecules

이 리포지토리는 분자 및 결정 구조의 국소 대칭(점군)을 계산하는 Python 모듈들을 제공합니다. 여러 기하학적 대칭 요소(회전축, 반사면, 역 중심, 반회전축 등)를 분석하여 대상 구조의 대칭성을 분류합니다.

## 기능

- **Primary Moment 계산:**  
  주 관성 모멘트를 계산하여 구조의 기본 대칭성을 분석합니다.

- **Proper/Improper 축 검출:**  
  회전축과 반회전축을 판별하여 구조의 올바른 대칭 요소를 확인합니다.

- **반사면 및 역 중심 검사:**  
  수평/수직 반사면과 역 중심의 존재 여부를 확인합니다.

- **Molecular & Crystal Symmetry:**  
  분자 및 결정 구조 모두에 대해 국소 대칭성을 평가합니다.

- **ASE 통합:**  
  [ASE (Atomic Simulation Environment)](https://wiki.fysik.dtu.dk/ase/)의 primitive_neighbor_list를 활용하여 이웃 원자 정보를 구축합니다.

- **SQLite 데이터베이스 연동:**  
  data_new.py 모듈을 이용해 SQLite 데이터베이스로부터 결정 구조 데이터를 읽어옵니다.

## 요구 사항

- Python 3.x
- [NumPy](https://numpy.org/)
- [ASE (Atomic Simulation Environment)](https://wiki.fysik.dtu.dk/ase/)

필요한 패키지는 아래 명령어로 설치할 수 있습니다:

bash
pip install numpy ase

------

# 리포지터리 구조


├── README.md
├── main.py                   # 국소 대칭 계산 메인 스크립트
├── element_mass.py               # 원소 질량 정보 제공 모듈
├── calculate_primary_moments.py  # 주 모멘트 계산 모듈
├── check_proper_axes.py          # 올바른 회전축 판별 모듈
├── check_inversion_center.py     # 역 중심 검사 모듈
├── check_reflection_plane.py     # 반사면 검사 모듈
├── check_improper_axis.py        # 반회전축 검사 모듈
├── data.sqlite                   #SQLite 데이터베이스스 
└── data_new.py                   # SQLite 데이터베이스 연동모듈

# 사용법

1. 분자대칭성 확인

main.py 파일 내에 주석 처리된 분자 대칭성 검사 코드를 참고하여, 직접 원자 리스트(local_atoms)를 정의한 후 실행하면 해당 분자의 대칭성을 계산할 수 있습니다.

2. 결정내 local symmetry 확인
SQLite 데이터베이스(data.sqlite)에 저장된 결정 데이터를 대상으로 국소 대칭성을 계산할 수 있습니다. data_new.py 모듈을 이용하여 데이터베이스 연결 및 결정 정보를 읽어오며, main.py 내 build_structure와 find_crystal_local_symmetry 함수를 사용합니다.

실행 시, 지정된 결정 ID 범위에 대해 local symmetry가 출력됩니다.

# 예제
main.py의 __main__ 블록에서는 두 가지 예제가 포함되어 있습니다:

분자 대칭성 검사 예제:
분자 데이터를 입력하여 대칭성을 계산하는 코드(주석 처리되어 있음).

결정 대칭성 검사 예제:
데이터베이스로부터 결정 데이터를 불러와 각 원자 및 이웃 원자 간의 국소 대칭성을 계산하는 코드.

필요에 따라 예제 코드를 활성화하여 사용하시기 바랍니다.


# 기여 방법
버그 리포트, 기능 제안, 풀 리퀘스트 등 모든 기여를 환영합니다.
이슈 페이지에서 아이디어 및 문제점을 공유해주세요.
# 라이선스
이 프로젝트는 MIT 라이선스 하에 배포됩니다.
