# SANSЛ - документ экранов приложения beta

Источник: founder-анкета 2026-06-15 и продуктовая редакция 2026-06-16.

Назначение: полный рабочий документ по экранам beta. Для каждого экрана указано, зачем он нужен, что на нем есть, как расположено и куда ведет flow.

## 1. Общая модель

Главная поверхность beta - чат с Сансом. Карта и Древо прогресса - визуальные якоря. Нижнего tab bar нет: основная навигация открывается выезжающим меню слева.

Базовые корневые разделы:

- Чат;
- Сегодня;
- Карта;
- Квесты;
- Память;
- Артефакты;
- Шаблоны;
- Планирование;
- Развилки;
- Профиль.

Правило "Назад": возвращать на предыдущий экран. Если стек недоступен - вернуть на корень текущего раздела.

Пользовательская копия: светская, практичная, без терапевтических, психологических и эзотерических claims. Санс не дает один "правильный" ответ в личных выборах, а показывает варианты и объясняет логику.

## 2. Главный flow beta

```text
Splash
  -> 18+ / Terms / Privacy
  -> AI-disclosure
  -> Swipe onboarding
  -> First summary
  -> Chat home
  -> 3 quest options
  -> Quest detail
  -> Proof setup
  -> Quest completion
  -> Artifact
  -> Map / Tree / Today
```

Возвратный flow:

```text
Push / cue / open app
  -> Chat or Today
  -> Continue route / pick quest / update map
  -> Complete action
  -> Artifact
  -> Memory and progress update
```

## 3. Экранная карта

### 0. Splash / загрузка бренда

Для чего: первый визуальный контакт и загрузка приложения.

Что есть:

- логотип / куб SANSЛ;
- слоган "Играй в свою жизнь";
- короткая анимация появления;
- fallback без motion.

Расположение:

- логотип по центру;
- слоган под логотипом;
- нижняя зона свободна, без лишней информации.

Flow:

- первый запуск -> экран 1;
- повторный запуск с активной сессией -> экран 5 или последний активный экран;
- ошибка сети -> системное состояние Offline.

### 1. 18+ / Terms / Privacy gate

Для чего: обязательный возрастной и юридический вход.

Что есть:

- текст "SANSЛ - приложение для взрослых 18+";
- ссылки Terms и Privacy;
- чекбокс согласия;
- кнопка "Продолжить";
- ссылка "Не согласен" / выход.

Расположение:

- заголовок сверху;
- короткий текст под ним;
- чекбоксы в нижней половине;
- CTA внизу, sticky на mobile.

Flow:

- согласие -> экран 2;
- отказ -> выход / закрытие onboarding.

### 2. AI-disclosure

Для чего: объяснить, что пользователь общается с AI и что решение остается за пользователем.

Что есть:

- короткий текст: "Вы общаетесь с AI. Он помогает структурировать выбор, но не принимает решений за вас.";
- ссылка "Как это работает";
- кнопка "Понятно".

Расположение:

- компактная карточка в центре;
- иллюстрация не обязательна;
- без медицинских или терапевтических claims.

Flow:

- "Понятно" -> экран 3;
- "Как это работает" -> help sheet -> назад к экрану 2.

### 3. Swipe onboarding

Для чего: быстро собрать стартовые настройки без ощущения психологической анкеты.

Что есть:

- одна карточка с утверждением;
- свайп вправо - "Да";
- свайп влево - "Нет";
- кнопки "Да" и "Нет" для accessibility;
- progress indicator;
- "Пропустить" вверху справа;
- пояснение, что это можно изменить позже.

Расположение:

- карточка занимает центр экрана;
- progress сверху;
- кнопки снизу;
- свайп-анимация мягкая, без gamified pressure.

Flow:

- завершение всех карточек -> экран 4;
- пропуск -> экран 4 с нейтральным summary;
- назад -> экран 2.

Стартовые карточки описаны в `sansl-product-spec.md`.

### 4. First summary

Для чего: дать первую ценность и объяснить, как ответы повлияли на старт.

Что есть:

- summary: "Это не характеристика личности и не оценка - только стартовая настройка.";
- 2-3 строки о выбранном фокусе;
- 3 кнопки: "Быстрый квест", "Средний квест", "Разобрать в чате";
- ссылка "Изменить ответы".

Расположение:

- summary сверху;
- 3 варианта как крупные кнопки-карточки;
- secondary links внизу.

Flow:

- "Быстрый квест" / "Средний квест" -> экран 10;
- "Разобрать в чате" -> экран 5;
- "Изменить ответы" -> экран 3.

### 5. Chat home / Санс

Для чего: главный рабочий экран beta.

Что есть:

- top bar: меню слева, название "Санс", incognito toggle, settings/context icon;
- visible AI-disclosure compact state;
- chat history;
- suggested reply bubbles;
- composer;
- voice message button;
- attach/context button only if allowed;
- "Почему эти варианты?" inside AI responses;
- text selection action "Спросить Санса об этом".

Расположение:

- header fixed;
- chat scroll area center;
- suggested bubbles above composer;
- composer fixed bottom;
- incognito state clearly visible when enabled.

Flow:

- menu -> экран 7;
- user asks -> answer with options on same screen;
- AI suggests 3 quest options -> экран 6;
- select quest -> экран 10;
- incognito -> same screen with memory-disabled indicator;
- highlight text -> contextual action sheet.

### 6. Three options / "3 двери"

Для чего: не давать один "правильный" ответ, а показывать выбор.

Что есть:

- три варианта;
- short rationale;
- button "Почему эти?";
- "Попросить еще варианты";
- "Сохранить как развилку";
- "Сделать квестом".

Расположение:

- варианты как stacked cards;
- rationale под каждым;
- общие действия снизу.

Flow:

- "Сделать квестом" -> экран 10;
- "Сохранить как развилку" -> экран 27;
- "Еще варианты" -> stays on screen 5/6.

### 7. Left slide menu

Для чего: корневая навигация вместо bottom tab bar.

Что есть:

- профиль header;
- быстрый плюс;
- разделы: Чат, Сегодня, Карта, Квесты, Память, Артефакты, Шаблоны, Планирование, Развилки, Профиль;
- premium marker для закрытых функций;
- settings shortcut.

Расположение:

- panel slides from left;
- overlay dims content;
- quick plus near top;
- list items large enough for mobile.

Flow:

- select section -> corresponding root screen;
- quick plus -> экран 11 custom quest flow;
- outside tap / swipe left -> closes menu.

### 8. Today / панель виджетов

Для чего: собрать день и показать следующий полезный шаг.

Что есть:

- следующий квест;
- квест дня;
- check-in состояния дня без диагностики;
- вход в карту сферы;
- последний артефакт;
- план;
- память;
- кристаллы;
- premium widget customization controls.

Расположение:

- верх: greeting and next step;
- middle: widget grid;
- lower: plan/artifact/memory cards;
- FAB absent; quick plus lives in side menu.

Flow:

- next quest -> экран 10;
- check-in -> inline card -> updated suggestions;
- map card -> экран 18/19;
- artifact card -> экран 16;
- customize widgets -> экран 32 / premium gate if needed.

### 9. Quest list

Для чего: каталог текущих, рекомендованных, избранных и пользовательских квестов.

Что есть:

- filters: все, сегодня, по сфере, избранное, завершенные;
- cards with title, sphere, duration, difficulty;
- create custom quest entry;
- search.

Расположение:

- filter chips below header;
- cards list;
- create action in top area or left menu quick plus.

Flow:

- quest card -> экран 10;
- create custom -> экран 11;
- favorite filter -> filtered list.

### 10. Quest detail

Для чего: показать квест, действия и способ выполнения.

Что есть:

- название;
- сфера;
- время;
- difficulty: простой / средний / сложный;
- actions checklist;
- "Почему это?" info button;
- buttons: принять, завершить, отложить;
- edit icon before completion;
- favorite;
- duplicate.

Расположение:

- header with sphere;
- actions in center;
- controls bottom;
- "Почему это?" as small icon near title or rationale.

Flow:

- accept -> экран 13;
- edit -> экран 11;
- proof setup missing -> экран 12;
- complete -> экран 14;
- duplicate -> confirmation sheet -> new quest detail.

### 11. Edit / custom quest

Для чего: создать или изменить квест через Санс.

Что есть:

- chat-like editing field;
- current quest draft;
- controls for easier / harder / more interesting;
- preview card;
- save button.

Расположение:

- top: draft summary;
- center: chat/editor;
- bottom: save/cancel.

Flow:

- save -> экран 10;
- cancel -> previous screen;
- ask Sанс -> same screen updates draft.

### 12. Proof setup

Для чего: выбрать способ подтверждения выполнения.

Что есть:

- text: "Как вам удобнее подтверждать выполнение квестов? Это можно поменять в настройках.";
- options: honor, note, checklist, timer, photo opt-in;
- privacy explanation for photo;
- "Продолжить".

Расположение:

- options as vertical cards;
- privacy note under photo option;
- CTA bottom.

Flow:

- choose proof -> экран 13;
- later change -> Settings / Quest detail.

### 13. Quest in progress

Для чего: поддержать выполнение без давления.

Что есть:

- active quest summary;
- actions checklist;
- timer if selected;
- note field if selected;
- "Сделал", "Частично", "Не сделал", "Отложить";
- calm reminder that no penalty exists.

Расположение:

- quest title top;
- checklist center;
- action buttons bottom.

Flow:

- did -> экран 14;
- partly -> screen 14 with partial state;
- did not -> экран 15 reroute sheet;
- postpone -> Today or previous screen.

### 14. Completion

Для чего: закрыть квест and capture result.

Что есть:

- confirmation;
- optional note;
- optional photo proof if selected;
- "Создать артефакт";
- "Сохранить без артефакта".

Расположение:

- confirmation top;
- inputs center;
- controls bottom.

Flow:

- create artifact -> экран 16;
- save without artifact -> Today / Map update;
- edit note -> stays.

### 15. Reroute / not done

Для чего: обработать "не сделал" без стыда.

Что есть:

- text: "Расскажите, что не подошло или оказалось сложным";
- options: сделать легче, перенести, заменить, пауза;
- free text optional.

Расположение:

- bottom sheet or modal;
- options as buttons;
- free text lower.

Flow:

- easier -> экран 11 with easier draft;
- postpone -> Planning;
- replace -> экран 6 / recommendations;
- pause -> route state updated.

### 16. Artifact ceremony

Для чего: отметить результат действия.

Что есть:

- artifact card;
- type: действие / наблюдение / вывод;
- link to source action;
- short generated summary editable by user;
- sound/haptic if enabled;
- save to memory;
- share later/manual only.

Расположение:

- card center;
- animation behind or around card;
- actions bottom.

Flow:

- save -> экран 17;
- edit summary -> inline editor;
- open map impact -> экран 18/21;
- close -> Today.

### 17. Artifact detail

Для чего: просмотреть сохраненный результат.

Что есть:

- title/date;
- source quest;
- summary;
- image if generated and permitted;
- linked sphere/route;
- delete/hide controls;
- share card manually.

Расположение:

- artifact visual top;
- text and source below;
- controls in overflow menu.

Flow:

- source quest -> экран 10;
- map link -> экран 19;
- delete/hide -> confirmation.

### 18. Map overview - card view

Для чего: простая версия карты для beta.

Что есть:

- sphere cards;
- status: in focus / paused;
- recent actions;
- entry to route/arc;
- progress markers.

Расположение:

- cards grid/list;
- featured sphere top;
- filters by active/paused.

Flow:

- sphere card -> экран 20;
- switch to graph -> экран 19;
- edit context -> экран 20.

### 19. Map overview - graph view

Для чего: расширенная визуальная карта с узлами-сферами.

Что есть:

- nodes for spheres;
- route links;
- visual progress;
- zoom/pan controls;
- reduced motion fallback.

Расположение:

- graph full-screen;
- left or top controls;
- detail drawer on node tap.

Flow:

- tap node -> экран 20;
- route edge -> экран 21;
- back -> previous map view.

### 20. Sphere detail

Для чего: показать контекст сферы и дать пользователю его редактировать.

Что есть:

- sphere name;
- visible context used by Sанс;
- roles;
- current routes;
- recent artifacts;
- edit context;
- privacy/source controls.

Расположение:

- header with sphere;
- context card;
- routes list;
- artifacts list.

Flow:

- edit context -> inline editor;
- route -> экран 21;
- artifact -> экран 17;
- privacy/source -> экран 31.

### 21. Route / arc detail

Для чего: показать маршрут, арку и квесты внутри.

Что есть:

- route title;
- arc timeline;
- current quest;
- completed actions;
- pause/archive controls;
- suggested next quest.

Расположение:

- route header;
- timeline center;
- next action bottom card.

Flow:

- current quest -> экран 10;
- pause -> confirmation;
- suggested next -> экран 10;
- completed artifact -> экран 17.

### 22. Tree / progress graph

Для чего: визуально показать рост от реальных действий.

Что есть:

- seed/tree state;
- branches by spheres or skills;
- action markers;
- explanation "рост только от подтвержденных действий";
- no person rating.

Расположение:

- tree/graph center;
- branch labels around;
- detail drawer on tap.

Flow:

- branch -> sphere detail;
- marker -> artifact detail;
- info -> explanation sheet.

### 23. Memory home

Для чего: управлять сохраненными чатами, дневниками and artifacts.

Что есть:

- tabs: чаты, дневники, артефакты, недельные итоги;
- source labels;
- delete/hide controls;
- incognito explanation;
- search.

Расположение:

- tabs top;
- list content center;
- privacy shortcut bottom/top.

Flow:

- diary -> экран 24;
- weekly portrait -> экран 25;
- chat archive -> detail view;
- delete -> confirmation.

### 24. Diaries: past / present / future

Для чего: дать структурированные дневники without therapy framing.

Что есть:

- three sections: прошлое, настоящее, будущее;
- entries from chats and user edits;
- source chips;
- edit/delete;
- "Сохранить только для себя" controls.

Расположение:

- segmented control top;
- entries list;
- compose/edit area.

Flow:

- entry -> detail;
- edit -> inline editor;
- source -> linked chat/quest/artifact.

### 25. Weekly portrait

Для чего: недельный итог без оценки личности.

Что есть:

- summary of actions;
- routes touched;
- artifacts created;
- "что сработало";
- "что можно попробовать дальше";
- edit summary;
- source chips.

Расположение:

- week header;
- stats cards;
- prose summary;
- next options.

Flow:

- choose next option -> экран 10 or 6;
- edit -> editor;
- source chip -> source screen.

### 26. Planning / cue / calendar

Для чего: управлять планами and reminders.

Что есть:

- planned quests;
- cue list;
- notification cap;
- quiet hours;
- calendar connection state;
- permission request only in context.

Расположение:

- today's plan top;
- cue cards list;
- settings at bottom.

Flow:

- add cue -> cue setup sheet;
- connect calendar -> permission explainer -> OS permission;
- planned quest -> экран 10.

### 27. Decision fork

Для чего: сохранить развилку выбора and compare options.

Что есть:

- question;
- 3+ options;
- rationale per option;
- "что проверить";
- "сделать квестом";
- "сохранить в карту".

Расположение:

- question top;
- option cards center;
- actions bottom.

Flow:

- option -> quest creation;
- save -> memory/map;
- ask Sанс -> chat.

### 28. Templates

Для чего: дать reusable quest/route templates.

Что есть:

- private templates;
- curated templates;
- create own template;
- premium marker for customization;
- no public templates in beta.

Расположение:

- categories top;
- template cards;
- create action.

Flow:

- template -> preview;
- use -> quest/route creation;
- share public unavailable -> waitlist/explainer if needed.

### 29. Search / web helper

Для чего: отдельный utility chat/search mode, если включен продуктово.

Что есть:

- clear mode label;
- web/source disclosure;
- source links;
- cost/limit state if relevant;
- no secret or private memory sent without consent.

Расположение:

- chat layout;
- sources below answer;
- mode badge in header.

Flow:

- ask -> answer with sources;
- save to memory -> explicit confirmation;
- back -> Chat.

Риск: требует отдельной cost, privacy and source-quality спеки.

### 30. Profile

Для чего: аккаунт, подписка, настройки and help.

Что есть:

- user account state;
- subscription;
- privacy;
- incognito settings;
- notifications;
- sound/haptics/accessibility;
- help and safety;
- support.

Расположение:

- sections list;
- critical actions separated visually;
- no hidden cancellation.

Flow:

- subscription -> экран 33;
- privacy -> экран 31;
- accessibility -> экран 32;
- help -> экран 34.

### 31. Trust center / privacy

Для чего: показать and control data use.

Что есть:

- what is saved;
- sources used for recommendations;
- memory consent;
- analytics consent;
- model improvement consent;
- calendar/photo/push/mic permissions;
- delete source;
- delete data;
- incognito explanation.

Расположение:

- grouped sections;
- toggles with explanations;
- destructive actions separated and confirmed.

Flow:

- change consent -> confirmation if impact is meaningful;
- delete source -> confirmation -> state update;
- delete data -> deletion flow.

### 32. Settings: sound, haptics, accessibility, game level

Для чего: let user reduce stimulation and game layer.

Что есть:

- game level: мало / средне / много;
- reduced motion;
- sound off;
- haptics off;
- high contrast;
- large text;
- quiet mode;
- simple wording;
- no-metaphor mode;
- no-timer mode.

Расположение:

- grouped toggles;
- preview if useful;
- save automatically.

Flow:

- toggles -> immediate effect;
- back -> Profile / previous screen.

### 33. Subscription / paywall / store

Для чего: show plan state and paid options without blocking protected surfaces.

Что есть:

- current plan;
- Standard / Premium comparison;
- AI/generation limits;
- cosmetic store;
- gift subscription;
- cancellation/refund links;
- "never paywall" note for safety/data rights/support.

Расположение:

- current plan top;
- plan cards center;
- store below;
- legal/cancel links clear and accessible.

Flow:

- upgrade -> payment flow only after legal/payment approval;
- cancel -> offboarding/cancellation flow;
- refund/support -> help.

### 34. Help / support

Для чего: give support and product explanations.

Что есть:

- what is SANSЛ;
- how AI works;
- how memory works;
- how to delete data;
- how to cancel subscription;
- how to turn off sound/haptics/notifications;
- support form;
- screenshot upload for bug reports;
- Telegram/support operator flow if available.

Расположение:

- search top;
- topics list;
- support form below or separate route.

Flow:

- topic -> article;
- support form -> submission state;
- safety -> экран 35.

### 35. Safety / human-help overlay

Для чего: handle boundary cases calmly and outside game mechanics.

Что есть:

- direct text;
- external resources;
- trusted contact option if configured;
- "SANSЛ не заменяет живую помощь";
- no animation, no reward, no paywall.

Расположение:

- full-screen overlay;
- resources and actions center;
- close/back policy depends on severity.

Flow:

- triggered from chat/safety/help -> overlay;
- resource selected -> external handoff/log event;
- close -> safe return path.

Тексты require founder/legal review before beta.

### 36. Feedback / bug report

Для чего: collect beta feedback in structured form.

Что есть:

- reason categories: не понял экран, квест не подходит, тон не подходит, слишком много игры, слишком мало игры, не доверяю памяти, хочу удалить/скрыть, баг, другое;
- screenshot attachment;
- free text;
- optional contact consent.

Расположение:

- category chips;
- text field;
- screenshot uploader;
- submit button.

Flow:

- submit -> success state;
- category "delete/hide" -> privacy screen shortcut;
- bug -> support queue.

### 37. Offboarding / cancellation

Для чего: let user leave without dark patterns.

Что есть:

- cancel subscription;
- delete data;
- keep read-only history if subscription expired;
- optional reason;
- less game mode suggestion only once and not blocking;
- support link.

Расположение:

- clear primary action for requested outcome;
- optional alternatives below;
- legal/receipt info as needed.

Flow:

- cancel -> cancellation confirmation;
- delete -> data deletion confirmation;
- reason skip -> finish.

## 4. System states

These are not separate product sections, but every major screen needs designs for:

| State | Purpose | Required UI |
| --- | --- | --- |
| Empty | First-time or no content | Explain what can happen next and offer one action. |
| Loading | AI, map, memory, store, sync | Skeleton or calm spinner; no fake progress. |
| Offline | No network | Show available local content: map, tree, artifacts, settings, safety resources. |
| Incognito | Memory disabled | Persistent label in chat; clear explanation. |
| Paywall | Premium-only action | Explain what is premium; never block safety, support, deletion, cancellation or legal. |
| Error | Failed action | Plain language, retry, support link. |
| Confirmation | Deletion, cancellation, consent changes | Clear impact; no pressure. |
| No access | Permission or plan issue | Explain missing permission/plan and path to fix. |
| Data deleted / hidden | After privacy action | Confirm result and show what remains. |
| Reduced stimulation | Accessibility/less-game | Disable decorative effects and simplify language. |
| Safety | Boundary state | Full-screen, calm, no game effects. |

## 5. First 3 store / landing screenshots

1. Сегодня - dashboard with next quest, check-in and current route.
2. Древо прогресса - growth from confirmed actions, not rating a person.
3. Квесты - example quest with actions, "Почему это?", proof choice and no-pressure completion.

## 6. Copy examples for core screens

AI-disclosure:

> Вы общаетесь с AI. Он помогает структурировать выбор, но не принимает решений за вас.

First summary:

> Я учел ваши ответы. Это не характеристика личности и не оценка - только стартовая настройка SANSЛ.

Quest "why":

> Этот квест связан с выбранной сферой и занимает мало времени. Он нужен, чтобы перейти от обсуждения к одному проверяемому действию.

Not done:

> Расскажите, что не подошло или оказалось сложным. Можно сделать шаг меньше, перенести или выбрать другой вариант.

Incognito:

> История чата не сохраняется в память.

Privacy source:

> Эти данные используются для подсказок. Вы можете отключить источник или удалить его.

Paywall:

> Эта настройка доступна в Premium. Без подписки остаются доступны история, удаление данных, поддержка, отмена и безопасность.
