# 🏥 MedAI Hub - Интеллектуальная платформа для здравоохранения

Объединённая платформа, содержащая 6 передовых AI-инструментов для медицины, пациентов, врачей и студентов.

## 🚀 Быстрый старт

### Требования
- Python 3.8+
- Flask 3.0+
- TensorFlow/Keras

### Установка

1. **Клонируйте репозиторий:**
```bash
git clone https://github.com/yourusername/medai-hub.git
cd medai-hub
```

2. **Установите зависимости:**
```bash
pip install -r requirements.txt
```

3. **Запустите приложение:**
```bash
python app.py
```

4. **Откройте в браузере:**
```
http://localhost:5000
```

## 📋 6 Инструментов Платформы

### 1. 💊 Помощник по лекарствам
- **Функция:** Загрузите рецепт, получите объяснение приёма лекарства
- **Технология:** OCR (pytesseract) + NLP для интерпретации
- **Особенность:** Интеграция с Telegram для напоминаний
- **Маршрут:** `/medicine-helper`

**Исходные проекты:**
- [marinp1/medication-reminder](https://github.com/marinp1/medication-reminder)
- [3GAMY181/Patient-Medication-Reminder-Bot](https://github.com/3GAMY181/Patient-Medication-Reminder-Bot-End-to-End-n8n-Automation-)

### 2. 👨‍⚕️ Навигатор врачей
- **Функция:** Опишите симптомы → узнайте, к какому врачу идти
- **Технология:** NLP для анализа симптомов, логика классификации
- **Особенность:** Интеллектуальное сопоставление с медицинскими специальностями
- **Маршрут:** `/doctor-navigator`

**Источник:** Custom разработка на основе медицинской таксономии

### 3. 🎤 Голосовой ассистент врача
- **Функция:** Запишите консультацию → ИИ заполнит карту пациента
- **Технология:** Speech-to-Text (OpenAI Whisper) + NLP для извлечения данных
- **Особенность:** Автоматическое создание медицинских документов
- **Маршрут:** `/doctor-assistant`

**Исходные проекты:**
- [drankush/VoxRad](https://github.com/drankush/VoxRad)
- [markbekhit/RadSpeed](https://github.com/markbekhit/RadSpeed)

### 4. 🎓 Тренажёр для студентов-медиков
- **Функция:** Практикуйтесь с ИИ-пациентом, задавайте вопросы, ставьте диагнозы
- **Технология:** Conversational AI + медицинская база знаний
- **Особенность:** Интерактивное обучение с обратной связью
- **Маршрут:** `/student-trainer`

**Источник:** Custom разработка с использованием GPT-подобных моделей

### 5. 🖼️ Анализ медицинских снимков
- **Функция:** Загрузите рентген/МРТ → получите анализ переломов
- **Технология:** DenseNet121 + MONAI (Medical Open Network for AI)
- **Точность:** ~80% на тестовом наборе
- **Особенность:** Визуализация результатов, генерация отчётов
- **Маршрут:** `/medical-imaging`

**Исходные проекты:**
- [NimilPGopal/Automated-Bone-Fracture-Detection](https://github.com/NimilPGopal/Automated-Bone-Fracture-Detection)
- [chaitanya6512/Automated-Bone-Fracture-Detection](https://github.com/chaitanya6512/Automated-Bone-Fracture-Detection)

### 6. 🔬 Детектор рака кожи
- **Функция:** Загрузите фото кожи → анализ опасности образования
- **Технология:** ResNet50 (Transfer Learning) + TensorFlow/Keras
- **Особенность:** Классификация на "Опасное" vs "Безопасное"
- **Маршрут:** `/skin-cancer-detector`

**Исходный проект:**
- [dipanshu-2106/Skin-cancer-detector](https://github.com/dipanshu-2106/Skin-cancer-detector)

## 📁 Структура проекта

```
medai-hub/
├── app.py                  # Flask приложение (главный сервер)
├── requirements.txt        # Python зависимости
├── README.md              # Этот файл
├── templates/             # HTML шаблоны
│   ├── index.html                    # Главная страница
│   ├── medicine-helper.html          # Помощник по лекарствам
│   ├── doctor-navigator.html         # Навигатор врачей
│   ├── doctor-assistant.html         # Голосовой ассистент
│   ├── student-trainer.html          # Тренажёр студентов
│   ├── medical-imaging.html          # Анализ снимков
│   ├── skin-cancer-detector.html     # Детектор рака кожи
│   ├── 404.html                      # Страница 404
│   └── 500.html                      # Страница 500
├── static/                # Статические файлы
│   ├── style.css         # CSS стили
│   └── script.js         # JavaScript
└── uploads/              # Папка для загруженных файлов
```

## 🔌 API Endpoints

| Endpoint | Метод | Функция |
|----------|-------|---------|
| `/` | GET | Главная страница |
| `/medicine-helper` | GET | Помощник по лекарствам |
| `/api/analyze-medicine` | POST | Анализ рецепта |
| `/doctor-navigator` | GET | Навигатор врачей |
| `/api/find-doctor` | POST | Поиск врача по симптомам |
| `/doctor-assistant` | GET | Голосовой ассистент |
| `/api/transcribe` | POST | Транскрибирование аудио |
| `/student-trainer` | GET | Тренажёр студентов |
| `/api/ai-patient` | POST | Ответ ИИ-пациента |
| `/medical-imaging` | GET | Анализ медснимков |
| `/api/analyze-xray` | POST | Анализ рентгена |
| `/skin-cancer-detector` | GET | Детектор рака кожи |
| `/api/detect-skin-cancer` | POST | Анализ кожи |

## 🛠️ Развёртывание

### Локально (разработка)
```bash
python app.py  # Запуск на http://localhost:5000
```

### На сервер (production)
```bash
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

### Docker
```bash
docker build -t medai-hub .
docker run -p 5000:5000 medai-hub
```

## ⚠️ Важно

1. **Это не медицинский диагноз!** Все результаты являются только информационными.
2. **Всегда консультируйтесь с врачом** перед принятием медицинских решений.
3. **Конфиденциальность:** Защита данных пациентов соответствует HIPAA/GDPR.

## 📊 Технологический стек

- **Backend:** Flask (Python)
- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **ML/AI:**
  - TensorFlow/Keras (для DenseNet121, ResNet50)
  - MONAI (Medical Imaging)
  - OpenAI Whisper (Speech-to-Text)
  - spaCy/NLTK (NLP)
- **Database:** SQLite (опционально для логирования)
- **API:** Flask RESTful

## 🎯 Особенности

✅ **6 интегрированных инструментов**
✅ **Современный UI с темной/светлой темой**
✅ **Мобильный дизайн (responsive)**
✅ **API для интеграции с другими системами**
✅ **Обработка изображений и аудио**
✅ **Интеграция Telegram для напоминаний**

## 🔐 Безопасность

- Валидация всех входных данных
- Защита от CSRF атак
- Ограничение размера загружаемых файлов
- Логирование всех операций
- Шифрование чувствительных данных

## 📝 Лицензия

MIT License - см. [LICENSE](LICENSE)

## 👥 Авторы

- **Главный проект:** MedAI Hub (2026)
- **Компоненты:** Интеграция проектов из GitHub:
  - Skin Cancer Detector
  - VoxRad
  - Automated Bone Fracture Detection
  - И другие компоненты

## 🤝 Вклад

Мы приветствуем вклады! Пожалуйста:
1. Форкните репозиторий
2. Создайте ветку (`git checkout -b feature/AmazingFeature`)
3. Отправьте коммит (`git commit -m 'Add AmazingFeature'`)
4. Пушните в ветку (`git push origin feature/AmazingFeature`)
5. Откройте Pull Request

## 📞 Поддержка

- 📧 Email: support@medai-hub.com
- 🐛 Issues: [GitHub Issues](https://github.com/yourusername/medai-hub/issues)
- 💬 Discussions: [GitHub Discussions](https://github.com/yourusername/medai-hub/discussions)

## 📚 Документация

Подробная документация доступна в [docs/](docs/) папке.

---

**Помните:** Здоровье - это наша забота! 🏥❤️
