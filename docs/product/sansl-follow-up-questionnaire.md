# SANSЛ - дополнительный продуктовый опросник

Дата: 2026-06-16.

Назначение: собрать решения, которые остались открытыми после founder-анкеты 2026-06-15. Этот опросник не отменяет принятые founder-решения; он добирает недосказанное, конфликтные зоны и вопросы, которые нельзя безопасно закрыть догадкой.

Формат ответа на каждый вопрос:

- Решение:
- Почему:
- Статус: принято / нужно обсудить / отложить / запретить
- Кто утверждает: founder / cofounder / оба / legal / design / research
- Блокирует: дизайн / разработку / тексты / оплату / legal / не блокирует

## 1. Onboarding и первая ценность

Q1.1. Сколько swipe-карточек допустимо до first summary?

- 6-8.
- 9-12.
- 13-16.
- Адаптивно: остановиться, когда достаточно сигнала.

Q1.2. Какие темы обязательно должны попасть в первый swipe-опрос?

- Работа / проекты.
- Дом / быт.
- Деньги.
- Обучение.
- Творчество.
- Отдых.
- Отношения / коммуникация.
- Фокус / порядок.
- Планирование.
- Другое.

Q1.3. Нужно ли показывать пользователю, какие настройки получились из ответов?

- Да, кратко на first summary.
- Да, отдельным экраном "Стартовые настройки".
- Нет, только использовать внутри продукта.

Q1.4. Можно ли использовать onboarding answers для персонализации после первого запуска?

- Да, пока пользователь не изменил настройки.
- Да, но только как видимый источник в Trust Center.
- Нет, использовать только для первого summary.

## 2. Терминология и язык

Q2.1. Утверждаем ли "Санс" как имя AI-навигатора в UI?

- Да.
- Да, но пользователь может выбрать другое имя.
- Нет, использовать "AI-навигатор".
- Проверить на пользователях.

Q2.2. Убираем ли слово "проводник" из пользовательского UI?

- Да, заменить на "Санс" / "AI-навигатор".
- Оставить только в help center.
- Оставить как брендовый термин.

Q2.3. Как называем "Карту жизни" в UI?

- Карта.
- Карта сфер.
- Карта маршрутов.
- Human Graph.
- Другое.

Q2.4. Как называем tree/growth surface?

- Древо прогресса.
- Граф действий.
- Древо.
- Human Graph.
- Другое.

Q2.5. Оставляем ли слово "инсайт"?

- Да.
- Нет, заменить на "вывод".
- Использовать "наблюдение".
- Разрешить только во внутренних спеках.

## 3. Visual direction

Q3.1. Что значит "Inter Light Glass v1.3" для SANSЛ beta?

- Оставляем типографику и light glass.
- Оставляем только принципы.
- Делаем Sansl-native visual system.
- Делаем 2 направления и выбираем после макетов.

Q3.2. Что именно входит в "кибер-античный + абстрактные переливы"?

- Статуя / античные формы.
- Стекло / куб / кристалл.
- Абстрактные градиенты.
- Карта / граф.
- Минимальный интерфейс без иллюстраций.

Q3.3. Какие визуальные запреты все-таки принимаем?

- Нет визуальной тревожности вне safety.
- Нет rarity-рамок для жизни.
- Нет leaderboard.
- Нет "уровня человека".
- Нет dark patterns.
- Нет красного давления.

Q3.4. Какой уровень игрового слоя по умолчанию?

- Мало.
- Средне.
- Много.
- Адаптивно по настройке onboarding.

## 4. AI tone, prompt admin and QA

Q4.1. Какие стили AI-ответов реально доступны пользователю?

- Спокойный.
- Строгий.
- С юмором.
- Энергичный.
- Без выбора стиля в beta.

Q4.2. Должен ли пользователь видеть процентную смесь стилей?

- Нет, это internal prompt setting.
- Да, в простых настройках.
- Да, но только как "тон общения".

Q4.3. Какие prompt-поверхности оператор может менять в admin?

- System prompt.
- Tone snippets.
- Quest templates.
- Safety refusals.
- Paywall copy.
- Notification copy.
- Только через review process, не напрямую.

Q4.4. Что считается regressions для AI tone?

- Психологические выводы о личности.
- Один "правильный" ответ в личном выборе.
- Давление.
- Shame-copy.
- Медицинский или терапевтический claim.
- Непрозрачное использование памяти.

## 5. Квесты, score and progression

Q5.1. Какой score допустим?

- Score действия, не человека.
- Score маршрута, не личности.
- Score только internal.
- Не использовать score в beta.

Q5.2. Что именно повышает score?

- Подтвержденное действие.
- Завершенный квест.
- Завершенная арка.
- Недельная последовательность без наказания.
- Качественная заметка пользователя.

Q5.3. Какой вес proof modes?

- Honor = полный вес.
- Фото = такой же вес, только больше контекста.
- Заметка = полный вес.
- Timer/checklist = полный вес.
- Все proof modes равны.

Q5.4. Нужны ли избранные и повторяемые квесты в beta?

- Да, оба.
- Только избранные.
- Только повтор.
- Не в beta.

## 6. Кристаллы и внутренняя экономика

Q6.1. Выберите модель заработка кристаллов.

Вариант A - спокойная экономика:

- 10 кристаллов за завершенный квест;
- дневной soft cap 60;
- после cap квесты дают артефакты, но не валюту;
- покупки: 300-900 кристаллов;
- темп: 1-2 покупки в месяц.

Вариант B - balanced:

- простой квест 10, средний 20, сложный 35;
- daily cap 100;
- повторные одинаковые квесты дают меньше;
- покупки: 500-1600 кристаллов;
- темп: 1-2 meaningful покупки в месяц.

Вариант C - premium cosmetic:

- без жесткого daily cap;
- diminishing returns после 3-5 квестов в день;
- premium store шире, но рост не покупается;
- покупки: 400-2500 кристаллов;
- темп зависит от активности.

Q6.2. Продаем ли кристаллы за деньги?

- Нет, продаем только фиксированную косметику напрямую.
- Да, но только fixed cosmetic packs без рандома.
- Не в beta/v1.
- Решить после legal/commercial review.

Q6.3. Какие sinks обязательны в beta?

- Темы.
- Скины.
- Голоса TTS.
- Фоны карты.
- Обложки арок.
- NPC / символы.
- Ничего в beta.

Q6.4. Какие покупки никогда нельзя делать за кристаллы?

- Рост.
- Score.
- Safety.
- Privacy/data rights.
- Доступ к удалению.
- "Лучшие" AI-ответы в safety context.

## 7. AI limits and monetization

Q7.1. Что ограничивает Standard?

- Число AI-сессий.
- Дневной/недельный token budget.
- Длина входного сообщения.
- Генерация изображений.
- Web search.
- Доступ к premium customization.

Q7.2. Что отличается в Premium?

- Больше AI budget.
- Больше генераций.
- Доступ к расширенному магазину.
- Кастомизация виджетов.
- Более длинные memory summaries.
- Приоритетные функции, но не safety.

Q7.3. Как показывать достижение лимита?

- "Лимит обновится завтра. Пока доступны карта, квесты и статичные предложения."
- "Можно докупить пакет генераций."
- "Можно перейти на Premium."
- "Отложить запрос."

Q7.4. Какие данные нужны для расчета AI unit economics?

- Средняя длина сообщения.
- Среднее число сообщений в день.
- Среднее число квестов и генераций.
- Цена модели на input/output tokens.
- Цена TTS/STT.
- Цена image generation.
- Target gross margin by plan.
- Fraud/bot protection threshold.

## 8. Privacy, memory and personalization

Q8.1. Какие источники можно использовать для персонализации без отдельного moment-of-use запроса?

- Onboarding answers.
- Chosen spheres.
- Completed quests.
- Saved artifacts.
- Explicit notes.
- Ничего кроме текущего диалога.

Q8.2. Что требует отдельного moment-of-use согласия?

- Calendar.
- Photo proof.
- Microphone.
- Push.
- Model improvement.
- Analytics.
- External integrations.

Q8.3. Показываем ли пользователю "почему Санс это предлагает" через data sources?

- Да, source chips.
- Да, separate "Почему?" sheet.
- Только по запросу.
- Нет в beta.

Q8.4. Как формулируем границу "помощь, а не слежка"?

- Пользователь видит источники.
- Пользователь может отключить источник.
- Нет скрытых выводов о эмоциях.
- Нет профилей третьих лиц.
- Нет импорта контактов в beta.

Q8.5. Что делать с логами для обучения?

- Не использовать в beta.
- Только opt-in model improvement.
- Только деперсонализированные после legal review.
- Отдельное хранилище и retention policy.

## 9. Safety and support

Q9.1. Кто утверждает safety overlay copy?

- Founder.
- Cofounder.
- Legal.
- Founder + legal.

Q9.2. Какие ресурсы показывать в safety overlay для РФ/СНГ?

- Нужен legal/safety список.
- Только generic "обратитесь за срочной помощью".
- Доверенные контакты пользователя.
- Support/human operator.

Q9.3. Нужно ли логировать safety trigger?

- Да, только event class без текста.
- Да, с redacted context.
- Нет.
- Решить после privacy/security review.

Q9.4. Как обычная поддержка передается оператору?

- Support email.
- Telegram bot.
- In-app form.
- Все варианты.

## 10. Social, Pair and UGC

Q10.1. Что точно входит в Pair mode beta?

- Парные квесты.
- Совместный маршрут.
- Семейный сценарий.
- Только коммерческий add-on future.
- Не запускать до отдельной спеки.

Q10.2. Можно ли делиться артефактами?

- Да, только вручную.
- Да, только image card без private text.
- Да, с текстом после preview.
- Нет в beta.

Q10.3. Какие UGC templates можно создавать?

- Private quest templates.
- Private route templates.
- Share by direct link.
- Public gallery after review.
- No public UGC in beta.

Q10.4. Какие social функции запрещены без модерации?

- DM.
- Public comments.
- Public feed.
- Groups.
- Ratings.
- Stories.

## 11. Platform and release

Q11.1. Реально ли делать Web, iOS and Android одновременно для beta?

- Да, один release train.
- Web first, mobile shell параллельно.
- PWA first, native later.
- iOS/Android after product proof.

Q11.2. Какие mobile-only функции являются beta blockers?

- Push.
- Photo proof.
- Haptics.
- Gestures.
- Widgets.
- Share sheet.
- Voice input.
- None.

Q11.3. Какие permissions нельзя спрашивать в onboarding?

- Push.
- Photo.
- Microphone.
- Calendar.
- Analytics.
- Model improvement.
- Все, кроме required age / terms / privacy.

## 12. Beta research

Q12.1. Какая beta cohort?

- 20-50 target users after questionnaire.
- Paid Early Access.
- Both.
- Closed waitlist only.

Q12.2. Какие решения проверяем на пользователях до freeze?

- Naming.
- First launch.
- Map.
- Quest card.
- Crystal/artifact ceremony.
- Sound/haptics.
- Paywall.
- Privacy explanations.

Q12.3. Какой weekly review cadence?

- Founder/cofounder weekly product decision review.
- P0/P1 separate.
- Research review + decision register.
- Metrics only.

Q12.4. Какие go/no-go кроме "1000 concurrent sessions"?

- First value in 60 seconds.
- No therapy confusion.
- AI-disclosure understood.
- Proof opt-in understood.
- Cancellation/deletion paths found.
- No shame-copy.
- Core flows pass on mobile.
