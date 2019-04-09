---
title: "Журнал встречи разработчиков Monero от 2019-01-28​"
date: 2019-01-28
id: 1
draft: false
categories: [logs, devs]
---   
 
> _**dEBRUYNE:**_ Встреча разработчиков?  
> _**rbrunner:**_ Скорее да, чем нет  
> _**rbrunner**_ Люди все еще истощены от встречи по поводу идентификатора платежа :)  
> _**dEBRUYNE:**_ Думаю, мы могли бы пропинговать людей  
> _**dEBRUYNE:**_ vtnerd, moneromooo, hyc, gingeropolous, TheCharlatan, sarang, suraeNoether, jtgrassie  
> _**dEBRUYNE:**_ Кто-нибудь хочет поучаствовать?  
> _**jtgrassie:**_ Да, я здесь  
> _**vtnerd:**_ Здесь  
> _**oneiric\_:**_ o/  
> _**dEBRUYNE:**_ Может, нам просто стоит начать, и люди сами подтянуться?  
> _**rehrar:**_ Оуу  
> _**rehrar:**_ извините, ребята, я работаю над новым оформлением FFS, у меня совсем вылетело из головы про эту встречу...  
> _**rehrar:**_ Это может случиться уже завтра  
> _**rbrunner:**_ Я знаю это состояние, называется "поток" :)  
> _**rehrar:**_ давай, действуй, dEBRUYNE  
> _**rehrar:**_ ребята, вам обязательно понравится этот новый внешний вид FFS. Он готов на 99%\  
> _**sarang:**_ Hi  
> _**oneiric\_:**_ rehrar: кто-то уже выполнил какие задачи?  
> _**dEBRUYNE:**_ Хорошо, jtgrassie, возможно, вы бы хотели начать с краткого описания вашего последнего PR? https://github.com/monero-project/monero/pull/5091  
> _**rehrar**_ oneiric, xiphon всё сделал  
> _**rehrar**_ как... положено...  
> _**dEBRUYNE:**_ Насколько я понимаю, это позволяет пользователю пропускать свою транзакцию через I2P, маскируя тем самым исходный IP-адрес отправителя / пользователя  
> _**oneiric\_:**_ великолепно  
> _**dEBRUYNE:**_ И это может работать с PR vtnerd, верно?  
> _**jtgrassie:**_ Конечно. В основном он просто основан на материалах Tor от vtnerds  
> _**oneiric\_:**_ dEBRUYNE, извини  
> _**jtgrassie:**_ На самом деле не так много добавлено  
> _**jtgrassie:**_ Я его запустил и протестировал  
> _**dEBRUYNE:**_ С точки зрения пользователя, что именно нужно будет настроить?  
> _**vtnerd:**_ Довольно мило  
> _**dEBRUYNE:**_ Предполагаю, что PR уже включен в бинарные файлы выпуска  
> _**jtgrassie**_ Я использовал i2p-zero от knacccs во время тестирования, но, конечно, всё будет работать с любой сторонней настройкой i2p  
> _**dEBRUYNE oneiric\_:**_ извините, dEBRUYNE <= Np  
> _**rbrunner:**_ Похоже, стоявшие плотины ломаются... Теперь, когда над будущем Kovri нависли темные тучи, и люди берут дело в свои руки...  
> _**jtgrassie:**_ По идее пользователь должен запустить i2p, сервис socks и входящий туннель  
> _**jtgrassie:**_ В основном процедура идентична с Tor  
> _**dEBRUYNE:**_ Хорошо, всё разумно, но в любом случае мы напишем соответствующую документацию для этого (подробное руководство)  
> _**jtgrassie:**_ rbrunner, да, у knaccc хороший кредит доверия с его i2p-zero  
> _**jtgrassie:**_ dEBRUYNE: Документация со стороны Monero уже готова, если я правильно понял. Но нужно подтянуть хвосты со стороны i2p  
> _**dEBRUYNE:**_ Я полагаю, мы могли бы написать несколько руководств для самых популярных реализаций?  
> _**jtgrassie:**_ например, для i2p-zero, для i2pd или Kovri они, конечно, будут другими  
> _**dEBRUYNE:**_ Понятно, здорово  
> _**dEBRUYNE:**_ vtnerd: Вы хотите что-нибудь добавить?  
> _**oneiric\_:**_ можно ли изменить текущее руководство kovri для использования Monero совместно с --exclusive-peer для новой поддержки прокси?  
> _**jtgrassie:**_ I2P-zero работает и протестирован совместно с #5091, я планирую обратиться за помощью к knaccc для более тщательной проверки и наведения финального лоска.  
> _**vtnerd**_Добавлена поддержка socks в базовых кошельках  
> _**sarang:**_ ^ Великолепно  
> _**jtgrassie:**_ Да vtnerd Я еще не проверял это, но выглядит здорово  
> _**vtnerd:**_ Таким образом, соединения с `monerod` через Tor / i2p возможны в пределах кошелька cli и wallet rpc  
> _**dEBRUYNE:**_ Великолепно  
> _**vtnerd:**_ Это также подразумевает аутентификацию + шифрование, даже если ssl не используется  
> _**dEBRUYNE:**_ Всё верно  
> _**dEBRUYNE:**_ moneromooo: ты здесь? Если да, не могли бы вы поделиться тем, над чем работали в последнее время?  
> _**moneromooo:**_ Я  
> _**moneromooo:**_ Возродил SSL PR, написал материал о сборах для нескольких отправителей и работаю над реализацией нового алгоритма размера блока от ArticMine...  
> _**dEBRUYNE:**_ Я полагаю, что сборы для нескольких отправителей работают аналогично multisig, поскольку отправители должны обмениваться данными, прежде чем транзакция может быть выполнена, верно?  
> _**moneromooo:**_ Да.  
> _**jtgrassie:**_ Я вижу, что есть 2 PR о SSL. В чем разница?  
> _**dEBRUYNE:**_ Теоретически это позволит отправителю предоставить выход наиболее корректно? Что будет похоже на P2EP у Bitcoin  
> _**moneromooo:**_ Второй добавляет некоторые нововведения, такие как возможность выбора сертификата по отпечатку пальца  
> _**moneromooo:**_ Да.  
> _**moneromooo:**_ (для первого предложения)  
> _**dEBRUYNE:**_ Все отлично  
> _**dEBRUYNE:**_ Для любого слушателя это нарушает предположение о входных данных, принадлежащих одному отправителю, что довольно сильно затрудняет анализ  
> _**rbrunner:**_ Хороший побочный эффект  
> _**rbrunner**_Довольно много работы предстоит, что бы полноценно интегрировать данный функционал  
> _**dEBRUYNE:**_ rbrunner: Что-нибудь, чем бы ты хотел поделиться?  
> _**rbrunner:**_ Да, просто немного информации  
> _**rbrunner:**_ Я начал своё исследование в направлении интеграции Monero в OpenBazaar  
> _**rbrunner:**_ Я уже поговорил с 2 их разработчиками, было очень интересно  
> _**rbrunner:**_ Через 2 / 3 недели я собираюсь предоставить отчет  
> _**rbrunner:**_ Слишком рано, чтобы сказать что-то ещё :)  
> _**dEBRUYNE:**_ Скоро мы непременно всё узнаем :)  
> _**rbrunner:**_ Угу  
> _**rbrunner:**_ ещё я в настоящее время борюсь с отладкой Go  
> _**rbrunner:**_ это целый новый мир для меня  
> _**dEBRUYNE:**_ moneromooo: Пушистый поделился какими-либо идеями относительно предстоящего выпуска 0.14 кстати?  
> _**moneromooo:**_ Нет.  
> _**dEBRUYNE:**_ Понятно  
> _**jtgrassie:**_ Я бы хотел, чтобы PR для tor и i2p объединили как можно раньше, чтобы мы могли провести как можно больше тестов  
> _**oneiric\_:**_ ^ +1  
> _**rbrunner:**_ Разве это не должно быть проверено за время замораживания кода?  
> _**dEBRUYNE:**_ fluffypony, luigi1111 ^  
> _**dEBRUYNE:**_ кстати, я могу предоставить небольшое обновление относительно GUI  
> _**dEBRUYNE:**_ Как всегда, множество исправлений и улучшений :p  
> _**dEBRUYNE:**_ selsta добавил функцию поддержки нескольких учетных записей  
> _**dEBRUYNE:**_ dsc\_ обновил автоматические настройки и теперь начнет работать над реализацией различных режимов совместимости и белой темы  
> _**rbrunner:**_ dsc\_ уже работает полный рабочий день над GUI?  
> _**dsc\_:**_ Да  
> _**rbrunner:**_ :)  
> _**rehrar:**_ dsc\_ цыпа :p  
> _**dEBRUYNE:**_ В свете недавнего обсуждения идентификатора платежа мы отключили возможность добавления идентификатора платежа по умолчанию, пользователю необходимо включить этот параметр вручную в меню настроек.  
> _**dsc\_:**_ rehrar ^  
> _**sarang:**_ Чудесно  
> _**rehrar:**_ Я говорил об этом на прошедшем Monero Coffe Chat, считаю это не очень хорошим решением  
> _**sarang:**_ Как он обрабатывает интегрированные адреса? Так же как и раньше?  
> _**sarang:**_ rehrar ?  
> _**rehrar:**_ Уже в течении нескольких месяцев мы топчемся на одном и том же месте  
> _**endogenic:**_ Я согласен с rehrar  
> _**rehrar:**_ Следует также удалить возможность включения данной опции, если мы собираемся избавиться от идентификаторов платежей  
> _**dEBRUYNE:**_ rehrar: Новый релиз GUI не будет доступен до середины марта  
> _**dEBRUYNE:**_ Что на несколько недель раньше запланированного обновления протокола  
> _**rehrar:**_ Удаление идентификатора платежа происходит в октябре  
> _**rehrar:**_ верно, идентификаторы платежей не удаляются в марте  
> _**dEBRUYNE:**_ Разве у нас не было единого мнения об удалении старых незашифрованных идентификаторов платежей в марте?  
> _**rehrar:**_ их убирают в октябре :)  
> _**sarang:**_ Мы обсуждали начало компании в марте  
> _**sarang:**_ и последующий отказ от них в октябре  
> _**rehrar:**_ хорошо, тогда, если мы собираемся сделать это, мы должны взять на себя обязательство связаться с биржами, такими как Binance, которые используют их, и помочь им избавиться от них в течении нескольких следующих месяцев  
> _**sarang:**_ (от незашифрованных)  
> _**rehrar:**_ Объем Binance огромен, если они все еще используют их, то на момент обновления люди будут очень расстроены, что они не могут вносить депозиты в XMR  
> _**rehrar:**_ Я просто рассуждаю с точки зрения рядового пользователя  
> _**dEBRUYNE:**_ Я думал, что незашифрованный в апреле и следом зашифрованный в октябре  
> _**dEBRUYNE:**_ Да, я согласен  
> _**sarang:**_ Хронология и примечания: https://github.com/monero-project/meta/issues/299  
> _**ErCiccione[m]:**_ удалить их в марте невозможно, биржи до сих пор их используют  
> _**dEBRUYNE:**_ При необходимости мы можем перенести до выпуска 0.15  
> _**rbrunner:**_ Ну, у них сложилось двоякое впечатление от журнала
> _**sarang:**_ всё это обсуждалось на предыдущем заседании  
> _**rehrar:**_ Мы должны заставить всю экосистему отказаться и отключить идентификаторы платежей, прежде чем мы удалим их  
> _**sarang:**_ Удалить = Сделать трудным в использовании  
> _**rbrunner:**_ ... или сделать их более трудными, да?  
> _**sarang:**_ sgp\_, проверка связи  
> _**rehrar:**_ sarang, понимаю, и я согласился с вами во время встречи. Но потом я начал думать об этом как обычный пользователь, которым я и являюсь.  
> _**rehrar:**_ И это стало для меня довольно серьезной проблемой  
> _**endogenic:**_ я думаю, что сделать их более сложными для генерации - отличная идея, но сделать их трудными для использования - не самая лучшая  
> _**endogenic:**_ ну, возможно и так  
> _**rehrar:**_ ^  
> _**dEBRUYNE:**_ Если мы перенесём решение данного вопроса на ноябрь, разве мы не столкнёмся с точно такими же вопросами и проблемами?  
> _**sgp\_:**_ Пользовательский интерфейс может предоставить расширяемое поле идентификатора платежа, например, в MyMonero  
> _**rehrar:**_ Безрассудно просто удалять вариант, который использует вся экосистема. Поэтому я предлагаю сохранить идентификатор платежа в пользовательском интерфейсе до октября  
> _**rehrar:**_ нет, dEBRYUNE, потому что они будут запрещены консенсусом  
> _**endogenic:**_ sgp\_, ИМХО, это может быть неправильным направлением распределения сил разработчиков  
> _**endogenic:**_ это относительно незначительный момент  
> _**jtgrassie:**_ Ничто не измениться, пока биржи и торговые площадки не сделают шаг на встречу  
> _**dEBRUYNE:**_ Всё верно  
> _**rehrar:**_ Проблема в том, что консенсус будет в апреле, и сервисы не будут обновляться до самого последнего момента. Таким образом, мы всё ещё должны оставить этот функционал в пользовательском интерфейсе  
> _**sgp\_:**_ endogenic, эти изменения уже объединены в GUI  
> _**endogenic:**_ ok  
> _**rehrar:**_ Но, когда они будут запрещены, биржи и сервисы будут вынуждены обновлять ПО или прекращать использование Monero, и только после этого мы сможем удалить их  
> _**sarang:**_ rehrar: это сильное заявление  
> _**rehrar:**_ Саранг, что они собрались обновлять?  
> _**sarang:**_ Да  
> _**rehrar:**_ Если они этого не сделают, то они не могут использовать Monero  
> _**jtgrassie:**_ Что, если для обмена потребуется идентификатор платежа?  
> _**rehrar:**_ Значит октябрь  
> _**rbrunner:**_ Выглядит не особо сложным  
> _**dEBRUYNE:**_ Хорошо, и информация для информации: мы все еще намерены отменить зашифрованные идентификаторы платежей в апреле, верно?  
> _**rehrar:**_ термин "устаревший" не значит, что это плохая функция, если её все еще используют  
> _**rehrar:**_ да, всё правильно  
> _**rehrar:**_ jtgrassie, точно  
> _**dEBRUYNE:**_ Тогда всё сходиться  
> _**sgp\_:**_ dEBRUYNE: нам нужно быть более конкретными, когда речь идет про удаление части функционала  
> _**rehrar:**_ пострадает в конечном счете некто иной как пользователь  
> _**sgp\_:**_ Существует два предложения GUI:  
> _**sgp\_:**_ 1. Спрячьте его на экране отправки с помощью дополнительной настройки  
> _**sgp\_:**_ 2. Скрыть его полностью на экране отправки  
> _**rbrunner:**_ Каковы аргументы в пользу 2 пункта?  
> _**rehrar:**_ Оба варианта плохие, но 1 лучше, чем 2  
> _**learninandlurkin:**_ Ну, если кого-то и нужно заставить «страдать», это биржи и прочие сервисы. И я не вижу способа заставить их «страдать», кроме как постоянные жалобы своих клиентов на то, что им нужно обновиться и возобновить полноценную работу  
> _**jtgrassie:**_ ^  
> _**sgp\_:**_ CLI имеет нечто подобное, когда пользователям необходимо установить режим передачи идентификатора оплаты вручную  
> _**rehrar:**_ Да, это будет означать полное отключение идентификаторов  
> _**jtgrassie:**_ именно так  
> _**rbrunner:**_ соглашусь с rerahr  
> _**endogenic:**_ обеспечены ли биржи четкими и достаточными техническими планами обновления?  
> _**dEBRUYNE:**_ <rehrar>, оба варианта плохие, но 1 лучше, чем 2 <= я бы не назвал первый вариант плохим. Мы владеем информацией, как это будет выглядеть?  
> _**dEBRUYNE:**_ в нем будет указан «Идентификатор платежа», и пользователь должен нажать на +, чтобы расширить поле  
> _**sgp\_:**_ endogenic: да, по электронной почте. Дополнительно будет пост в блоге, он содержит ту же информацию, что и рассылалась по электронной почте  
> _**pigeons:**_ пользователи часто используют кошельки, которые не поддерживают подадреса  
> _**endogenic:**_ хорошо  
> _**rehrar:**_ Кроме того, следует отметить, что график обновления бирж - сентябрь, а не октябрь, когда уже наступит плановое обновление сети  
> _**rbrunner:**_ Какие это кошельки?  
> _**dsc\_:**_ Rehrar: Я не понимаю, почему вариант 1. вызывает какие-либо проблемы / путаницы  
> _**pigeons:**_ я думаю, что это не имеет большого значения, если перевод идёт с основного адреса пользователя  
> _**rehrar:**_ сентябрь - это время, когда новые версии будут выходить уже без идентификатора платежа в пользовательском интерфейсе  
> _**sgp\_:**_ противопоставление и альтернатива, это всегда хорошо. Мы все еще можем назвать это устаревшим в техническом плане, наподобие оптической связи, в которой мы все нуждаемся для отказа от старых технологий  
> _**learninandlurkin:**_ LOL! Пользователи бирж довольно часто просто используют другие биржи. Никаких кошельков.  
> _**rehrar:**_ dsc\_, dEBRUYNE, хорошо, тогда я полагаюсь на ваше мнение  
> _**pigeons:**_ rbrunner: я думал, что mymonero  
> _**rbrunner:**_ Ok  
> _**endogenic:**_ pigeons: rbrunner, да, получение на такие адреса еще не поддерживается  
> _**endogenic:**_ хотя отправка на них была возможна  
> _**pigeons:**_ и да, как говорится в «learnandlurkin», они просто переходят в другие системы обмена, которые еще не поддерживают подадреса.  
> _**rbrunner:**_ Я действительно не могу придумать ни одного хорошего аргумента для пункта 2  
> _**dEBRUYNE:**_ endogenic: кажется, что это не такая большая проблема. Обменники, как правило, поддерживают снятие как с подадресов, так и с простых адресов (особенно, если мы собираемся заставить их использовать подадреса)  
> _**dEBRUYNE:**_ Для переводов на MyMonero это работает правильно, если пользователь отправляет субадрес  
> _**sgp\_:**_ На самом деле второе решение уже было объединено: https://github.com/monero-project/monero-gui/pull/1866  
> _**rbrunner:**_ Может быть, мне не хватает времени, что бы проверить это :)  
> _**learninandlurkin:**_ Важно что-то сделать в предверии, чтобы оправдать наличие большой красной отметки «УСТАРЕЛО В АПРЕЛЕ»  
> _**sgp\_:**_ Это было для пункта 1: https://github.com/monero-project/monero-gui/pull/1855  
> _**rehrar:**_ Ну что же, рабочая группа Monero начнет наводить шум везде где только можно, на всех сервисах, где нас будут слушать. Попробуйте попасть на эти мусорно-информационные сайты тоже.  
> _**rehrar:**_ Так что все будут знать, что они устарели в апреле, а полностью отменены в сентябре  
> _**rbrunner:**_ Как вариант для решения, под первым пунктом напишите «Идентификатор платежа (необязательно, не рекомендуется)» или аналогичную приписку  
> _**dsc\_:**_ rbrunner: отметил для себя  
> _**sgp\_:**_ rehrar: наверно, дождемся поста в блоге, но это займет несколько дней  
> _**learninandlurkin:**_ Может быть, пост на Reddit будет полезнее?  
> _**learninandlurkin:**_ В дополнении к сообщению в блоге  
> _**learninandlurkin:**_ Если люди так сильно волнуются по поводу хэшрейта сети  
> _**rbrunner:**_ или про терабайтный блокчейн :)  
> _**sarang:**_ «вздох»  
> _**sarang:**_ Есть вопросы к MRL?  
> _**moneromooo:**_ Проверяет ли кто-то изменения размера блока от ArticMine на странное поведение и прочие болячки?  
> _**rbrunner:**_ Как будет работать такое тестирование? Приватный блокчейн?  
> _**sarang:**_ Я жду информацию о стоимости от ArticMine, чтобы завершить модель полностью  
> _**rbrunner:**_ или просто симуляция?  
> _**moneromooo:**_ Кроме того, smoth предложил среднее, а не медиану для 100000 блоков. Было бы намного лучше, если бы это не ухудшило текущую ситуацию  
> _**sarang:**_ Вы имеете в виду в вычислительном отношении или как?  
> _**moneromooo:**_ Лучше? Непременно  
> _**oneiric\_:**_ для среднего значения сортировка не требуется  
> _**sarang:**_ Я добавлю для этого отдельную симуляцию  
> _**moneromooo:**_ Ну, это просто лучше. «Forger the much»  
> _**sarang:**_ «Forger the Much» звучит как имя персонажа из Властелина колец  
> _**moneromooo:**_ :)  
> _**dEBRUYNE:**_ Предлагаю закрыть обсуждение идентификатора платежа, по сути, мы согласны с тем, что мы не должны усложнять пользователю его жизнь (до тех пор, пока не будет выпущено 0.15).  
> _**dEBRUYNE:**_ ?  
> _**moneromooo:**_ Ну, не знаю... Я действительно усложнил задачу для рядового пользователя  
> _**rbrunner:**_ В CLI несколько другая история  
> _**rbrunner:**_ чем в GUI  
> _**rbrunner:**_ Люди там привыкли жонглировать опциями и параметрами  
> _**sgp\_:**_ rehrar: Я рекомендую открыть еще один PR, чтобы отменить 1866, и мы можем собрать отзывы там  
> _**rbrunner:**_ Звучит неплохо  
> _**rehrar:**_ Чуваки, если я сейчас устрою стриминг через Jitsi, чтобы показать новый FFS в действии, вам будет интересно посмотреть его?  
> _**sarang:**_ Я бы посмотрел, если встреча будет официально закрыта  
> _**jtgrassie:**_ конечно  
> _**sgp\_:**_ да, я могу начать пока один и записать всё  
> _**rehrar:**_ Через 15 минут я буду готов  
> _**rehrar:**_ Я дам знать, будьте готовы  
> _**sgp\_:**_ У меня вопрос по tx_extra, если больше не о чем поговорить  
> _**sgp\_:**_ Люди говорят, что вы можете помещать туда произвольные данные в любом формате, который хотите, если вы готовы за это платить. Тем не менее вам всё еще нужно добыть транзакцию для ее включения. Я не думал, что узлы будут блокировать транзакции с произвольными данными tx_extra  
> _**moneromooo:**_ Он будет в узле txpool, когда вы передадите его. Кошелек может увидеть это до того, как его добыли  
> _**sgp\_:**_ moneromooo: будет ли он разгадан?  
> _**sgp\_:**_ другими  
> _**moneromooo:**_ Действительно?  
> _**sgp\_:**_ предположим, что это действительно  
> _**moneromooo:**_ У него достаточно высокая комиссия?  
> _**sgp\_:**_ предположим, что да  
> _**sgp\_:**_ Я столкнулся с противоречивой информацией: https://monero.stackexchange.com/a/3627/42  
> _**moneromooo:**_ Тогда, вероятно, да  
> _**rbrunner:**_ Когда-то у меня была идея поместить туда "мои" MMS-сообщения, я посмотрел на код и не нашел больших блоков для данных tx_extra  
> _**moneromooo:**_ Этот ответ выглядит неправильным  
> _**jtgrassie:**_ Это неправильно  
> _**sgp\_:**_ Если он будет разгадан, то это соответствует моему предположению. Кажется, есть заблуждение, что люди не будут видеть мои сделки с произвольными tx_extra.  
> _**moneromooo:**_ И, пожалуйста, не спамьте и не помещайте в него отпечатки пальцев. Это для «полезных» данных  
> _**rbrunner:**_ Я не думаю, что какой-либо кошелек в настоящее время показывает это  
> _**jtgrassie:**_ это так  
> _**jtgrassie:**_ я думаю  
> _**rbrunner:**_ Да, конечно :)  
> _**sgp\_:**_ Отлично, это разумный ответ на мой вопрос ;)  

_[Ссылка на предыдущую встречу](https://xmr.ru/threads/760/) группы разработчиков Monero от 2018-12-16_  

---
_Источник: [Monero DevMeeting 2019-01-28](https://www.reddit.com/r/Monero/comments/akmf5q/logs_of_yesterdays_dev_meeting/)_________________  
Перевод:  [Unholy](https://xmr.ru/members/754/)    
Редактирование_:  [Mr. Pickles](https://xmr.ru/members/50/) (@v1docq47)  
Коррекция:  [Kukima](https://xmr.ru/members/138/)_