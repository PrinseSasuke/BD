# Система управления базами данных


# SQLite

### Установка
```
mkdir build
cd build
cmake ..
make
```

### Тесты
```
cd build
make check
```

### Запуск виртуальной таблицы
```
cd build
./bin/sqlite3
```


```
.load ./lib/libvtable.dylib
```
or load `libvtable.so` (Linux), `libvtable.dll` (Windows)

Создание виртуальную таблицу:  
Первый входной параметр задаёт схему виртуальной таблицы. Пожалуйста, придерживайтесь следующего формата:
(имя_столбца [пробел] тип_столбца), разделяя столбцы запятыми.
Мы поддерживаем только базовые типы данных: INTEGER, BIGINT, SMALLINT, BOOLEAN, DECIMAL и VARCHAR.
Второй параметр задаёт схему индекса. Пожалуйста, используйте формат:
(имя_индекса [пробел] имена_индексируемых_столбцов), разделяя индексы запятыми.
```
sqlite> CREATE VIRTUAL TABLE foo USING vtable('a int, b varchar(13)','foo_pk a')
```


```
sqlite> INSERT INTO foo values(1,'hello');
sqlite> SELECT * FROM foo ORDER BY a;
a           b         
----------  ----------
1           hello   
```



https://sqlite.org/vtab.html


