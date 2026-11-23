<div align="center">

# 📰 Blogicum

**Блог-платформа на Django: публикации с отложенной датой, категории, комментарии, профили и регистрация пользователей**

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-5.1-092E20?logo=django&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5-7952B3?logo=bootstrap&logoColor=white)
![Tests](https://img.shields.io/badge/pytest-26%2F26_passed-2ea44f?logo=pytest&logoColor=white)

</div>

> Итоговая версия проекта. Предыдущие этапы: [django-sprint1](https://github.com/vadim-guseinov/django-sprint1) (шаблоны и маршрутизация) → [django-sprint3](https://github.com/vadim-guseinov/django-sprint3) (модели и админка) → **django-sprint4**.

## О проекте

Blogicum — полноценный блог: пользователи регистрируются, пишут посты с картинками, привязывают их к категории и месту, комментируют чужие публикации и ведут свою страницу профиля.

## Возможности

- Регистрация, вход, выход, смена и восстановление пароля (письма сохраняются в файлы — `EMAIL_BACKEND` для разработки).
- Создание, редактирование и удаление постов только автором; загрузка изображений.
- **Отложенная публикация**: пост с будущей датой и снятые с публикации посты видит только автор в своём профиле.
- Комментарии с редактированием и удалением автором; счётчик комментариев через `annotate(Count)`.
- Пагинация по 10 постов, страницы категорий и профилей.
- Собственные страницы ошибок 403 (CSRF), 404, 500.
- Админ-панель для управления постами, категориями и локациями.

## Что сделано

- Модели `Post`, `Category`, `Location`, `Comment` с миграциями.
- Общий QuerySet с `select_related` и `annotate` вынесен в `utils.py` — без дублирования и N+1 запросов.
- Формы на ModelForm, шаблоны на наследовании и include-блоках, Bootstrap 5.
- **26 из 26 автотестов** проходят.

## Стек

Python 3.12 · Django 5.1 · Django ORM · SQLite · Pillow · django-bootstrap5 · pytest

## Запуск

**Требования:** Python 3.10+ (проверено на 3.12).

```bash
git clone https://github.com/vadim-guseinov/django-sprint4.git
cd django-sprint4
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt

cd blogicum
python manage.py migrate
python manage.py loaddata ../db.json    # тестовые данные
python manage.py createsuperuser
python manage.py runserver
```

Сайт: http://127.0.0.1:8000/ · админка: http://127.0.0.1:8000/admin/

### Тесты

```bash
pytest          # из корня репозитория
```

## Автор

**Вадим Гусейнов** — Python-разработчик (Backend) · [Telegram](https://t.me/eviliing)
