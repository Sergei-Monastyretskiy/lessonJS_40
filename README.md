# Node.js Async File Utilities

Асинхронні утиліти для роботи з файлами в Node.js з використанням `fs/promises`.

## Опис

Проект містить три асинхронні функції для роботи з файловою системою:

- **writeFileAsync** - асинхронний запис даних у файл
- **readFileAsync** - асинхронне читання вмісту файлу
- **deleteFileAsync** - асинхронне видалення файлу

Усі функції включають детальне логування операцій та обробку помилок.

## Встановлення

```bash
# Клонуйте репозиторій
git clone <repository-url>

# Перейдіть до директорії проекту
cd lessonJS_40
```

## Використання

### Імпорт функцій

```javascript
import { writeFileAsync, readFileAsync, deleteFileAsync } from './main.js';
```

### writeFileAsync(filename, content)

Записує вміст у файл асинхронно.

**Параметри:**
- `filename` (string) - ім'я файлу
- `content` (string) - вміст для запису

**Приклад:**

```javascript
await writeFileAsync('example.txt', 'Привіт, це тестовий файл!');
// Консоль: "Файл успішно записано"
```

### readFileAsync(filename)

Читає вміст файлу асинхронно.

**Параметри:**
- `filename` (string) - ім'я файлу

**Повертає:**
- Promise<string> - вміст файлу

**Приклад:**

```javascript
const content = await readFileAsync('example.txt');
console.log('Прочитаний вміст:', content);
// Консоль: "Файл успішно прочитано: Привіт, це тестовий файл!"
```

### deleteFileAsync(filename)

Видаляє файл асинхронно.

**Параметри:**
- `filename` (string) - ім'я файлу

**Приклад:**

```javascript
await deleteFileAsync('example.txt');
// Консоль: "Файл успішно видалено"
```

## Обробка помилок

Усі функції включають обробку помилок:

- **writeFileAsync** - логує помилки запису
- **readFileAsync** - розпізнає відсутність файлу (ENOENT) та інші помилки
- **deleteFileAsync** - розпізнає відсутність файлу (ENOENT) та інші помилки

**Приклад обробки помилок:**

```javascript
try {
  await readFileAsync('nonexistent.txt');
} catch (error) {
  // Консоль: "Файл не існує: nonexistent.txt"
}
```

## Повний приклад

```javascript
import { writeFileAsync, readFileAsync, deleteFileAsync } from './main.js';

async function demo() {
  try {
    // Записуємо файл
    await writeFileAsync('test.txt', 'Тестовий вміст');
    
    // Читаємо файл
    const content = await readFileAsync('test.txt');
    console.log('Отриманий вміст:', content);
    
    // Видаляємо файл
    await deleteFileAsync('test.txt');
  } catch (error) {
    console.error('Виникла помилка:', error);
  }
}

demo();
```

## Технічні вимоги

- Node.js 14.0.0 або вище (для підтримки ES modules та `fs/promises`)
- Використання ES6+ синтаксису (async/await, import/export)

## Логування

Кожна функція логує свої операції:

| Функція | Успіх | Помилка | Файл не існує |
|---------|-------|---------|---------------|
| writeFileAsync | ✅ Файл успішно записано | ❌ Помилка при записі файлу | - |
| readFileAsync | ✅ Файл успішно прочитано | ❌ Помилка при читанні файлу | ⚠️ Файл не існує |
| deleteFileAsync | ✅ Файл успішно видалено | ❌ Помилка при видаленні файлу | ⚠️ Файл не існує |

## Ліцензія

MIT

## Автор

Hillel JavaScript Course - Lesson 40
