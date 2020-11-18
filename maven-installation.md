# Установка и конфигурирование [Maven](http://maven.apache.org/)
1. Скачать [архив](https://maven.apache.org/download.cgi) и распаковать в любую папку, например, *C:\tools\maven*
2. Задать системную переменную среды *M2_HOME* со значением равным пути установки Maven, то есть `M2_HOME = C:\tools\maven`.
3. Добавить в системную переменную среды *Path* путь `%M2_HOME%\bin`. После этого Maven должен запускаться из командной строки командой *mvn*.
4. Скопировать конфигурационный файл `C:\tools\maven\conf\settings.xml` в папку `C:\Users\%UserName%\.m2` (при необходимости создать указанную папку из командной строки командой `mkdir C:\Users\%UserName%\.m2`).
5. При необходимости, настроить параметры подключения Maven к центральному репозиторию (в случае если прямой доступ к нему ограничен) одним из следующих способов:
    -	Задать зеркало для центрального репозитория Maven, добавив в конфигурационный файл *.m2\settings.xml* (из профайла пользователя) в секцию *&lt;mirrors&gt;* следующий элемент:
        ```
        <mirror>
          <id>nexus-mirror</id>
          <mirrorOf>central</mirrorOf>
          <url>путь://до/репозитория/Nexus</url>
        </mirror>
        ```
    - [Установить и настроить](https://github.com/Jepria/doc/blob/master/cntlm-settings-for-npm-yarn-maven.md) локальный прокси сервер CNTLM, который позволит Maven корректно подключиться к центральному репозиторию через сетевой прокси сервер.
6. Настроить дополнительный репозиторий *bin-repo* (для поиска зависимостей и плагинов, отсутствующих в центральном репозитории Maven):
    - Склонировать [репозиторий](https://github.com/Jepria/bin-repo) в любую папку, например *C:\bin-repo*.
    - Задать системную переменную среды *BIN_HOME* со значением равным пути размещения репозитория *bin-repo*, то есть `BIN_HOME = C:\bin-repo`.
7. Добавить в конфигурационный файл *.m2\settings.xml* (из профайла пользователя) в секцию *&lt;profiles&gt;* следующий элемент:
    ```
    <profile>
      <repositories>
        <repository>
          <id>binhome-local-deploy</id>
          <name>binhome-local-deploy-repo</name>
          <url>file:${BIN_HOME}\deploy</url>
        </repository>
        <repository>
          <id>binhome-local-build</id>
          <name>binhome-local-build-repo</name>
          <url>file:${BIN_HOME}\build</url>
        </repository>
      </repositories>
      <pluginRepositories>
        <pluginRepository>
          <id>local-maven-plugins-build</id>
          <name>local-maven-plugins-build-repo</name>
          <url>file:${BIN_HOME}\build</url>
        </pluginRepository>
        <pluginRepository>
          <id>local-maven-plugins-deploy</id>
          <name>local-maven-plugins-deploy-repo</name>
          <url>file:${BIN_HOME}\deploy</url>
        </pluginRepository>
      </pluginRepositories>
      <id>binhome</id>
    </profile>
    ```
8. Активировать новый профиль добавлением в тот же файл в секцию *<settings>* следующего элемента:
    ```
    <activeProfiles>
      <activeProfile>binhome</activeProfile>
    </activeProfiles>
    ```
Пример готового конфигурационного файла settings.xml: [maven-settings.xml](maven-settings.xml)

