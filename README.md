# Адрес СМК c кодом камень-ножницы-бумага

0xFB2b4b69384a80534a9732ec90242e347E32cBBE

https://goerli.etherscan.io/tx/0x4f140766fc9dff22e3a082a0a2e384498a36129dc3f9c2c44d325e2272f291c5

# ДЗ: камень-ножницы-бумага

0. Зачем commit-reveal?

Поскольку игра не является атомарной операцией, то на определенном ее этапе один из игроков зашлет в код свой ответ, а второй нет. Таким образом у второго игрока будет возможность ответ подглядеть и всегда обыграть первого. Чтобы этого не происходило, нужно захешировать ответ, а после того, как все дадут свой ответ, расшифровать его.

1. В чём особенность смарт-контрактов без конструктора? 

У контракта все равно будет определен дефолтный конструктор без параметров constructor() {}

2. Чем отличается тип смарт-контракта library от типа contract?
 
library содержит переиспользуемый код, деплоятся на специальные адреса. На них накладываются следующие ограничения: у них нет хранилища, поэтому они не могут содержать некостантые переменные состояния; не могут хранить эфир (нет fallback функции); не могу иметь payable функции; не могут наследоваться или быть наследованы; не могут быть уничтожены (нет selfdestruct())

3. Какие типы памяти существуют в EVM?

Storage: Глобальная память, доступная для всех функций контракта. Это постоянное хранилищем, которое сеть Ethereum хранит на каждом узле.
Memory: Локальная память, доступная для каждой функции контракта. Это временная память, которая очищается после выполнения функции.
Calldata: Память для хранения поступающих в функцию данных, включая аргументы функции, неизменяемая.
Stack: стек для загрузки переменных и промежуточных значений, 32-битные слова с максимальной глубиной 1024 слова.

4. Зачем нужен ABI?

Это двоичный интерфейс контракта, который позволяет контрактам взаимодействовать друг с другом и с внешним миром.

5. Зачем нужны вставки assembly в смарт-контакт?

Такие вставки позволяют реализовывать логику, которую невозможно реализовать при помощи plain solidity, например указатели на определенные блоки памяти. Может быть полезно при написании библиотек.

6. Зачем нужен тип msg, tx, block?

Не буду расписывать, зачем нужны все поля в этих типах. В общих словах они предоставляют информацию о блокчейне (номер блока, timestamp) или от текущей транзакции (адрес вызывающий транзакцию, gas price транзакции, количество переданного эфира)

7. Как можно задать случайное значение в смарт-контракт?

Запросить у оракула 