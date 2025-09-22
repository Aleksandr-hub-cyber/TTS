# Wisper_TTS

## Описание

**Wisper_TTS** — проект для экспериментов с синтезом речи (Text-To-Speech, TTS) и распознаванием речи (Whisper) в среде Google Colab. Разработанное приложение является полноценной системой перевода речи в реальном времени с поддержкой клонирования голоса. Оно может быть использовано как в демонстрационных целях, так и в качестве базового прототипа для более сложных решений (например, онлайн-переводчиков в реальном времени).
## Основные возможности

* Whisper (OpenAI) – распознавание речи (ASR).

* MarianMT (Helsinki-NLP) – машинный перевод.

* vXTTS v2 (Coqui-AI) – синтез речи и клонирование голоса.

* Gradio – веб-интерфейс для работы в реальном времени.

## Структура репозитория

```
Wisper_TTS/
├── Whisper_XTTS_v2.ipynb       # Google Colab блокнот с примерами кода
├── README.md          # Документация по проекту
```

## Быстрый старт

1. Клонируйте репозиторий:
   ```bash
   git clone https://github.com/Aleksandr-hub-cyber/Wisper_TTS.git
   cd Wisper_TTS
   ```

2. Запустите Google Colab:
   
   Откройте нужный блокнот и следуйте инструкциям.

## Пример использования

В блокноте можно найти примеры преобразования текста в речь и обратно:

```python
# Пример синтеза речи
    output_path = "output.wav"
    try:
        if ref_audio:
            # Клонирование голоса
            tts_model.tts_to_file(
                text=translated_text,
                language=tgt_lang,
                file_path=output_path,
                speaker_wav=ref_audio
            )
        else:
            # Без клонирования
            tts_model.tts_to_file(
                text=translated_text,
                language=tgt_lang,
                file_path=output_path
            )
    except Exception as e:
        return f"❌ Ошибка синтеза речи: {e}", None

# Пример распознавания речи
    result = asr_model.transcribe(audio, language=src_lang)
    recognized_text = result["text"]
```

3. Реализация

* Вход:
аудиозапись с микрофона или файла.

* Опционально:
референсное аудио для клонирования голоса.

* Языки:
  1. Распознавание (Whisper): русский, английский, немецкий.

  2. Перевод (MarianMT): ru↔en, en↔de, de↔en.

  3. Синтез (XTTS v2): многоязычная поддержка (русский, английский, немецкий и др.).

* Выход:

  1. Распознанный текст.

  2. Переведённый текст.

  3. Синтезированная речь на целевом языке с голосом говорящего (при наличии ref_audio).

4. Результаты работы
<img width="1811" height="889" alt="загружено" src="https://github.com/user-attachments/assets/699ecb30-08ac-418a-92b3-f36df7381397" />


На скриншоте показан пример:

* Входное аудио: русская речь с тестовой фразой «Проверка, проверка, раз, два, три, четыре, пять. Привет мир. Проверка, раз, два, три, четыре, пять.».

* Система корректно распознала текст.

* Выполнен перевод на английский язык: “Check, check, one, two, three, four, five, hello, peace, Check, check, one, two, three, four, five.”.

* Выполнен синтез речи с использованием XTTS v2.

* При загрузке референсного аудио сохраняются характеристики голоса.

### Интерфейс предоставляет удобный выбор исходного и целевого языка, загрузку аудио и отображает результат.

## Требования

- Python 3.8+
- Google Colab
- Зависимости:git+https://github.com/openai/whisper.git, transformers==4.44.2 sentencepiece sacremoses, coqui-tts==0.26.1, gradio==5.44.1


## Вклад

Pull request и идеи приветствуются! Для багов и предложений создавайте issue.

---

> Автор: [Aleksandr-hub-cyber](https://github.com/Aleksandr-hub-cyber)
