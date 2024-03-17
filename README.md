# Lab01
01. Скачайте библиотеку boost с помощью утилиты **wget**.
   Адрес для скачивания ```https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz```.
- ```sh
  $ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
  ```
  * Вывод: <br />
  2024-02-25 19:28:19 (431 KB/s) - «boost_1_69_0.tar.gz» сохранён [111710205/111710205]
  
02. Разархивируйте скаченный файл в директорию ```~/boost_1_69_0```.
- ```sh
  $ tar xzf boost_1_69_0.tar.gz
  ```

03. Подсчитайте количество файлов в директории ```~/boost_1_69_0``` **не включая** вложенные директории.
- ``` sh
  $ cd ~/boost_1_69_0)
  $ find -type f -maxdepth 1 | wc -l
  ```
  * Вывод: <br />
  12

04. Подсчитайте количество файлов в директории ```~/boost_1_69_0``` **включая** вложенные директории.
- ``` sh
  $ find -type f | wc -l
  ```
  * Вывод: <br />
  61191
   
05. Подсчитайте количество заголовочных файлов, файлов с расширением ```.cpp```, сколько остальных файлов (не заголовочных и не ```.cpp```).
- ``` sh
  $ find -type f -name "*.hpp" | wc -l
  ```
  * Вывод: <br />
  14912
- ``` sh
  $ find -type f -name "*.cpp" | wc -l
  ```
  * Вывод: <br />
  13774
- ``` sh
  $ find -type f -not -name "*.hpp" -not -name "*.cpp" | wc -l
  ```
  * Вывод: <br />
  32505
      
06. Найдите полный пусть до файла ```any.hpp``` внутри библиотеки _boost_.
- ``` sh
  $ find -type f -name any.hpp
  ```
  * Вывод: <br />
  ./boost/hana/fwd/any.hpp <br />
  ./boost/hana/any.hpp <br />
  ./boost/xpressive/detail/utility/any.hpp <br />
  ./boost/any.hpp <br />
  ./boost/spirit/home/support/algorithm/any.hpp <br />
  ./boost/type_erasure/any.hpp <br />
  ./boost/proto/detail/any.hpp <br />
  ./boost/fusion/include/any.hpp <br />
  ./boost/fusion/algorithm/query/any.hpp <br />
  ./boost/fusion/algorithm/query/detail/any.hpp <br />
      
07. Выведите в консоль все файлы, где упоминается последовательность ```boost::asio```.
- ``` sh
  $ grep "boost::asio" -r
  ```
  
08. Скомпилируйте _boost_. Можно воспользоваться инструкцией или ссылкой.
- ``` sh
  $ sudo apt install libicu-dev
  $ ./bootstrap.sh --prefix=boost_output
  $ ./b2 install -j 8
  ```
  
09. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ```~/boost-libs```.
- ```sh
  $ cd ..
  $ mkdir boost-libs
  $ cd boost_1_69_0/boost_output
  $ mv ./lib ~/boost-libs
  ```
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
- ```sh
  $ du -a ~/boost-libs
  ```
11. Найдите топ10 самых "тяжёлых".
- ```sh
  $ du -a ~/boost-libs | sort -n -r | head
  ```
