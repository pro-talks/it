---
layout: post
title:  "Установка jekyll на Windows 7"
date:   2022-10-19 19:05:05 +0300
categories: jekyll installation
permalink: install-jekyll-on-windows-7
---

# Установка jekyll на Windows 7

## Попытка 2 - Успешная

1. [Установить MSYS2](https://www.msys2.org/)
   
   - Обязятельно `pacman -S mingw-w64-x86_64-gcc`
2. Установка Ruby
   
- `1 - MSYS2 base installation` - еще раз запустил на всякий
   
3. [Установка Jekyll](https://jekyllrb.com/)  `gem install bundler jekyll`

4. Запуск `bundle exec jekyll serve`

   **Ошибка**

   ````
   C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve/se
     rvlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
             from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/comm
     ands/serve/servlet.rb:3:in `<top (required)>'
   ````

   **Фикс**

   Добавить `gem "webrick"` в Gemfile

## Проблема при запуске старого проекта

- При запуске старого проекта выпадали предупреждения и не удавалось найти модуль `Could not find ffi-1.11.2 in any of the sources`
- **Решение**
  - Копировать Gemfile из рабочего модуля
  - `bundle update`









## Попытка 1

1. [Install Jekyll on Windows](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_install_jekyll_on_windows.html#install-ruby-and-ruby-development-kit)

2. Install ruby

3. [Install msys](https://www.msys2.org/)

4. ```
   gem install jekyll
   ```

5. Move to directory with blog

   - gem install bundler
   - remove  existing `Gemfile` and `Gemfile.lock` files.
   - bundle init

6. Paste

   ```
   source "https://rubygems.org"
   
   gem 'wdm'
   gem 'jekyll'
   ```

7. ERROR: Failed to build gem native extension.

   ```
   Gem::Ext::BuildError: ERROR: Failed to build gem native extension.
   
       current directory: C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/wdm-0.1.1/ext/wdm
   C:/Ruby31-x64/bin/ruby.exe -I C:/Ruby31-x64/lib/ruby/3.1.0 -r
       ./siteconf20221019-6140-s1293p.rb extconf.rb
       checking for -lkernel32... *** extconf.rb failed ***
   Could not create Makefile due to some reason, probably lack of necessary
   libraries and/or headers.  Check the mkmf.log file for more details.  You may
   need configuration options.
   
   Provided configuration options:
           --with-opt-dir
           --without-opt-dir
           --with-opt-include
   ```

8. [Схожая ошибка, рекомендация переустановить все заново](https://github.com/travis-ci/travis.rb/issues/558#issuecomment-355962361)
9. Все почистил