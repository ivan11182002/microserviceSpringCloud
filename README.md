# startGradle
##練習建置Gradle專案
**build.gradle說明**
1.`apply plugin`: 引入插件，這裡引入 java 及 war 兩個插件，這樣就可以編譯、測試並包裝 war 檔了 (一般 console、desktop 程式不需要引入 war 這個插件)。

2.`sourceCompatibility`: 指出編譯要用的 JDK 版本，這裡指出是要用 1.8 版。

3.`version`: 設定我們自己的這個專案的版本編號

4.`sourceSets`: 裡面比較值的注意的是 resources，設定檔我們是放在專案的根目錄下的 config 目錄裡，所以 12~14 是必要的，不然 gradle 不會知道要把這個目錄下的檔案也包裝進 war。至於 main/java、test/java 這兩個設定因為值都是 gradle 的預設值，在這裡是可省略的。

5.`buildDir`: 指出編譯後的產出要放到那個目錄下。

6.`repositories`: 指出 gradle 要到那些網站抓 jar 檔。

7.`configurations.all`: gradle 抓 jar 檔的時候，會把相依的 jar 檔一併抓下來，不然，我們要找到所有相依 jar 檔會浪費非常大量年輕寶貴的生命，但是，有時候我們不想要其中的某些 jar 檔時，可以在這裡以 exclude group 將它排除，或是 gradle 抓下來的 jar 版本不是我們想要的，可以用 force group 強制限定版本。

8.`dependencies`: 這是一般人最熟悉的部份，把我們專案需要的 jar 檔寫在這裡，有些 framework 會有非常多的 jar 檔，版號又一樣，那麼，可以先用 def 定義版號的變數，省去每次換版本的麻煩。

9.`compile fileTree`: 有一些 jar 檔不是到網路上的 jar repository 裡抓的，是放在自己的電腦某處，像這裡，這類的 jar 檔是放在專案根目錄的 library 目錄下，所以要這個指令指出來。

10.`testCompile group`: 指出測試時要用的 framework，這裡使用的是 JUnit 4.+ 版。
