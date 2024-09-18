# CardProject
- 객체지향 프로그래밍 수업
기본적인 카드 게임을 구현하는 Kotlin 프로그램입니다. 
다양한 카드와 플레이어를 포함하여 카드 덱을 관리하고, 게임의 기본 로직을 제공합니다.

## 📗 개요
- **목표**: 다양한 카드 게임을 구현하고 실행할 수 있도록 하는 것.
- **기능**:
  - 카드 종류 및 모양 지원
  - 플레이어 클래스 구현
  - HTML 형식으로 카드 상태 표시
  - 게임 덱 관리
 
## 코드 설명

    val deck = GameDeck() // 새로운 카드 덱 생성
    val player = HumanPlayer() // 인간 플레이어 생성
    player.draw(deck) // 덱에서 카드 뽑기
    println(player.toHTML()) // 플레이어의 카드 표시

Card 클래스
카드의 종류를 정의합니다. 각 카드는 심볼, 색상, 값을 가지고 있습니다.

    enum class Card(val face: String, val back: String = "🂠") {
        SA("🂡"), S2("🂢"), ... // 여러 카드 타입
        fun symbol() {...}
        fun color() {...}
    }
  
CardItem 데이터 클래스
카드의 상턔(앞 또는 뒷면)을 유지합니다.

    data class CardItem(val card: Card, var up: Boolean = false) {
        fun show() = if (up) card.face else card.back
    }
GameDeck 클래스
카드 덱을 관리하고, 카드를 뽑고 추가하는 기능을 제공합니다

    class GameDeck() : Deck {
        val d_list: MutableList<CardItem> = ...
        override fun draw(): CardItem {...}
    }
플레이어
두 종류의 플레이어 클래스를 구현합니다: HumanPlayer와 ComputerPlayer

    class HumanPlayer : Player {
        override fun draw(d: Deck) {...}
         override fun put(d: Deck) {...}
    }

    class ComputerPlayer : Player {
        override fun draw(d: Deck) {...}
        override fun put(d: Deck) {...}
    }

