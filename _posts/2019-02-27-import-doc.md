---
title: Импортируем doc
author: ~
date: '2019-02-27'
slug: импортируем-doc
categories: []
tags: []
---

Увы, статистические данные часто размещены в неудобном старинном вордовском формате `.doc` :)

1. Ставим R пакет `docxtractr`.
2. Устанавливаем [LibreOffice](https://www.libreoffice.org/download/download/).
3. Находим исполняемый файл LibreOffice и указываем путь к нему.
Например, под Windows это может выглядеть так:

```r
library(docxtractr)
set_libreoffice_path("C:/Program Files/LibreOffice/program/soffice.exe")
```
На linux и macos из командной строки можно набрать: 

```bash
which libreoffice
```

И далее, например:

```r
set_libreoffice_path("/usr/bin/libreoffice")  
Sys.setenv(LD_LIBRARY_PATH = "/usr/lib/libreoffice/program/") 
```

Если на ubuntu появляется ошибка с ненайденным libreglo.so, то дело в `LD_LIBRARY_PATH`.

4. Берём для примера файл doc c gks. Можно не скачивать, а использовать ссылку:

```r
url = 'http://www.gks.ru/bgd/regl/b18_02/IssWWW.exe/Stg/d010/1-08.doc'

tbl = docxtractr::read_docx(url)
table_1 = docx_extract_tbl(tbl, tbl_number = 1, header = TRUE, preserve = FALSE, trim = FALSE)
```
5. Profit!
