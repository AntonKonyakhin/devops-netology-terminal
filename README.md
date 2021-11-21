# devops-netology-terminal

1. Установлен OracleVirtualBox Версия 6.1.28 x64
2. Установлен Hashicorp Vagrant 2.2.19 x 64
3. Терминал Powershell в windows 10
4. выполнено vagrant init, vagrant up
5. Какие ресурсы выделены по-умолчанию?
RAM 1ГБ
HDD dinamic 64 ГБ
CPU - 2 
подключена общая папка с конфигурацией vagrant
6. Как добавить оперативной памяти или ресурсов процессора виртуальной машине?
```
  Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"

    config.vm.provider "virtualbox" do |vb|
        vb.name = "ubuntu_vg"
        vb.memory = "2048"
        vb.cpus=4
    end 
 
end
```
7. выполнил
vagrant ssh
попрактивался с командами ls, pwd, whoami, less, more, touch, mkdir, mv, cat

8. В какой переменной можно задать длину журнала history, и на какой строчке manual это описывается?
Manual page bash(1) line 838

Shell Variables
HISTSIZE
              The number of commands to remember in the command history (see HISTORY below).  If the value is 0, com‐
              mands  are  not saved in the history list.  Numeric values less than zero result in every command being
              saved on the history list (there is no limit).  The shell sets the default value to 500  after  reading
              any startup files.
HISTFILESIZE
              The maximum number of lines contained in the history file.  When this variable is assigned a value, the
              history  file  is truncated, if necessary, to contain no more than that number of lines by removing the
              oldest entries.  The history file is also truncated to this size after writing it when a  shell  exits.
              If  the  value is 0, the history file is truncated to zero size.  Non-numeric values and numeric values
              less than zero inhibit truncation.  The shell sets the default value to the  value  of  HISTSIZE  after
              reading any startup files.		  

что делает директива ignoreboth в bash?
ignorespace — не сохранять строки начинающиеся с символа пробел
ignoredups — не сохранять строки, совпадающие с предыдущими записями
ignoreboth — использовать обе опции ignorespace и ignoredups

HISTCONTROL
              A  colon-separated  list of values controlling how commands are saved on the history list.  If the list
              of values includes ignorespace, lines which begin with a space character are not saved in  the  history
              list.  A value of ignoredups causes lines matching the previous history entry to not be saved.  A value
              of ignoreboth is shorthand for ignorespace and ignoredups.  A value of erasedups  causes  all  previous
              lines  matching  the  current  line to be removed from the history list before that line is saved.  Any
              value not in the above list is ignored.  If HISTCONTROL is unset, or does not include  a  valid  value,
              all  lines  read by the shell parser are saved on the history list, subject to the value of HISTIGNORE.
              The second and subsequent lines of a multi-line compound command are not tested, and are added  to  the
              history regardless of the value of HISTCONTROL.
			  
9. В каких сценариях использования применимы скобки {} и на какой строчке man bash это описано?
{} применимы в сценариях, где нужно подставить значение из скобок, занчение в скобках может быть range.
написано в этой строчке

Manual page bash(1) line 1091


10. однократным вызовом touch можем создать 100000 файлов так:

touch file{1..10000}
аналогичным образом создать 300000 не получается, возникает сообение о том, что мы превысили занчеие ARG_MAX
-bash: /usr/bin/touch: Argument list too long
и нам нужно лучше испольлзовать цикл for.

11. [[ -d /tmp ]]
```
vagrant@vagrant:~$ [[ -d /tmp ]]
vagrant@vagrant:~$ echo $?
0
```

проверяет, что /tmp это директория и возвращает 0 - true

12. создал папку /tmp/new_path_directory
скопировал файл bash из папки /bin/bash в папку /tmp/new_path_directory
```
vagrant@vagrant:~$ type -a bash
bash is /usr/bin/bash
bash is /bin/bash
```
добавил новую запись /tmp/new_path_directory перед записью /usr/bin/bash в PATH 
```
vagrant@vagrant:~$ export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/tmp/new_path_directory:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
vagrant@vagrant:~$ type -a bash
bash is /tmp/new_path_directory/bash
bash is /usr/bin/bash
bash is /bin/bash
```

13. Планировщик at и batch отличаются тем, что при помощи at можно запланировать одноразовые задачи в определенное время, а спомощью batch запланировать задачи, которые ваыполнятся при загрузке системы нже 1.5 или занчения, указанного atd


14. выполнено командой vagrant halt
