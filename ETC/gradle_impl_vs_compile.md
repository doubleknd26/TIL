# Gradle Implementation VS Compile

compile
- compile은 api 또는 implementation으로 대체되었다.

implementation
- Gradle이 컴파일 클래스 경로에 종속 항목을 추가하고 빌드 출력에 종속 항목을 패키징합니다. 그러나 모듈에서 implementation 종속 항목을 구성하면 모듈이 컴파일 시간에 종속 항목을 다른 모듈에 누출하기를 바라지 않는다는 것을 Gradle에 알려주는 것입니다. 즉 종속 항목은 런타임에만 다른 모듈에서 이용할 수 있습니다.
- api 또는 compile(지원 중단됨) 대신 이 종속 항목 구성을 사용하면 빌드 시스템에서 다시 컴파일해야 하는 모듈 수가 줄어들기 때문에 빌드 시간이 크게 개선될 수 있습니다. 예를 들어 implementation 종속 항목이 API를 변경하면 Gradle은 이 종속 항목과 이에 직접적으로 종속된 모듈만 다시 컴파일합니다. 대부분의 앱과 테스트 모듈은 이 구성을 사용해야 합니다.

api
- Gradle은 컴파일 클래스 경로와 빌드 출력에 종속 항목을 추가합니다. 모듈에 api 종속 항목이 포함되면 모듈이 다른 모듈로 종속 항목을 이전하여 다른 모듈에서 런타임과 컴파일 시간에 사용할 수 있도록 한다는 것을 Gradle에 알려주는 것입니다.
- 이 구성은 compile(현재는 지원 중단됨)처럼 작동하지만 주의해서 다른 업스트림 소비자에게 이전해야 하는 종속 항목과만 사용해야 합니다. 그 이유는 api 종속 항목이 외부 API를 변경하면 Gradle이 컴파일 시 종속 항목에 액세스 권한이 있는 모든 모듈을 다시 컴파일하기 때문입니다. 따라서 api 종속 항목 수가 많으면 빌드 시간이 크게 증가할 수 있습니다. 종속 항목의 API를 별도의 모듈에 노출하지 않으려면 라이브러리 모듈에서 implementation 종속 항목을 대신 사용해야 합니다.

---

api: 의존 라이브러리 수정시 해당 모듈을 의존하고 있는 모듈들 또한 재빌드  
e.g) A api B -> C
- A 에서 C 접근 가능
- C 수정하면 A, B 모두 재빌드

implementaion: 의존 라이브러리가 수정되면, 직접적으로 의존하고 있는 모듈까지만 재빌드  
e.g) A imp B -> C
- A 에서 C 접근 불가능
- C 수정하면 B 까지만 재빌드


reference)
- https://developer.android.com/studio/build/dependencies#dependency_configurations
