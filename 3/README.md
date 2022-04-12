### Q_OBJECT Macro

Q_OBJECT MACRO는 Qt를 시작하는 사람들에게 이상하게 느껴진다.

Qt QObject Class :
    Q_OBJECT macro는 class를 정의할 때 private section에 항상 있어야한다. class를 정의할 때 signal, slot과 QT의 meta-object system에서 제공되는 다른 서비스들도 선언한다.

이것은 signal과 slot을 사용할 필요가 있는 것 처럼 느껴진다.

- 아래는 MOC(Meta-Object Complicer) 와 관련된 다른 문서에서 발췌한 내용이다.

"""
MOC(Meta-Object Compiler) 는 QT의 C++ Extension을 다루는 프로그램이다. MOC tool은 C++ header 파일을 읽는다. 이 때 class 정의에서 Q_OBJECT macro를 발견하면 해당 class에 대해 meta-object code를 포함한 C++ source file을 생성합니다. meta-object code는 signal and slot 메카니즘(run-time type 정보, 그리고 동적 property 시스템)에 필요합니다.
"""
- 아래는 Signal and slot에 대한 다른 문서이다.
"""
signal과 slot을 포함하는 모든 class는 선언시 최상단에 Q_OBJECT를 언급해야한다. 또한 QObject에서 파생되어야한다. (직간접적으로)
"""

- signal과 slot간의 연결을 만들기 위해 Object Scope를 이용한다.
"""
QObject::connect(sender, signal, receiver, slot):
"""

- Q_OBJECT Macro가 항상 필요한가?
항상 필요하지는 않지만 넣어두는 것이 좋다.
실제로 Q_OBJECT Macro는 meta-object code가 생성되어야할 때(singal and slot 메카니즘을 moct tool이 사용할 때)만 필요하다.
하지만 Q_OBJECT를 Q_OBJECT macro, meta object 코드 없이 사용하는 것은 가능하지만, signal and slot 또는 다른 기능들을 사용할 수 없다.