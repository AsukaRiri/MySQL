# MySQL

###Windows下忘記ROOT密碼的修改方式

1、停止MYSQL服務，CMD打開命令提示字元窗口，輸入 net stop mysql

2、在CMD命令提示字元窗口，進入MYSQL安裝目錄，比如 C:\Program Files\MySQL\MySQL 5.5\bin

3、進入mysql安全模式，即當mysql起來後，不用輸入密碼就能進入資料庫。

輸入 mysqld --skip-grant-tables

4、重新打開一個CMD命令提示字元窗口，輸入mysql -uroot -p，使用空密碼的方式登錄MySQL(不用輸入密碼直接按enter)

5，輸入以下命令開始修改root用戶的密碼(注意：命令中mysql.user中間有個「點」)

mysql> update mysql.user set password=PASSWORD('新密碼') where User='root';

6，刷新權限表

mysql> flush privileges;

7、離開
mysql> quit

這樣MYSQL超級管理員賬號ROOT已經重新設定好了，接下來在工作管理員裡結束掉 mysqld.exe (安全模式) 這個處理程序，重新啟動MYSQL即可！

MYSQL重新啟動後，就可以用新設定的ROOT密碼登陸MYSQL了！
