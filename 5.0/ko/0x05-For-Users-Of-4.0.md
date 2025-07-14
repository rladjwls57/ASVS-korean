# v4.x 대비 변경 사항

## 소개

표준 v4.x에 익숙한 사용자는 v5.0에 도입된 주요 변경 사항을 검토하면 도움이 된다. 여기에는 내용, 범위 및 기본 철학의 변화를 포함한다.

버전 4.0.3의 286개 요구사항 중 변경되지 않은 것은 11개에 불과하며, 15개는 의미를 변경하지 않고 문법적으로 소폭 조정되었다. 총 109개(38%)의 요구사항은 더 이상 버전 5.0에서 별도의 요구사항으로 남아있지 않으며, 50개는 단순히 삭제되었고, 28개는 중복으로 제거되었으며, 31개는 다른 요구사항에 병합되었다. 나머지 요구사항들은 어떤 형태로든 수정되었다. 실질적인 수정이 이루어지지 않은 요구사항조차도 재배열이나 구조 변경으로 인해 식별자가 달라졌다. 

버전 5.0의 원활한 채택을 위해, 버전 4.x의 요구사항이 버전 5.0의 어떤 요구사항에 대응되는지 사용자가 파악할 수 있도록 매핑 문서를 제공한다. 이러한 매핑 문서는 릴리스 버전과 연동되지 않으며, 필요에 따라 업데이트되거나 보완될 수 있다.

## 요구사항 철학

### 범위와 핵심

버전 4.x는 표준에서 정의한 범위에 부합하지 않는 요구사항이 포함되어 있었으며, 이는 제거되었다. 5.0의 범위 기준에 부합하지 않거나 검증이 불가능한 요구사항 또한 제외되었다.

### 보안 메커니즘보다 보안 목표에 중점

버전 4.x에서는 많은 요구사항이 근본적인 보안 목표보다 특정 메커니즘에 집중되어 있었다. 버전 5.0에서는 요구사항이 보안 목표에 중심을 두며, 특정 메커니즘은 유일한 실질적 해결책인 경우에만 참조하거나 예시 또는 보충 안내로 제공한다. 

이러한 접근은 주어진 보안 목표를 달성하기 위해 여러 방법이 존재할 수 있음을 인정하며, 조직의 유연성을 제한할 수 있는 불필요한 규제를 지양한다.

또한, 동일한 보안 문제를 다루는 요구사항은 적절한 경우 통합되었다.

### 문서화된 보안 결정

문서화된 보안 결정이라는 개념은 버전 5.0에서 새롭게 등장한 것처럼 보이지만, 이는 버전 4.0의 정책 적용과 위협 모델링 관련 요구사항의 진화된 형태이다. 이전에는 일부 요구사항이 허용된 네트워크 연결을 결정하는 등 보안 통제 구현을 위한 분석을 암묵적으로 요구하였다.

구현 및 검증에 필요한 정보가 확보되도록, 이러한 기대사항을 명확하고 실행 가능하며 검증할 수 있도록 문서화 요구사항으로 분명히 정의한다. 

## 구조적 변경 및 신규 장

버전 5.0에서는 여러 장에서 완전히 새로운 내용을 도입하였다:

* OAuth 및 OIDC – 접근 위임 및 싱글 사인온(single sign-on; SSO)을 위한 이러한 프로토콜의 광범위한 채택을 고려하여, 개발자가 직면할 수 있는 다양한 시나리오를 다루기 위한 전용 요구사항이 추가되었다. 이 영역은 이전 버전에서 모바일 및 IoT 요구사항을 별도로 분리했던 것처럼, 궁극적으로 독립적인 표준으로 발전할 수 있다.

* WebRTC – 이 기술의 보급이 확산됨에 따라, 고유한 보안 고려사항과 과제들을 별도의 섹션에서 다루고 있다.

또한, 관련된 요구사항들을 논리적으로 묶어 장과 섹션을 구성하도록 개선하였다.

이러한 구조 개편으로 인해 다음과 같은 신규 장이 추가되었다:

* 자체 포함 토큰 – 기존에는 세션 관리 항목에 포함되었으나, 이제는 독립적인 메커니즘이자 OAuth 및 OIDC와 같은 무상태 통신의 기반 요소로 인식되어 별도의 장에서 다뤄진다. 고유한 보안 특성을 고려하여 전용 요구사항이 추가되었으며, 버전 5.x에서 일부 신규 요구사항이 도입되었다.

* 웹 프론트엔드 보안 – 브라우저 기반 애플리케이션의 복잡성이 증가하고 API 중심 아키텍처가 확산됨에 따라, 프론트엔드 보안 요구사항을 별도의 장으로 분리하였다.

* 시큐어 코딩 및 아키텍처 – 기존 장에 포함되지 않았던 일반적인 보안 관행에 대한 신규 요구사항을 이 장에 통합하였다.

버전 5.0의 기타 구성 변경은 목적의 명확화를 위한 것이다. 예를 들어, 입력 검증 요구사항은 정제 및 인코딩 항목과의 연관성보다는 비즈니스 규칙을 강제하는 역할에 초점을 맞추어 비즈니스 로직과 함께 배치되었다.

기존 V1 아키텍처 장은 삭제되었다. 서두에는 범위에서 벗어난 요구사항이 포함되어 있었고, 이후 섹션들은 관련 장으로 재배치되었으며, 요구사항은 중복 제거 및 명확화 작업이 이루어졌다.

## 외부 표준과의 직접 매핑 제거

표준 본문에서는 외부 표준과의 직접 매핑이 제거되었다. 이는 OWASP Common Requirement Enumeration (CRE) 프로젝트와의 매핑을 준비하기 위한 것으로, 이를 통해 ASVS를 다양한 OWASP 프로젝트 및 외부 표준과 연결할 수 있도록 한다.

아래에서 설명된 바와 같이 CWE 및 NIST와의 직접 매핑은 더 이상 유지되지 않는다.

### NIST 디지털 신원 지침과의 결합도 감소

NIST [디지털 신원 지침(SP 800-63)](https://pages.nist.gov/800-63-3/)은 오랫동안 인증 및 권한 부여 제어의 참고 자료로 활용되어 왔다. 버전 4.x에서는 일부 장이 NIST의 구조와 용어에 밀접하게 정렬되어 있었다.

이러한 지침은 여전히 중요한 참고 자료이지만, 지나치게 엄격한 정렬은 널리 통용되지 않는 용어 사용, 유사 요구사항의 중복, 불완전한 매핑과 같은 문제를 초래하였다. 버전 5.0에서는 명확성과 실효성을 높이기 위해 이러한 접근 방식을 지양하였다.

### CWE(Common Weakness Enumeration)와의 결합도 감소

[CWE(Common Weakness Enumeration)](https://cwe.mitre.org/)은 소프트웨어 보안 약점에 대한 유용한 분류 체계를 제공한다. 그러나 카테고리 전용 CWE, 단일 CWE에 대한 매핑의 어려움, 버전 4.x의 부정확한 매핑 등 여러 문제로 인해, 버전 5.0에서는 CWE와의 직접 매핑을 중단하기로 결정하였다.


## Rethinking Level Definitions

Version 4.x described the levels as L1 ("Minimum"), L2 ("Standard"), and L3 ("Advanced"), with the implication that all applications handling sensitive data should meet at least L2.

Version 5.0 addresses several issues with this approach which are described in the following paragraphs.

As a practical matter, whereas version 4.x used tick marks for level indicators, 5.x uses a simple number on all formats of the standard including markdown, PDF, DOCX, CSV, JSON and XML. For backwards compatibility, legacy versions of the CSV, JSON and XML outputs which still use tick marks are also generated.

### Easier Entry Level

Feedback indicated that the large number of Level 1 requirements (~120), combined with its designation as the "minimum" level that is not good enough for most applications, discouraged adoption. Version 5.0 aims to lower this barrier by defining Level 1 primarily around first-layer defense requirements, resulting in clearer and fewer requirements at that level. To demonstrate this numerically, in v4.0.3 there were 128 L1 requirements out of a total of 278 requirements, representing 46%. In 5.0.0 there are 70 L1 requirements out of a total of 345 requirements, representing 20%.

### The Fallacy of Testability

A key factor in selecting controls for Level 1 in version 4.x was their suitability for assessment through "black box" external penetration testing. However, this approach was not fully aligned with the intent of Level 1 as the minimum set of security controls. Some users argued that Level 1 was insufficient for securing applications, while others found it too difficult to test.

Relying on testability as a criterion is both relative and, at times, misleading. The fact that a requirement is testable does not guarantee that it can be tested in an automated or straightforward manner. Moreover, the most easily testable requirements are not always those with the greatest security impact or the simplest to implement.

As such, in version 5.0, the level decisions were made primarily based on risk reduction and also keeping in mind the effort to implement.

### Not Just About Risk

The use of prescriptive, risk-based levels that mandate a specific level for certain applications has proven to be overly rigid. In practice, the prioritization and implementation of security controls depend on multiple factors, including both risk reduction and the effort required for implementation.

Therefore, organizations are encouraged to achieve the level that they feel like they should be achieving based on their maturity and the message they want to send to their users.
