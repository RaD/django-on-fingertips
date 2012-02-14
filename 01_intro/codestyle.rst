****************
Общие соглашения
****************

====================
Стиль исходного кода
====================

Пожалуйста, следуйте следующим правилам при разработке своих приложений:

* Если особо не оговорено иное, надо использовать стандарт :pep:`8`. Можно
  использовать утилиту аналогичную `pep8.py`_ для проверки исходного кода.

* Для отступа следует использовать четыре пробела.

* Пользуйтесь символами подчёркивания (_), а не выделениемРегистра при указании
  имён переменных, функций и методов (т.е., `poll.get_unique_voters()`, а не
  `poll.getUniqueVoters()`).

* Используйте заглавные буквы в определении класса или функций, которые
  возвращают классы (например, `InitialCaps`).

* Подготовьте все строки к переводу.

* В строках документации используйте «активные слова», например::

    def foo():
        """
        Посчитает что-то и вернёт результат.
        """
        pass

  а не::

    def foo():
        """
        Посчитать что-то и вернуть результат.
        """
        pass

* Не указывайте своё имя в коде. Политика Django предусматривает хранение имён
  авторов кода в файле AUTHORS.

.. _`pep8.py`: http://svn.browsershots.org/trunk/devtools/pep8/pep8.py

=======
Шаблоны
=======

В шаблонах используйте только один пробел между фигурными скобками и содержимым
тега.

Делайте так::

    {{ foo }}

а не так::

    {{foo}}

=============
Представления
=============

В представлениях первым параметром всегда должен быть `request`.

Делайте так::

    def my_view(request, foo):
        # ...

а не так::

    def my_view(req, foo):
        # ...

======
Модели
======

Имена полей должны определяться в нижнем регистре с использованием символа
подчёркивания.

Делайте так::

    class Person(models.Model):
        first_name = models.CharField(max_length=20)
        last_name = models.CharField(max_length=40)

а не так::

    class Person(models.Model):
        FirstName = models.CharField(max_length=20)
        Last_Name = models.CharField(max_length=40)

Класс `Meta` должен описываться после определения полей, отделённый от них
пустой строкой.

Делайте так::

    class Person(models.Model):
        first_name = models.CharField(max_length=20)
        last_name = models.CharField(max_length=40)

        class Meta:
            verbose_name_plural = 'people'

а не так::

    class Person(models.Model):
        first_name = models.CharField(max_length=20)
        last_name = models.CharField(max_length=40)
        class Meta:
            verbose_name_plural = 'people'

и не так::

    class Person(models.Model):
        class Meta:
            verbose_name_plural = 'people'

        first_name = models.CharField(max_length=20)
        last_name = models.CharField(max_length=40)

Порядок внутренних классов модели и стандартных методов должен быть таким (ничто
из нижеперечисленного не является обязательным):

* Определение всех полей класса.

* `class Meta`.

* `def __unicode__()`.

* `def save()`.

* `def get_absolute_url()`.

* Любые свои методы.

Если для модели определена опция `choices`, определите выбор в виде кортежа
кортежей, использовав заглавные буквы для его имени. Определение лучше помещать
в начале файла с моделями или перед классом.

Пример::

    GENDER_CHOICES = (
        ('M', 'Male'),
        ('F', 'Female'),
    )
