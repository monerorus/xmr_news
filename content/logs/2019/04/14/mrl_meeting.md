---    
title: "Журнал встречи исследовательской лаборатории Monero от 2019-03-18"
date: 2019-04-14
id: 1
draft: false
categories: [logs, mrl]
---

> **_sarang:_** 1. ПРИВЕТСТВИЯ    
> **_sarang:_** Всем привет!    
> **_suraeNoether:_** Здравствуйте, коллеги!    
> **_worriedrise:_** Hello    
> **_oneiric:_** здравствуйте мои дорогие    
> **_suraeNoether:_** worriedrise: я почти уверен, что смогу доказать, что экземпляр взаимодействия подписей без стороннего вмешательства достигается без применения особых усилий. Я потратил около часа, работая над этим доказательством в выходные.    
> **_sarang:_** мы обсудим это в ближайшее время, нужно добавить соответствующую повестку дня    
> **_sarang:_** поскольку я уверен, что это вызовет много встречных споров    
> **_sarang:_** 2. КРУГЛЫЙ СТОЛ    
> **_worriedrise:_** С нетерпением жду, чтобы посмотреть на это    
> **_sarang:_** Мы довольно много обсуждали выбор корректных выходных данных и должны подготовиться к этому, чтобы у нас были готовые рекомендации к следующему выпуску    
> **_sarang:_** Распределение выходного возраста для выборок, сделанных различными опциями, располагаются достаточно близко друг к другу при обычных условиях ветвления    
> **_sarang:_** На этом этапе я намерен настоятельно рекомендовать output-lineup метод    
> **_sarang:_** есть мысли по этому поводу?    
> **_suraeNoether:_** я предпочитаю метод очереди, пока мы не определим лучшую альтернативу или, как вариант, лучшие метрики для дальнейшего анализа    
> **_worriedrise:_** Я согласен    
> **_sarang:_** Отлично    
> **_moneromooo:_** методы линейного вывода параметров (при условии, что вы все еще используете гамму) будут сильно отличаться    
> **_sarang:_** Они используют то же самое среднее значение за прошедшие 2 дня, но с повышением среднего периода роста, определяемым цепью (или ее частью)    
> **_moneromooo:_** И это зависит от того, сколько выходов будет в блоке. Мне это кажется фундаментально неправильным решением, хотя на практике это всё работает...    
> **_moneromooo:_** чувствую, что я переборщил :p    
> **_sarang:_** я не знаю лучшего подхода, который будет отвечать всем вашим требованиям    
> **_sarang:_** дело в том, что они используют усреднение для сглаживания колебаний плотности    
> **_suraeNoether:_** какой бы метод мы ни выбрали, нам придется переоценивать параметры выбора, так как всё распределение технически не будет соответствовать гамме?    
> **_suraeNoether:_** повышенная чувствительность к плотности блокчейна на самом деле является особенностью, а не вытекающей ошибкой    
> **_sarang:_** в условиях голода усреднение будет означать, что более старые результаты предпочтительнее, чем среднее значение за прошедшие 2 дня    
> **_moneromooo:_** Я ожидал, что гамма останется    
> **_sarang:_** выбор exp-гаммы останется    
> **_sarang:_** параметры используют средний выходной возраст    
> **_suraeNoether:_** Вопрос к Сарангу о голодовке: распределение времени в реальной жизни очень чувствительно к плотности блокчейна и наоборот. Состояние голода, как описывает Саранг, это «что произойдет, если люди начнут тратить все меньше и меньше или просто увеличат интервал времени между этими тратами?», ответ на это *должен* заключаться в том, что более старые выходы появляются в кольцевых сигнатурах чаще, чем нам хотелось бы    
> **_sarang:_** Я приглашаю людей немного поиграть с алгоритмами и условиями в цепочках с помощью моего нового кода для моделирования ;)    
> **_suraeNoether:_** в ответ на точку зрения moo: мы все еще пытаемся приблизить гамма-распределение с точки зрения возраста одного из будующих выходов, которые должны быть подтверждены    
> **_worriedrise:_** Кто-нибудь смотрит на показатели того, сколько раз выход используется в кольце?    
> **_suraeNoether:_** в любом случае нам следует провести собственный анализ затрат времени и посмотреть, являются ли параметры, приведенные в статье monerolink, верными    
> **_sarang:_** Если я правильно помню, то статистическое среднее имеет тенденцию к фиксированному размеру кольца    
> **_sarang:_** если люди хотят больше аналитической деятельности, то сейчас самое время для этого, у нас как раз появилась рабочая схема и она уже готова к следующему выпуску    
> **_sarang:_** В любом случае: уже есть рабочий тестовый код Bulletproofs MPC, но гарантии безопасности сильно зависят от количества раундов и наличия / отсутствия предварительных условий    
> **_suraeNoether:_** worriedrise и sarang: среднее количество применений на ключ с фиксированным размером кольца R и N всего кольца составляет <= R . Почему? Предположим, что каждая кольцевая подпись имеет R членов и N кольцевых подписей в общей сумме. Тогда существует не менее N ключей (по одному на каждую подпись кольца), поэтому среднее количество применений на ключ - это общее количество применений (N * R), разделенное на общее количество ключей (их N и более). Как-то так    
> **_suraeNoether:_** среднее использование на ключ составляет не более R    
> **_suraeNoether:_** Вы имеете в виду «bulletproofed диапазон доказательства MPCs» правильно? не отдельно взятые произвольные bulletproofed?    
> **_sarang:_** доказательство диапазона    
> **_suraeNoether:_** весьма искусно    
> **_sarang:_** смысл данной идеи распространяется и на общие доказательства    
> **_worriedrise:_** Средний, да. Вопрос в том, будут ли присутствовать кольца в этом случае, которые переоценены или вообще не выбраны?    
> **_sarang:_** наверняка    
> **_worriedrise:_** и насколько данная проблема серьезна?    
> **_suraeNoether:_** стоп, ты вообще читал про lelantus?    
> **_sarang:_** Да, и даже играл с несколькими из их схем реализации, которые они используют    
> **_sarang:_** модификации BPs и сигма-протокол Groth    
> **_sarang:_** больше мне нечего добавить    
> **_sarang:_** Моя заявка на финансирование уже открыта и завершена на 1/3!    
> **_suraeNoether:_** Есть ли у вас мысли или идеи о том, как оценить масштаб кольца lelantus по сравнению с нашим?    
> **_sarang:_** Да, при более тщательном подборе операций и лучшем понимании того, как обрабатываются обязательства в протоколе Groth    
> **_sarang:_** это всё очень круто только на словах    
> **_suraeNoether:_** Хорошо, от меня что-то нужно добавить в этом чтении на данную тему?    
> **_sarang:_** suraeNoether: у вас есть обновления для нас?    
> **_sarang:_** нет, не сейчас    
> **_suraeNoether:_** Итак, моя работа на прошлой неделе вращалась вокруг моделирования моего нового кода, который я хочу сейчас кратко описать:    
> **_suraeNoether:_** я пытаюсь смоделировать блокчейн в «достаточно реалистичной» среде и внедрить в это моделирование какое-то ненормативное поведение, которое может заинтересовать анализатор при машинном обучении поведения    
> **_suraeNoether:_** например, если мы хотим смоделировать классический еженедельный EABE-контроль, этому будет соответствовать встраивание периодического сигнала в эту цепочку блоков    
> **_suraeNoether:_** другой пример: что делать, если конкретный производитель просто нетерпелив и тратит быстрее, чем другие? Получается, что нас ждет экспоненциальное распределение вместо гаммы    
> **_suraeNoether:_** цель моего алгоритма сопоставления состоит в том, чтобы попытаться найти этот встроенный сигнал и увидеть, насколько он применим в данной задаче как с точки зрения ложных срабатываний, так и отрицательных значений    
> **_suraeNoether:_** это можно сравнить с методами, используемыми в monerolink для тестирования подходов, с одним серьезным исключением: цель заключается в том, чтобы оценить мощность статистического теста в широком диапазоне гипотез    
> **_suraeNoether:_** я хочу поговорить с Сарангом сегодня после встречи, чтобы обсудить методы моделирования выбора выхода. В конце концов, если мы хотим в дальнейшем реализовывать одну из четырех схем, имеет смысл реализовать их предварительно в симуляции и протестировать их производительность...    
> **_suraeNoether:_** я хочу подобрать очень точный набор для проведения тестов, чтобы понять суть того, что именно мы хотим тестировать, и какую информацию нам нужно получить в итоге для принятия обоснованных решений    
> **_suraeNoether:_** с другой стороны, мы всё равно получим довольно строгий набор симуляций для воспроизведения моноблочных цепей    
> **_sarang:_** отличная работа!    
> **_worriedrise:_** Можем ли мы как-то отслеживать, какие выходы могут быть переоценены или вообще не выбраны, как я упоминал ранее    
> **_suraeNoether:_** другие мои обновления касаются вопросов безопасности dlsag и слушания об обобщениях конструкции keccak для семейства хэш-функций parazoa    
> **_worriedrise:_** Я считаю, что это может быть отличным исследованием    
> **_moneromooo:_** Я думаю, что вы можете воссоздать это с помощью инструментов в src/blockchain_utilities    
> **_sarang:_** worriedrise: как эти данные повлияют на выбор выходных данных?    
> **_worriedrise:_** Если мы сможем найти определенные результаты, которые последовательно отбираются, это, скорее всего, и будет истинный отправитель    
> **_worriedrise:_** И наоборот    
> **_worriedrise:_** это может происходить с подходом через равномерный выбор в разрезе небольших блоков, а не только для выхода на основе coinbase    
> **_sarang:_** мы видим, что результаты выбираются с неправильным взвешиванием ссылаясь на размеры блока    
> **_worriedrise:_** Выходы из Coinbase легко заметить    
> **_sarang:_** Цифры для output-lineup показывают, что это гораздо практичнее со стороны математики    
> **_sarang:_** Мой инструмент может предоставить эти самые цифры    
> **_suraeNoether:_** worriedrise, это действительно интересная эвристика. Но, я не слишком переживаю из-за этого    
> **_sarang:_** например, как часто выбираются выходные данные в блоках размера X относительно их появления в цепочке    
> **_worriedrise:_** Да, но мы должны проверить, смогут ли другие методы сделать это непреднамеренно    
> **_sarang:_** Что ты имеешь в виду? Ведь мы можем проверить эти данные для всех предложенных методов    
> **_sarang:_** просто запустите инструмент симуляции, выбрав предпочтительный метод выбора и условие для плотности цепи    
> **_sarang:_** (включая настоящую цепочку)    
> **_worriedrise:_** верю, что сможем, я просто не был уверен в этом    
> **_sarang:_** Хорошо, понял    
> **_sarang:_** Я добавил эту функциональность еще неделю назад в мой инструмент    
> **_sarang:_** Не стесняйтесь запускать его, если вы действительно хотите поэкспериментировать с полученными результатами :p    
> **_sarang:_** (ссылка в повестке дня)    
> **_worriedrise:_** Спасибо. Я его не видел    
> **_sarang:_** всегда пожалуйста    
> **_suraeNoether:_** итак, мое главное беспокойство основано на отсутствии дисперсии    
> **_worriedrise:_** Как насчет фактической цепочки блоков, у нас есть эти данные?    
> **_suraeNoether:_** если средней размер кольца < или = 11, в том случае когда у нас фиксированный размер кольца - 11, дисперсия использования на выход будет просто *огромной*    
> **_sarang:_** worriedrise: эти данные означают, что...    
> **_suraeNoether:_** эта эвристика получится ужасной    
> **_sarang:_** плотность цепи или частота выбора, основанная на плохом взвешивании данных?    
> **_worriedrise:_** Согласен. Мы можем встретить проблему с coinbase выходами.    
> **_worriedrise:_** Данные выходов используют в реальном блокчейне. И у нас уже готовы данные для сравнения    
> **_worriedrise:_** Не только для моделирования    
> **_sarang:_** У меня нет данных о том, как часто выбираются выходы из небольших блоков    
> **_sarang:_** Зато у меня есть данные о том, как действует текущая схема выбора при смоделированных выборках из фактической цепочки    
> **_worriedrise:_** Это хороший показатель. Мне интересно, что из этого получиться :)    
> **_suraeNoether:_** мы можем гоняться за эвристикой весь день, давайте двигаться дальше    
> **_suraeNoether:_** Да    
> **_worriedrise:_** Хорошо    
> **_suraeNoether:_** worriedrise: ничто не мешает вам собирать данные, тщательно изучать и делать соответствующие выводы    
> **_suraeNoether:_** как правило, я всегда выступаю за любые дополнительные данные    
> **_worriedrise:_** Я не знаю, как это сделать, но я обязательно посмотрю    
> **_sarang:_** suraeNoether: у вас есть что-нибудь еще, что можно рассмотреть на собрании?    
> **_suraeNoether:_** у меня всё, хотя я подозреваю, что черновик соответствующего документа выйдет в свет на этой неделе (хоть я и сказал ранее, что он должен появиться на прошлой)    
> **_sarang:_** ладно    
> **_sarang:_** worriedrise/randomrun еще была идея сделать MLSAG короче: https://github.com/monero-project/research-lab/issues/52    
> **_sarang:_** Это переросло в идею общих MLSAG, в которой применяется своего рода агрегация ключей    
> **_sarang:_** Хотите прокомментировать или обсудить?    
> **_worriedrise:_** конечно    
> **_worriedrise:_** это то, что казалось бы вполне разумным решением, но сейчас у меня нет никаких доказательств безопасности использования этого метода    
> **_suraeNoether:_** для простых транзакций ringct в этом подходе используется агрегация ключей, как в Musig, с сигнатурами LSAG для создания RingCT. Общий размер подписей меньше, хотя время проверки занимает примерно столько же    
> **_worriedrise:_** Идея заключается в использовании линейной хешированной комбинации для агрегирования ключей    
> **_worriedrise:_** в один ключ подписи    
> **_worriedrise:_** хотя общая связанность выглядит сложнее    
> **_sarang:_** верно    
> **_sarang:_** в худшем случае потребуется новый формат образа    
> **_sarang:_** в лучшем - вторая точка образа, верно?    
> **_suraeNoether:_** доказательство неприкосновенности из-за его структуры сводится аналогичному доказательству, похожему на доказательство безопасности для бумажных подписей (https://eprint.iacr.org/2018/774.pdf)    
> **_suraeNoether:_** именно, только выглядит сложнее    
> **_worriedrise:_** Правильно, это хорошо работает только с предыдущим правилом    
> **_suraeNoether:_** *одобрительно кивает головой*    
> **_worriedrise:_** Удалось ли вам записать, как это будет работать, не меняя образ ключа?    
> **_sarang:_** вы имеете в виду общую форму?    
> **_sarang:_** к сожалению, нет    
> **_worriedrise:_** Я хотел бы пологать, что bc будет хорошо работать в купе с DLSAG.    
> **_sarang:_** Конкретная форма будет работать и с уже существующим образом ключа, но добавит вторую точку как вы уже говорили ранее    
> **_worriedrise:_** да, вижу    
> **_sarang:_** я только сегодня начал детально изучать эту схему!    
> **_worriedrise:_** Да, но только для агрегирования суммы    
> **_worriedrise:_** Мне кажется, что нам нужны разные наборы констант для различных образов ключей    
> **_worriedrise:_** с изменением образа ключа все они объедятся воедино    
> **_worriedrise:_** проблема в том, что это не работает для DLSAG    
> **_sarang:_** правильно    
> **_worriedrise:_** Поскольку их образы ключей не определены в общей точке    
> **_worriedrise:_** я пытаюсь проследить этот путь    
> **_worriedrise:_** буду рад услышать ваши комментарии :)    
> **_sarang:_** Это хорошая идея    
> **_worriedrise:_** Спасибо!    
> **_sarang:_** Как только эта встреча закончится, я займусь ее пересмотром    
> **_worriedrise:_** Это все выглядит слишком хорошо, чтобы быть правдой. Пожалуйста, внимательно перепроверьте это еще раз    
> **_worriedrise:_** отлично    
> **_sarang:_** вопросы?    
> **_sarang:_** конечно, будем продолжать расследование!    
> **_suraeNoether:_** информация о Konferenco: мы уже начинаем покупать билеты для выступающих    
> **_suraeNoether:_** Билеты на конференцию скоро поступят в продажу (tm)    
> **_suraeNoether:_** Если кто-то хочет представить тезисы, пожалуйста, не стесняйтесь! Просто, перейдите по адресу konferenco.xyz    
> **_sarang:_** я очень воодушевлен этой новостью!    
> **_suraeNoether:_** У нас отличный список из выступающих, и нам нужно еще больше!    
> **_sarang:_** Возможно, мы сможем увидеть worriedrise/randomrun :D    
> **_worriedrise:_** Я видел, что в мае ты будешь в Нью-Йорке    
> **_worriedrise:_** на другой конференции    
> **_h4sh3d[m]:_** Каких именно выступающих вы ищете?    
> **_suraeNoether:_** я считаю, что у нас может быть кто-то из фонда по правам человека и/или активист, работающий в Венесуэле, и еще у нас есть исполнительный директор coincenter - Джерри Брито    
> **_suraeNoether:_** h4sh3d[m]: кто угодно, если его выступление хоть как-то связано с технической составляющей или технологиями Monero, или как вариант, темы о повышении конфиденциальности в целом    
> **_suraeNoether:_** у нас также есть выступающие о социальных последствиях при развитии этих технологий. В общем, только научная работа, никаких ICO, сбор интеллектуалов, только хардкор!    
> **_suraeNoether:_** если у вас есть идея для выступления, вы также можете представить её    
> **_suraeNoether:_** worriedrise: да, я буду на MCC    
> **_sarang:_** suraeNoether, ты счастливчик!    
> **_suraeNoether:_** у меня такое чувство, что на меня хотят повесить всю организацию предстоящей встречи :p    
> **_worriedrise:_** Поскольку мы сейчас говорим о других технологиях, что вы думаете об идее иметь Monero адреса в качестве адресов Bitmessage?    
> **_worriedrise:_** https://github.com/monero-project/research-lab/issues/51    
> **_worriedrise:_** Я знаю, что есть некая проблема с порядком шифрования и аутентификации    
> **_sarang:_** Кажется разумным, если использовать это правильно!    
> **_worriedrise:_** если мы это переживем...    
> **_worriedrise:_** спасибо    
> **_suraeNoether:_** я просто еще не думал об этом    
> **_worriedrise:_** Не могли бы вы объяснить, в чем именно заключается проблема    
> **_suraeNoether:_** простой способ исправить это - использование ключевых структур    
> **_suraeNoether:_** Итак    
> **_suraeNoether:_** когда вы планируете воспользоваться данными функциями, не думаю, что вы хотите проходить аутентификацию и только затем использовать шифрование    
> **_suraeNoether:_** с последующей расшифровкой и только затем проверкой, я имею в виду    
> **_sarang:_** угу    
> **_suraeNoether:_** это плохой способ, потому что вы в конечном итоге расшифровываете что-то, не зная, что именно и от кого оно поступило    
> **_suraeNoether:_** с другой стороны, если шифрованный текст подписан ключом аутентификации, то вы знаете, кто подписал его, и только затем «одобряете» шифрованный текст    
> **_suraeNoether:_** сначала вы проверяете подпись и только затем расшифровываете текст    
> **_nioc:_** не знаю, имеет ли это какое-либо отношение, но rbrunner использовал bitmessage для своей схемы multisig (MMS)    
> **_worriedrise:_** Что плохого в том, чтобы не знать, от кого пришло сообщение?    
> **_worriedrise:_** вы могли бы прочитать его позже, разве нет?    
> **_worriedrise:_** как только введете свой ключ    
> **_suraeNoether:_** вот пример    
> **_sarang:_** Вы не знаете наверняка, было ли изменено зашифрованное сообщение    
> **_suraeNoether:_** почему данная реализация опасна    
> **_worriedrise:_** Я бы знал, ведь это было подписано сопроводительным ключом    
> **_suraeNoether:_** грубый пример: «что если разработчик приложения расшифровывает зашифрованный текст и начинает выполнять его как код, параллельно проверяя, что подпись действительна? Получается, тогда вы запускаете произвольный код, не зная, что в нем». И мне кажется, что разработчик должен делать это в обратном порядке...    
> **_worriedrise:_** При первом контакте мне просто нужно взять этот ключ, и с этого момента я буду знать, подписаны ли другие данные этим ключом    
> **_suraeNoether:_** на самом деле ответ нет, шифрование/дешифрование должно идти совсем в обратном порядке    
> **_suraeNoether:_** конечно, это глупый и очень злонамеренный пример для проведения аналогии    
> **_suraeNoether:_** Есть куда более безобидные примеры, такие как упоминал Саранг, что вы не знаете, действительно ли зашифрованный текст расшифровывается до ожидаемого текста    
> **_suraeNoether:_** и, честно говоря, это основной корень проблемы    
> **_moneromooo:_** разработчик приложения не может проверить подпись и начинает выполнять зашифрованный текст как код?    
> **_suraeNoether:_** зашифрованный текст неотличим от белого шума, поэтому он вряд ли что-то сможет выполнить :D    
> **_sarang:_** это будет отличная встреча!    
> **_moneromooo:_** Зашифрованный текст находится под контролем атакующего    
> **_suraeNoether:_** [https://link.springer.com/chapter/10.1007/3-540-44448-3_41](https://link.springer.com/chapter/10.1007/3-540-44448-3%5C_41) эта статья является отличным примером    
> **_worriedrise:_** Понял, я подумаю об этом на досуге. Интересно, как эта проблема решается в Bitmessage    
> **_suraeNoether:_** moneromooo: верно, но в этот момент разработчик просто выполняет случайный код, полученный от сторонней организации    
> **_moneromooo:_** Ты тоже так думал :)    
> **_sarang:_** В интересах экономии времени давайте рассмотрим пункты, касающиеся этой встречи, а затем продолжим дальнейшее обсуждение    
> **_sarang:_** Я планирую поговорить с suraeNoether о выборе выхода, возможно, у него появятся какие-то мысли на этот счет, в дополнении я подробно рассмотрю изменения MLSAG и продолжу эксперименты с Lelantus    
> **_sarang:_** и посмотрите мой запрос на финансирование, в конце концов! :p    
> **_suraeNoether:_** moneromooo, нет, в моем примере разработчик сначала расшифровывает выполняемый код :D    
> **_sarang:_** suraeNoether: ваши планы на эту неделю?    
> **_suraeNoether:_** 1) запрос на финансирование 2) ежемесячный отчет 3) симуляции 4) безопасность dlsag 5) снижение безопасности mlsag    
> **_suraeNoether:_** Оу! И закончить прочтение материала о parazoa    
> **_sarang:_** Зашибись    
> **_sarang:_** Любые вопросы или замечания, прежде чем мы официально закроем сегодняшнюю встречу?    
> **_sarang:_** Спасибо, что присоединились к нам!    
> **_worriedrise:_** Это вам спасибо!    
> **_sarang:_** Спасибо всем за участие. Объявляю перерыв!    

---
_Источник:_ [_Logs for the Monero Research Lab Meeting Held on 2019-03-18_](https://repo.getmonero.org/monero-project/monero-site/blob/b87354501b6343f9146f331805ddadc45696f728/_posts/2019-03-18-logs-for-the-Monero-Research-Lab-meeting-held-on-2019-03-18.md)  
_Перевод: [Unholy](https://xmr.ru/members/754/) (@Unholy)  
Редактирование: [Mr. Pickles](https://xmr.ru/members/50/) (@v1docq47)  
Коррекция: [Kukima](https://xmr.ru/members/138/) (@Kukima)_