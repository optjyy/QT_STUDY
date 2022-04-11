### Signal and Slot

- 본 게시물은 아래의 링크를 참조하였습니다.
- https://www.bogotobogo.com/Qt/Qt5_SignalsSlotsGui.php

Signal과 Slot은 객체들간의 communication을 위해 사용된다. Signal and Slot 메카니즘은 QT의 중심 기능이고 다른 프레임워크와 가장 차별화된 기능이다.

GUI 프로개르밍에서는 한 widget을 변경하였을 때 다른 widget이 알기를 바란다. 더 일반적으로 얘기하자면 우리는 객체가 다른 객체와 communication하기를 원한다. 예를 들면 user가 click 버튼을 누르면 우리는 window의 close() 함수가 호출되기를 바란다. 오래된 toolkit들은 이러한 기능을 callbacks기능을 이용하여 communication을 구현하였다. callback은 함수 포인터이기 때문에 어떤 이벤트를 감지되었을 때 processing function에게 이 포인터를 넘겨줄 수 있다. 이 때 적절하다면 processing function이 callback을 호출한다. callback은 두가지 결점이 있다. 첫번째로 type-safe하지 않다는 것이다. processing function이 정확한 argument로 함수를 호출할지 확실할 수 없다.
두번째로 calllbakc은 processing function과 강하게 결합된다는 것이다. 이는 processing function이 어떤 callback을 호출할지 알아야하기 때문이다.

Qt에서는 이러한 callback의 대안인 Signals and Slots을 사용한다. Signal은 특정 이벤트가 일어날 때 발생됩니다. Qt의 widget에는 많은 사전에 정의된 signal들이 있지만 widget 상속을 통해 자체 signal을 이에 추가할 수 있다. 

Slot은 특정 signal에 대응하는 함수이다. Qt의 Widget들은 사전에 정의된 slot들을 가지고 있다. 하지만 widget을 상속하고 관심있는 signal을 다룰 수 있는 자체 slot을 추가하는 것이 일반적이다.

Singal and Slot 메카니즘은 type safe 하다. signal의 signature와 이를 받는 slot의 signature는 match되어야한다. 

compiler가 mismatch를 찾으면 알려준다. 

signal과 slot은 약하게 결합한다. signal을 방출하는 class는 slot에 대해 알지 못하낟. Qt의 signal and slot 메카니즘은 singal을 slot에 연결하였을 때 signal의 parameter와 함께 호출되는 것을 보장합니다. signal and slot은 모든 타입의 모든 개수의 argument를 받을 수 있고 완벽히 type safe합니다.

QObject 또는 QT subclass를 상속하는 모든 클래스들은 singal and slot을 포함할 수 있습니다. singal을 객체의 state가 변화될 때 발생합니다. 이것은 객체가 communication을 위해 수행하는 것입니다.객체들은 signal을 수신하였는지에 대해 신경쓰지 않습니다. 이것은 진정한 정보 encapsulation이고 객체를 software component로 사용될 수 있게 보장합니다.

Slot은 signal을 수신할 때 사용될 수 있지만 동시에 일반적인 member function입니다. 객체가 signal을 수신하였는지 알지 못하는 것처럼, slot역시 signal이 어디에 연결되었는지 알지 못합니다. 이것은 QT를 이용하여 독립적인 구성요소를 생성할 수 있음을 보장합니다. slot에 signal을 원하는 만큼 연결할 수 있고, signal도 원하는 slot에 모두 연결할 수 있습니다. signal을 다른 signal에 연결하는 것도 가능합니다.






