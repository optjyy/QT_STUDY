# Hello World!

본 게시물은 아래의 링크를 참조하였습니다.
https://www.bogotobogo.com/Qt/Qt5_TutorialHelloWorld.php

QCoreApplication class는 console Qt Application을 위한 event loop를 제공합니다. 이 class는 Non-GUI application에서 event loop를 제공하기 위해 사용됩니다. 반대로 GUI application을 위해서는 QApplication을 사용할 수 있습니다.

a.exec()를 호출할 때 event loop는 실행됩니다.

이 파일을 컴파일하고 실행시켰을 때 아무 반응도 하지 않습니다. event loop는 실행 중이고, 마우스 클릭과 같은 event를 기다리고 있습니다. 하지만 우리는 event를 발생시키지 않았기 때문에 무한히 실행 중인 상태에 머무릅니다.

이 프로젝트를 컴파일할 때 Qt app은 아래와 같은 순서로 컴파일된다.
1. qmake 가 .pro 파일을 parsing하고 makefile을 만든다.
2. 프로그램이 make (jom in window) 명령어에 의해 만들어진다.
   
   