# tic-tac-toe_3x3

<img alt="tic-tac-toe screen" align="left" width="200" src="tic-tac-toe-screen.png">

---
<p>
Модуль для реалізації гри хрестики-нулики на полі 3x3. Реалізовано на Python з учбовою метою,
але це не заважає використовувати цей пакет для реалізації гри в різноманітних варіантах.

Модуль надає абстрактні класи які визначають інтерфейси для реалізації гри для власних варіантів візуалізації.

В модулі реалізована нескладна консольна гра, яка використовується для демонстрації використання модуля і основних її
конструкцій.
</p>

[відео першого дня вебінару тут](https://www.youtube.com/live/WWJHsMAN1j4)

---

1. [Інсталяція.](#1-інсталяція)
2. [Використання консольного варіанту гри.](#2-використання-консольного-варіанту-гри)
    - [запуск консольного варіанта гри](#21-запуск-консольного-варіанту-гри)
    - [використання консольного варіанту гри як приклада використання API модуля](#22-використання-консольного-варіанту-гри-як-приклада-використання-api-модуля)
3. [Використання модуля для власної реалізації гри.](#3-використання-модуля-для-власної-реалізації-гри)
4. [API модуля.](#4-api-модуля)

---

## 1. Інсталяція.

Встановлення модуля:
```bash
pip install tic-tac-toe-3x3
```

---

## 2. Використання консольного варіанту гри.

Консольний варіант гри використовується для демонстрації можливостей модуля і використання у якості прикладу 
використання API модуля для реалізації власних варіантів гри.

### 2.1. Запуск консольного варіанту гри.

__Запуск консольного варіанта гри:__
```bash 
python -m tic_tac_toe_3x3.console_simple
```

__Опціональні параметри для консольного варіанта гри:__
- -X, гравець із відміткою "X". За замовченням має значення "human", доступні варіанти:
    - 'human' - гравець людина, хід вводиться за допомогою консолі
    - 'random' - компʼютерний гравець, хід обирається випадковим чином з доступних
    - 'minimax' - компʼютерний гравець з алгоритмом minimax, перший хід (якщо він перший) 
    обирається випадковим чином, далі - оптимальним
- -0, гравець із відміткою "0". За замовченням має значення "minimax", доступні варіанти:
    - 'human' - гравець людина, хід вводиться за допомогою консолі
    - 'random' - компʼютерний гравець, хід обирається випадковим чином з доступних
    - 'minimax' - компʼютерний гравець з алгоритмом minimax, перший хід (якщо він перший) 
    обирається випадковим чином, далі - оптимальним (використовується реалізація мінімаксного алгоритму)
- --starting, визначає хто починає гру. За замовченням має значення "X", доступні варіанти:
    - 'X' - гравець із відміткою "X" починає гру
    - '0' - гравець із відміткою "0" починає гру

Приклад запуску консольного варіанту гри із запуском двох компʼютериних 
гравців - з випадковими ходами (X) і використовуючого оптимальну стратегію (0), перший ход робить гравець "0":

```bash
python -m tic_tac_toe_3x3.console_simple -X random -0 minimax --starting 0
```

\* - _зверніть увагу на використання символу цифри 0 (нуль) а не букви "O"!_

### 2.2. Використання консольного варіанту гри як приклада використання API модуля.

Код консольного варіанту гри розташовано в пакеті `tic_tac_toe_3x3.console_simple`.

__Модулі і призначення:__
- \_\_main\_\_.py - використовується для запуску консольного варіанту гри 
- args.py - визначає обробку аргументів командного рядка (функція `parse_args`). Відповідно до введених 
параметрів (або не введених - за замовченням) створює відповідних гравців і визначає хто починає гру.
- cli.py - визначає основну "стартову" функцію `main` для режиму командного рядка: отримає від parse_args() всі 
налаштування для створення гри, створює екземпляр гри ("рушій гри" - екземпляр класу 
tic_tac_toe_3x3.game.engine.TicTacToe) з конкретними параметрами і запускає цикл гри. 
- players.py - визначає клас консольного гравця наслідуючись від абстрактного класу `Player` і реалізує метод 
get_move() - специфічний для консольного гравця метод отримання ходу від гравця.
- renderes.py - визначає клас консольного рендерера наслідуючись від абстрактного класу `Renderer` і реалізує метод 
render() - специфічний для відображення гри в консолі. Також реалізує специфічні функції для використання в 
методі render().

---

## 3. Використання модуля для власної реалізації гри.

__Створення власної реалізації гри__ на основі наданого рушія гри (екземпляр класу `TicTacToe`) буде повторювати логіку 
наведеного консольного варіанту:
- визначити клас специфічного гравця на основі абстрактного класу `Player` і реалізувати метод get_move() - отримати 
хід гравця
- визначити клас специфічного рендерера на основі абстрактного класу `Renderer` і реалізувати метод render() - 
відображення специфічного для гри відображення стану гри (поле, повідомлення)
- визначити модуль (модулі) які отримують первинні налаштування гри (гравці, хто починає гру), створюють і запускають 
відповідний рушій гри (екземпляр класу `TicTacToe`), використовуючи визначені класи гравців і рендерера.

---

## 4. API модуля.

- ### tic_tac_toe_3x3
    - #### tic_tac_toe_3x3.game 
        - ##### [tic_tac_toe_3x3.game.engine](#модуль-tic_tac_toe_3x3gameengine)
        - ##### [tic_tac_toe_3x3.game.players](#модуль-tic_tac_toe_3x3gameplayers)
        - ##### [tic_tac_toe_3x3.game.renderers](#модуль-tic_tac_toe_3x3gamerenderers)
    - #### tic_tac_toe_3x3.logic
        - #### [tic_tac_toe_3x3.logic.exceptions](#модуль-tic_tac_toe_3x3logicexceptions)
        - #### [tic_tac_toe_3x3.logic.minimax](#модуль-tic_tac_toe_3x3logicminimax)
        - #### [tic_tac_toe_3x3.logic.models](#модуль-tic_tac_toe_3x3logicmodels)
        - #### [tic_tac_toe_3x3.logic.validators](#модуль-tic_tac_toe_3x3logicvalidators)
    - #### tic_tac_toe_3x3.console_simple
        - #### [tic_tac_toe_3x3.console_simple.args](#модуль-tic_tac_toe_3x3console_simpleargs)
        - #### [tic_tac_toe_3x3.console_simple.cli](#модуль-tic_tac_toe_3x3console_simplecli)
        - #### [tic_tac_toe_3x3.console_simple.players](#модуль-tic_tac_toe_3x3console_simpleplayers)
        - #### [tic_tac_toe_3x3.console_simple.renderers](#модуль-tic_tac_toe_3x3console_simplerenderers)
        - #### [tic_tac_toe_3x3.console_simple.__main__](#модуль-tic_tac_toe_3x3console_simple__main__)
    
---

- #### Модуль `tic_tac_toe_3x3.game.engine`

    пакет game містить елементи які реалізують ігровий механізм - в тому разі і в загальному вигляді (абстрактні класи):
    - ##### Клас `TicTacToe`
        cтворює гру та реалізує основний ігровий цикл:
        - ###### Параметри:
            - `player1` (`Player`): перший гравець, реалізація якого повинна відповідати абстрактному класу `Player`.
            - `player2` (`Player`): другий гравець, реалізація якого повинна відповідати абстрактному класу `Player`.
            - `renderer` (`Renderer`): реалізація класу, що наслідує абстрактний клас `Renderer` для відображення поточного стану гри.
            - `error_handler` (`ErrorHandler` | `None`, за замовчуванням `None`): функція для обробки помилок.
        - ###### Методи: 
            - `__post_init__(self) -> None`: викликається після ініціалізації для перевірки валідності гравців (різні позначки).
            - `play(self, starting_mark: Mark = Mark("X")) -> None`: створює гру (перший хід визначається параметром `starting_mark`), реалізує цикл гри: відобразити стан гри, перевірити умови завершення гри (якщо так - закінчити цикл), отримати наступний хід від чергового гравця (у випадку помилкового ходу - викликати error_handler(), за замовченням - виклик відсутній) 
            - `get_current_player(self, game_state: GameState) -> Player`: повертає гравця, чия черга робити хід.

---

- #### Модуль `tic_tac_toe_3x3.game.players`

    визначає абстрактний клас `Player` для створення гравців і надає декілька конкретних реалізацій гравців. 
    - ##### Клас `Player`
        абстрактний клас, що представляє гравця в грі.
        - ###### Параметри:
            - `mark` (`Mark`): маркер гравця (наприклад, "X" або "O").
        - ###### Методи:
            - `make_move(self, game_state: GameState) -> GameState`: абстрактний метод, який повинен бути реалізований у підкласах для виконання ходу гравця.

    - ##### Клас `ComputerPlayer(Player)`
        абстрактний клас специфікований для комп'ютерних гравців. Додає затримку перед ходом для імітації "розміреності" гравця.
        - ###### Параметри:
            - `mark` (`Mark`): маркер гравця (наприклад, "X" або "O").
            - `delay_seconds` (`float`): затримка перед ходом у секундах. За замовченням встановлюється 0.25 секунди.
        - ###### Методи:
            - `make_move(self, game_state: GameState) -> GameState`: реалізує хід гравця із затримкою.
            - `get_computer_move(self, game_state: GameState) -> Move`: абстрактний метод, що повинен бути реалізований у підкласах для визначення ходу комп'ютерного гравця.
    
    - ##### Клас `RandomComputerPlayer(ComputerPlayer)`
        компʼютерний гравець що реалізує випадковий хід з числа допустимих правилами гри.
        - ###### Параметри:
            - `mark` (`Mark`): маркер гравця (наприклад, "X" або "O").
            - `delay_seconds` (`float`): затримка перед ходом у секундах. За замовченням встановлюється 0.25 секунди.

    - ##### Клас `MinimaxComputerPlayer(ComputerPlayer)`
        реалізація компʼютерного гравця з алгоритмом minimax для визначення оптимального ходу.

        Якщо цей гравець робить перший хід в грі - він робить випадковий хід. Далі обираються оптимальні ходи з точки зору 
        мінімаксної стратегії.
        - ###### Параметри:
            - `mark` (`Mark`): Маркер гравця (наприклад, "X" або "O").
            - `delay_seconds` (`float`): затримка перед ходом у секундах. За замовченням встановлюється 0.25 секунди.

---

- #### Модуль `tic_tac_toe_3x3.game.renderers`
    - ##### Клас `Renderer`
        абстрактний клас, що представляє рендерер для відображення стану гри.
        - ###### Методи:
            - `render(self, game_state: GameState) -> None`: абстрактний метод, який повинен бути реалізований у підкласах для відображення поточного стану гри.

---

- #### Модуль `tic_tac_toe_3x3.logic.exceptions
    - ##### Клас `InvalidGameState`
        Виключення, яке виникає при некоректному стані гри.
    - ##### Клас `InvalidMove`
        Виключення, яке виникає при некоректному ході.
    - ##### Клас `UnknownGameScore`
        Виключення яке виникає коли граф гри не може бути зважено. Це може сигналізувати про помилковий стан гри.

---

- #### Модуль `tic_tac_toe_3x3.logic.minimax`
    Надає механізми для реалізації алгоритму minimax для визначення оптимального ходу комп'ютерного гравця.
    - ##### Функція `minimax`
        допоміжна функція що реалізує рекурсивний алгоритм minimax оцінки запропонованого ходу (`Movie`)
        повертає оцінку ходу (-1 (програш), 0 (нічия), 1 (перемога)) з точки зору гравця `maximizer` і логіки обрання ходів `choose_highest_score`.
    - ##### Функція `find_best_move`
        повертає найкращий хід з можливих для поточного гравця в стані гри `game_state`.

---

- #### Модуль `tic_tac_toe_3x3.logic.models`
    Модуль описує моделі що відповідають сутностям гри.
    - ##### Константа `WINNING_PATTERNS`
        Список можливих виграшних комбінацій на полі 3x3.
    - ##### Клас `Mark`
        Маркер гравця ("X" або "0").
    - ##### Клас `Grid`
        Стан що зберігає і валідує стан сітки (поля гри).
        - ###### Параметри:
            - `cells` (`str`): рядок що описує стан сітки (може складатись тільки з символів "X", "0" і " ", загальна кількість символів - 9).
        - ###### Методи:
            - `__post_init__(self) -> None:` викликається після ініціалізації для перевірки валідності стану сітки.
        - ###### Властивості
            так як `Grid` є не змінюваним об'єктом, всі властивості - кешовані: обчислюються при першому зверненні, при наступних зверненнях повертаються з кешу.
            - `x_count` (`int`): кількість відміток "X" на сітці.
            - `o_count` (`int`): кількість відміток "0" на сітці.
            - `empty_count` (`int`): кількість пустих клітинок на сітці.
    - ##### Клас `Move`
        Описує хід гравця. Є типовим обʼєктом для передачі стану - DTO.
        - ###### Параметри:
            - `mark` (`Mark`): гравець, що робить хід.
            - `cell_index` (`int`): індекс клітинки на полі (від 0 до 8) - куди робить хід гравець.
            - `before_state` (`GameState`): стан гри до ходу.
            - `after_state` (`GameState`): стан гри після ходу.
    - ##### Клас `GameState`
        Описує стан гри.
        - ###### Параметри:
            - `grid` (`Grid`): стан сітки (поля гри).
            - `starting_mark` (`Mark`): маркер гравця що починає гру. За замовченням має значення `Mark("X")`.
        - ###### Методи:
            - `__post_init__(self) -> None:` викликається після ініціалізації для перевірки валідності стану гри.
            - `make_random_move` (`Move | None`): випадковий хід для поточного гравця.
            - `make_move_to`(`index`: `int`) -> `Move`: створює хід гравця на клітинку з індексом `index`.
            -  `evalute_score(self, maximizer: Mark) -> int`: оцінює стан гри з точки зору гравця `maximizer` (використовується для алгоритму minimax).
        - ###### Властивості
            - `current_mark` (`Mark`): маркер гравця, що робить хід.
            - `game_not_started` (`bool`): показує чи гра не почалася (поле пусте).
            - `tie` (`bool`): показує чи гра закінчилася в нічию.
            - `game_over` (`bool`): показує чи гра закінчилася.
            - `winner` (`Mark | str | None` ): маркер переможця (якщо є).
            - `winning_cells` (`List[int]`): список індексів клітинок, що утворюють виграшну комбінацію (якщо є).
            - `possible_moves` (`List[Move]`): список можливих ходів для поточного гравця.

---

- #### Модуль `tic_tac_toe_3x3.logic.validators`
    Включає валідатори що використовуються в інших частинах коду для валідації.

---

- #### Модуль `tic_tac_toe_3x3.console_simple`
    Надає реалізацію простого консольного варіанту гри.
    Може бути використано як зразок використання API модуля для реалізації власних варіантів гри.

---