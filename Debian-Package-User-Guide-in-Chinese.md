# 如何在 Ubuntu / Debian 系統裡面做套件操作. Debian 的套件管理工具 apt

Debian 底層使用工具 dpkg, 上層使用工具 apt 來管理其套件。 作者：鄭原真, 2002...2018.

許多 Linux 發行版本都有各自的套件管理系統，最常見的便是由 Redhat 所起用的 RPM。Debian 採用了他自己的套件管理系統，並且提供了功能強大的 APT (Advanced Package Tool)，可以幫助您解決套件安裝或是移除過程中，相當棘手的相依性問題。 

Package (套件) 是甚麼 ? 

DEB：DEB 是 DEBIAN/Linux 的套件名稱。Debian 是一個完全由社群推動而成的一個 Linux 發行版本。 

DEB：那麼 Package 是甚麼 ? Package (套件) 是一由一組檔案，包含程式、程式庫、資料檔案以及文件所組成的一個集合。根據套件安裝後的功能，大約可以分成幾個類別： 

* 程式套件：例如 DEB 套件 
* 程式庫套件： 
* 文件套件： 
* 其他套件： 

在沒有套件管理程式之前，我們只能全手動逐一安裝各個程式；安裝之後若要移除套件，只能各憑本領。若是要升級套件，則需要先移除舊版本套件後再安裝新版本套件。若是移除不完整，且恰巧遇上新舊版本程式互相衝突的情形，則後果無法預知。 

有了套件管理程式之後，上述所有問題皆可一併解決。 

套件檔案相關資訊 

DEB 套件的命名：以 perl-doc_5.6.1-5_all.deb 為例，perl-doc 為套件名稱，5.6.1 為套件原始版本，5 為套件發行版本，all 表示本套件是給所有的 CPU 所使用的套件。在 all 這個欄位，其他的值如 i386 表示該套件是給 i386 系列 CPU 使用，或是 alpha 表示該套件是編譯給 alpha 系列 CPU 所執行的程式。 

一個套件檔案內所包含的資料有 

* 套件建立的時間，敘述資訊等。 
* 所要安裝的檔案。 
* 各個檔案安裝後所在的目錄，檔案擁有者，權限設定，...， 檔案大小。 

使用套件管理系統： 

DEB 套件的管理全部都是經過指令 dpkg 來對套件進行安裝，移除，升級等動作。 

安裝套件： 

安裝 DEB套件指令： 

dpkg -i (or -install) options file1.deb ... fileN.deb 

範例：下列指令將把 bash 安裝在你的系統上面 

dpkg -i bash_2.05-7_i386.deb 

安裝過程失敗常見的狀況： 

1. 該套件已經安裝，不能再次安裝 
2. 安裝該套件之前，需要先安裝其他套件 (通常稱為 dependency 問題)。 解決方法便是將所需要的相關套件先行安裝。 
典型的 dependency 關係：安裝 libxxx-dev 之前通常需要先安裝 libxxx。 
3. 所要安裝的套件與現有套件間有衝突 (conflict) 不能安裝該套件。在單一個發行版本中通常是不會有這種情形， 但若你因為需要安裝來自不同發行版本的套件時，便容易會有這樣的情形。 

移除套件： 

移除 DEB 套件指令 

dpkg -r (or --remove) pkg1 ... pkgN 

移除套件 pkg1 ... pkgN，但對於有將設定檔分開的套件，則並不移除設定檔。 

dpkg --purge pkg1 ... pkgN 

移除套件 pkg1 ... pkgN， 含設定檔案等。 

查詢套件的資訊 

範例 

dpkg -l # 列出所有已安裝套件名稱 

dpkg -s info # 查詢套件 'info' 是否安裝 ? 

dpkg -S /usr/bin/info # 查詢包含檔案 /usr/bin/info 的套件為何 ? 

dpkg -L info # 查詢套件 'info' 所所安裝的所有檔案 

APT (Advanced Package Tool) 

apt 是由 Debian 所發展的強大套件維護工具。其後端程式便是 dpkg。apt 程式可以很自動的處理套件的版本一致性問題，套件的升級，移除等等。 

使用方法： 

1. 使用 apt-setup 來設定 /etc/apt/sources.list檔案。或是手動設定 /etc/apt/sources.list。 
2. 執行 apt-get update。這一個指令的功能在於，將 ftp 或是 http 網站上面的套件索引下載。這樣我們就可以經由在硬碟上的索引，來判斷那一個套件需要升級，或是安裝一個套件時，需要配合安裝另一個套件。 
3. 安裝新套件： 

apt-get install 套件名稱 

例如 

apt-get install bash 

apt 便會自動依照 /etc/apt/sources.list 內的資訊，找到最新版本的 bash 套件，並進行下載及安裝。 

4. 移除套件： 

apt-get remove 套件名稱 

例如： 

apt-get remove lynx 

5. 升級系統套件： 

apt-get upgrade 

將系統所有套件進行升級動作，通常在 apt-get update 之後執行 apt-get upgrade。 

apt-get dist-upgrade 

將所有系統套件進行升級，與 apt-get upgrade 不同之處，在於 "apt-get dist-upgrade" 會進行較進一步的演算法來處理套件之衝突的關係，並在維持系統套件整合的情形下，進行套件升級。 

apt-get --simulate upgrade (與 apt-get -s upgrade 一樣) 

加上 --simulate 之後，apt-get 將會列出 apt-get upgrade 指令過程中所有將會執行的動作。這樣我們可以在進行系統升級前，瞭解哪些程式將會被升級，並評估是否要進行升級的動作。 

另外，也支援參數 -d 或寫為 --download-only，意思是說，只下載而不進行安裝的動作。 

6. 刪除系統暫存的 deb 檔案： 

apt-get clean 

經過 apt-get 下載並安裝過的 DEB 檔案，會存放在目錄 "/var/cache/apt/archives/" 下面，而不會自動刪除。 apt-get clean 會將所有 deb 檔案刪除。 

apt-get autoclean 

與 apt-get clean 不同之處在於，apt-get autoclean 只會刪除目錄 "/var/cache/apt/archives/" 下以經過期版本的 DEB 檔案。例如在該目錄下有 bash_2.05-4_i386.deb 與檔案 bash_2.05-7_i386.deb，目前系統安裝的是版本 -7 的 bash 套件(也是最新版本套件)，則 apt-get autoclean 會將 -4 的 bash 套件檔案從硬碟刪除刪除。 

7. 找尋某個尚未安裝的套件的資訊： 

apt-cache search 某個關鍵字 

例如： 

apt-cache search java 

會將所有套件相關資訊中，有 java 字眼的全部顯示出來。 

apt-cache show bash 

會將套件 bash 的所有資訊顯示出來，不管 bash 套件是否安裝在系統內。 

系統安全的維護 

請連線到 http://www.debian.org/security/index.en.html，在該頁面上有說明關於 Debian 對於系統安全修正的處理策略。該策略中最重要的部分，在於 Debian 明確表示，所有系統安全的修正檔案將會在第一時間內放到一個固定的地方。您只需要把該地方的敘述放到 /etc/apt/source.list 即可。 

## 放在 Crontab 裡面每天跑 

每天自動把系統升級到最新版本 !! 

這個想法當然是很令人高興。理想上，Debian 套件管理軟體的確可以做到這樣的功能。為什麼呢？ 

其實套件自動升級，是一件奇妙的事。尤其對於自由軟體/開放源碼這一類的軟體系統來說。簡單來說，大約有下列幾點： 

1. 舊版本程式的正常工作的功能，新版本不一定正常。 
2. 新版本程式的設定檔，格式/放置的位置與新版不一樣。 

其中第一個問題是任何系統都可能遇到的。即便是使用商業軟體，假設你使用了該軟體一個很少人使用的的功能，而新版軟體恰恰好該功能程式沒修改好，所以安裝了新版本軟體，反而你安裝一個工作不正常的軟體。所以，若是一個非常重要的線上系統， 

Debian 的套件在升級時，如果發現是在對系統作升級的動作，則有一個固定的地方可以放入一個將設定檔轉換格式的程式。所以，假設系統中安裝了 Apache，有一天 Apache 出了新版本，也有了 Debian 的套件了，這時候我們當然希望系統可以自動安裝新版本。但是萬一新版的 Apache 與舊版的的 Apache 的設定不同時，便需要人手動去修該設定。 

在我的系統的 cron 放了一個這樣的檔案： 

#! /bin/bash 

apt-get update 

apt-get -y -d dist-upgrade 

apt-get -s dist-upgrade 

這樣我每天就可以經由 cron log 來決定何時需要升級哪些檔案。

# TODO: 加入 autoremove