# Laravel_install_note
Laravel git clone 專案後要打的指令 跟 Laravel 安裝套件需要打的指令跟注意事項
<h1>Laravel git clone 專案後要打的指令如下</h1>
<ul>
 <li> composer install 安裝有用到的套件 (npm 前端管理套件  composer php後端管理套件)</li>
 <li> cp .env.example .env 複製一份原始環境 </li>
 <li> php artisan key:generate 產生金鑰 </li>
 <li> 之後還要到.env重新設定 database的帳密登入 </li>
 <li> 5.7以上Laravel 可能會因為密碼不能是空值會報錯，可能需要去刷新database的使用者權限 </li> 
</ul>
<h1> Laravel 安裝套件 </h1>
  以下套件暫時以jorenvanhocht/laravel-share 代替</br>
   composer require 套件名 (安裝套件) </br>
 到 config/app.php
'providers' => [ //這裡是放置安裝的套件 </br>
    ...
    Jorenvh\Share\Providers\ShareServiceProvider::class,
]; </br>
到 config/app.php
'aliases' => [ //這裡是啟動套件關鍵字，基於後面的服務 </br>
    ...
    'Share' => Jorenvh\Share\ShareFacade::class,
]; </br>
php artisan vendor:publish --provider="Jorenvh\Share\Providers\ShareServiceProvider" 這個指令是發行套件的許可證，發行到vendor並啟動服務，不打的話就不能用套件
