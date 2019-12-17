# 特權埠口 (Privileged Ports)
http://linux.vbird.org/linux_server/0110network_basic.php#tcpip_transfer_tcp_pport

網路既然是雙向的，一定有一個發起端。問題是，到底要連線到伺服器取得啥玩意兒？ 也就是說，哪支程式應該在哪個埠口執行，以讓大家都知道該埠口就是提供哪個服務，如此一來，才不會造成廣大用戶的困擾嘛！ 所以囉，Internet 上面已經有很多規範好的固定 port (well-known port)， 這些 port number 通常小於 1024 ，且是提供給許多知名的網路服務軟體用的。 在我們的 Linux 環境下，各網路服務與 port number 的對應預設給他寫在 /etc/services 檔案內喔！ 底下鳥哥列出幾個常見的 port number 與網路服務的對應：

<table width="95%" border="1" cellspacing="0" cellpadding="3" bgcolor="lightyellow">
<tr bgcolor="lightblue" align="center"><td width="100">連接埠口</td><td>服務名稱與內容</td></tr>
<tr><td align="center">20</td><td>FTP-data，檔案傳輸協定所使用的主動資料傳輸埠口</td></tr>
<tr><td align="center">21</td><td>FTP，檔案傳輸協定的命令通道</td></tr>
<tr><td align="center">22</td><td>SSH，較為安全的遠端連線伺服器</td></tr>
<tr><td align="center">23</td><td>Telnet，早期的遠端連線伺服器軟體</td></tr>
<tr><td align="center">25</td><td>SMTP，簡單郵件傳遞協定，用在作為 mail server 的埠口</td></tr>
<tr><td align="center">53</td><td>DNS，用在作為名稱解析的領域名稱伺服器</td></tr>
<tr><td align="center">80</td><td>WWW，這個重要吧！就是全球資訊網伺服器</td></tr>
<tr><td align="center">110</td><td>POP3，郵件收信協定，辦公室用的收信軟體都是透過他</td></tr>
<tr><td align="center">443</td><td>https，有安全加密機制的WWW伺服器</td></tr>
</table>

另外一點比較值得注意的是，小於 1024 以下的埠口要啟動時， 啟動者的身份必須要是 root 才行，所以才叫做特權埠口嘛！這個限制挺重要的，大家不要忘記了喔！ 不過如果是 client 端的話，由於 client 端都是主動向 server 端要資料， 所以 client 端的 port number 就使用隨機取一個大於 1024 以上且沒有在用的 port number。

* Socket Pair
由於網路是雙向的，要達成連線的話得要伺服器與用戶端均提供了 IP 與埠口才行。 因此，我們常常將這個成對的資料稱之為 Socket Pair 了！

* 來源 IP + 來源埠口 (Source Address + Source Port)
* 目的 IP + 目的埠口 (Destination Address + Destination Port)

由於 IP 與埠口常常連在一起說明，因此網路定址常常使用『 IP:port 』來說明，例如想要連上鳥哥的網站時， 正確的鳥哥網站寫法應該是：『 linux.vbird.org:80 』才對！
