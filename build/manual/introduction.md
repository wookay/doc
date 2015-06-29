소개 글
============

과학 분야 컴퓨팅은 고성능의 많은 수학적 계산 처리를 필요로 한다. 하지만 당사자인 전문 연구자들은 속도가 느리더라도 동적인 언어로서 그들의 업무를 처리한다. 동적인 언어를 즐겨쓰는 나름의 이유들로 보아, 이러한 추세는 쉽게 사그러들지 않아 보인다. 다행히 근래의 언어 디자인과 컴파일러 기법의 발달은 미뤄뒀던 성능 부분을 해결함으로서 프로토타이핑 작업시 개별 환경의 생산성을, 성능이 중요한 애플리케이션 구축시 그 효용성을 충분히 발휘한다. 줄리아 프로그래밍 언어는 다음과 같은 역할을 수행한다: 과학과 수학 분야의 컴퓨팅에 적합한 기존의 정적 타입 언어에 견줄만한 성능을 갖춘 유연한 동적 언어.

줄리아 컴파일러는 파이썬, R과 같은 언어와 다르다. 해서 줄리아의 성능을 처음 보면 아마 의아할 것이다. 막상 작성한 코드가 느리면 "성능 향상 팁"을 읽어보길 권한다. 줄리아가 어떤 식으로 작동하는지 이해를 하면, C로 짠거마냥 빠른 코드는 쉽게 작성할 수 있다.

줄리아는 타입 추론과 LLVM으로 구현한 적시 컴파일(JIT)을 사용해 선택적 타입, 멀티플 디스패치, 좋은 성능을 이뤄내고 있다. 그리고 명령형, 함수형, 객체 지향 프로그래밍의 특징을 포괄하는 다양한 패러다임을 추구한다. 줄리아는 고급 단계의 수치 계산에 있어 R, 매트랩, 파이썬처럼 간편하고 표현력이 우수하다. 뿐만 아니라 일반적인 형태의 프로그래밍 또한 가능하다. 이를 위해 줄리아는 수학 프로그래밍 언어를 근간으로 구축하였고 리스프, 펄, 파이썬, 루아, 루비와 같은 대중적인 동적 언어의 특징을 가져와 취합하고 있다.

기존에 있는 동적 언어와 비교해 줄리아만의 독특한 점은:

-   핵심 언어는 최소한으로 꾸린다; 정수를 다루는 프리미티브 연산자(+ - * 같은)를 비롯하여 기본 라이브러리는 줄리아 자체로 작성되었다.
-   객체를 구성하고 서술하는데 쓸 타입을 언어에서 풍부히 지원하며, 타입 선언을 할 때에도 선택적으로 사용할 수 있다.
-   인자 타입을 조합함으로서 함수의 작동 행위를 정의하는 "멀티플 디스패치"
-   인자 타입에 따라 효율적이고 특화된 코드를 자동으로 생성한다
-   C처럼 정적으로 컴파일되는 언어에 근접하는 훌륭한 성능

종종 동적 언어에 대해 "타입이 없다"는 식으로 말하는데 실은 그렇지 않다: 프리미티브(숫자와 같은 기본 타입의)이거나 별도 정의를 통틀어 모든 객체는 타입을 가진다. 그러나 대부분의 동적 언어는 타입 선언이 부족해 컴파일러가 해당 값의 타입을 인지하지 못한다거나 종종 타입에 대해 무엇인지 명시적으로 밝힐 수 없는 상태가 되곤 한다. 한편 정적 언어는 타입 정보를 - 보통 반드시 - 컴파일러용으로 달기에 타입은 오직 컴파일 시점에만 존재해 실행시에는 이를 다루거나 표현할 수가 없다. 줄리아에서 타입은 그 자체로 런타임 객체이며 컴파일러가 요하는 정보를 알려주는 데에도 쓰인다.

일상적인 프로그래머라면 개의치 않을 타입과 멀티플 디스패치는 줄리아의 핵심 개념이다: 함수들은 서로 다른 인자 타입들을 조합함으로서 정의되고 가장 그 정의와 맞물리는 타입을 찾아 디스패치하여 실행된다.  이 모델은 수학 프로그래밍과 잘 맞는데, 객체 지향에선 연산자가 첫번째 인자를 "갖는" 방식이기에 자연스럽지가 않다. 연산자는 단지 특별히 표기한 함수일 뿐이다 ``+`` 함수에 엮일 새로운 데이터 타입을 정의하려면 해당하는 메서드 정의만 추가하면 된다. 기존 코드는 새로운 데이터 타입과 더불어 원할하게 작동한다.

런타임 타입 추론(타입 지정을 점진적으로 늘려가며)을 이유로 또 이 프로젝트를 시작할 때 무엇보다 성능을 강조하였기에 줄리아의 계산 효율은 다른 동적 언어들에 비해 우월하며 심지어 정적으로 컴파일하는 경쟁 언어들마저 능가한다. 거대한 규모의 수치 해석 문제에 있어 속도는 매번 그리고 앞으로도, 아마 항상 결정적 요소일 것이다: 처리되는 데이터의 양이 지난 수십년간 무어의 법칙을 따르고 있으니 말이다.

사용하기 편하면서도 강력하고 효율적인 언어를 줄리아는 목표하고 있다. 다른 시스템과 견주어 줄리아를 씀으로 얻는 이득은 다음과 같다:

-   자유롭게 사용 가능하며 오픈 소스이다(MIT 라이센스)
-   사용자가 정의한 타입 또한 내장한 타입처럼 빠르고 간결하다
-   성능을 위해 코드를 벡터화할 필요가 없다; 벡터화하지 않은 코드도 빠르다
-   병렬과 분산 처리를 위해 고안되었다
-   가벼운 그린 쓰레딩(코루틴)
-   거슬리지 않는 강력한 타입 시스템
-   숫자와 다른 타입을 위한 우아하고 확장 가능한 컨버젼 및 프로모션(타입 변환)
-   UTF-8을 비롯, 효율적인 유니코드 지원
-   C 함수 직접 호출(별도의 래퍼나 특정한 API가 필요하지 않음)
-   다른 프로세스를 관리하는 쉘과 비슷한 강력한 기능
-   리스프와 비슷한 매크로, 메타프로그래밍을 위한 장치들

