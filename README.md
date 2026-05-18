Вот готовый `README.md` для проекта `MyProject`:

```markdown
# MyProject – Git Merge в Visual Studio и командной строке

Демонстрационный проект для отработки навыков работы с Git: инициализация локального репозитория, создание веток, слияние изменений и работа через интерфейс Visual Studio.

## Задача

1. Инициализировать локальный репозиторий в папке `MyProject`
2. Добавить файл `Program.cs` и закоммитить его в `main`
3. Создать ветку `feature` и внести изменения в `Program.cs`
4. Выполнить слияние ветки `feature` в `main`
5. Проверить результат слияния

## Исходные данные

- **Папка проекта:** `MyProject`
- **Тип проекта:** Console App (.NET Core)
- **Файл:** `Program.cs`
- **Начальное содержимое:** `Console.WriteLine("Hello, World!");`
- **Изменение в feature:** `Console.WriteLine("Hello, Feature!");`

## Структура проекта

```
MyProject/
├── .git/
├── Program.cs
├── MyProject.csproj
└── README.md
```

---

## Решение через командную строку

### 1. Инициализация репозитория и первый коммит

```bash
cd MyProject
git init
git add Program.cs
git commit -m "Initial commit with Program.cs"
```

### 2. Создание ветки `feature` и внесение изменений

```bash
git checkout -b feature
echo 'Console.WriteLine("Hello, Feature!");' > Program.cs
git add Program.cs
git commit -m "Update greeting to Feature version"
```

### 3. Слияние ветки `feature` в `main`

```bash
git checkout main
git merge feature -m "Merge feature branch into main"
```

### 4. Проверка результата

```bash
git log --oneline --graph
cat Program.cs
# Вывод: Console.WriteLine("Hello, Feature!");
```

---

## Решение через Visual Studio (пошагово)

### Шаг 1. Создать локальный репозиторий

1. Открыть Visual Studio
2. `Файл → Создать → Проект`
3. Выбрать шаблон **Console App (.NET Core)** (или **Console App (.NET Framework)** в зависимости от версии)
4. Имя проекта: `MyProject`
5. Нажать **Создать**
6. После создания проекта: `Git → Создать репозиторий Git`
7. Выбрать **Только локальный** → **Создать**

### Шаг 2. Добавить файл `Program.cs` и сделать коммит

1. Открыть `Program.cs` (создан автоматически шаблоном)
2. Убедиться, что код содержит:
   ```csharp
   Console.WriteLine("Hello, World!");
   ```
3. Открыть окно **Git Changes** (`Вид → Git Changes`)
4. В поле сообщения ввести: `Initial commit with Program.cs`
5. Нажать **Commit All**

### Шаг 3. Создать ветку `feature`

1. В окне **Git Changes** справа вверху нажать на выпадающий список веток (отображается `main`)
2. Выбрать **New Branch**
3. Ввести имя: `feature`
4. Нажать **Create Branch** (произойдёт автоматическое переключение на новую ветку)

### Шаг 4. Изменить `Program.cs` в ветке `feature`

1. В редакторе изменить строку на:
   ```csharp
   Console.WriteLine("Hello, Feature!");
   ```
2. Сохранить файл (`Ctrl+S`)
3. В окне **Git Changes** отобразятся изменения
4. В поле сообщения ввести: `Update greeting to Feature version`
5. Нажать **Commit All**

### Шаг 5. Переключиться на `main` и выполнить слияние

1. В выпадающем списке веток выбрать **main**
2. Нажать **Switch** (подтвердить переключение)
3. В окне **Git Changes** нажать кнопку **Merge** (или в меню `Git → Слияние ветвей`)
4. Выбрать ветку **feature** → нажать **Merge**
5. Слияние выполнится (без конфликтов, так как `main` не изменялся после ответвления)

### Шаг 6. Проверить результат

1. Открыть `Program.cs` — содержимое должно быть:
   ```csharp
   Console.WriteLine("Hello, Feature!");
   ```
2. Открыть окно **Git Repository** (`Git → Manage Branches` или `Ctrl+0, Ctrl+R`)
3. Убедиться, что ветка `main` содержит коммит слияния

---

## Ожидаемый результат

### Граф коммитов

```
*   abc1234 (HEAD -> main) Merge feature branch into main
|\
| * def5678 (feature) Update greeting to Feature version
* | ghi9012 Initial commit with Program.cs
```

### Содержимое `Program.cs` в `main`

```csharp
Console.WriteLine("Hello, Feature!");
```

### Содержимое `Program.cs` в `feature` (без изменений)

```csharp
Console.WriteLine("Hello, Feature!");
```

---

## Финальная проверка через Visual Studio

| Действие | Ожидаемый результат |
|----------|---------------------|
| `Git → Manage Branches` → двойной клик на `main` | Файл `Program.cs` содержит `Hello, Feature!` |
| `Git → Manage Branches` → двойной клик на `feature` | Файл `Program.cs` содержит `Hello, Feature!` |
| `git log --oneline --graph` в терминале | История показывает merge-коммит |

✅ Все операции выполнены **только локально**, без удалённого репозитория.

---

## Критерии оценки и их выполнение

| Критерий | Статус | Способ проверки |
|----------|--------|-----------------|
| Корректная инициализация репозитория | ✅ | `git init` или через VS: `Git → Создать репозиторий Git` |
| Добавление и коммит `Program.cs` | ✅ | Коммит `Initial commit with Program.cs` в `main` |
| Создание ветки `feature` и изменение файла | ✅ | Ветка `feature`, коммит с `Hello, Feature!` |
| Успешное слияние | ✅ | `git merge feature` в `main` без конфликтов |
| Проверка результата в `main` | ✅ | `Program.cs` содержит `Console.WriteLine("Hello, Feature!");` |

---

## Полезные команды Git (шпаргалка)

| Команда | Описание |
|---------|----------|
| `git init` | Инициализация нового репозитория |
| `git add <файл>` | Добавление файла в staging-область |
| `git commit -m "..."` | Фиксация изменений с сообщением |
| `git checkout -b <ветка>` | Создание и переключение на новую ветку |
| `git checkout <ветка>` | Переключение на существующую ветку |
| `git merge <ветка>` | Слияние указанной ветки в текущую |
| `git log --oneline --graph` | Просмотр истории коммитов в компактном виде |
| `cat <файл>` | Просмотр содержимого файла |

---

## Примечания

- **Fast-forward vs merge commit:** В данном примере слияние создаёт отдельный merge-коммит, так как используется `git merge` без флага `--ff-only`. Если бы изменения в `main` не происходили после создания `feature`, Git по умолчанию мог бы выполнить fast-forward слияние (без дополнительного коммита).
- **Visual Studio vs командная строка:** Все операции можно выполнять как через графический интерфейс Visual Studio, так и через встроенный терминал (`Вид → Терминал`).
- **Конфликты:** В данном сценарии конфликтов не возникает, так как `main` не изменялся после создания ветки `feature`.
```

Сохраните этот текст как `README.md` в корне папки `MyProject`. При необходимости закоммитьте его:

```bash
git add README.md
git commit -m "Add README.md with project documentation"
```
