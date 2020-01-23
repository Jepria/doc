# Настройка локального прокси для доступа к удалённым репозиториям через *NPM*, *Yarn*, *Maven* в среде *Windows*

## Установка и настройка *CNTLM*

1.Скачать и установить *CNTLM* по стандартному пути установки(*C:\Program Files (x86)\Cntlm*).  

**ВНИМАНИЕ!!!**  
Не стоит рисковать, устанавливая файл в другие директории. Это может привести, как минимум, к нестабильной работе.

2.Найти и изменить следующие настройки в файле *C:\Program Files (x86)\Cntlm\cntlm.ini* значениями, соответствующими
вашей учетной записи.

```
Username	YOUR_USERNAME
Domain		YOUR_DOMAIN
Proxy		YOUR_PROXY_IP:PORT
NoProxy		localhost, 127.0.0.*, 10.*, 192.168.*
Listen		53128
```

3.Открыть консоль, и выполнить следующие команды для генерации хэша пароля:

```
> cd c:\the_install_directory_of_cntlm
> cntlm -H
Password: введите пароль учетной записи
PassLM          D6888AC8AE0EEE294D954420463215AE
PassNT          0E1FAED265D32EBBFB15F410D27994B2
PassNTLMv2      91E810C86B3FD1BD14342F945ED42CD6 # Only for user YOUR_USERNAME, domain YOUR_DOMAIN
```

4.Скопируйте целиком последнюю строку из консоли в файл *C:\Program Files (x86)\Cntlm\cntlm.ini*

**ВНИМАНИЕ!!!!**  
- Файл *C:\Program Files (x86)\Cntlm\cntlm.ini* обязательно должен содержать ОДНУ пустую строку до параметров и ОДНУ после
и строго не рекомендуется изменять пробелы и отступы в значениях конфигурации. (Особенности парсинга файла)
- НЕ забывайте выполнять шаг 3) каждый раз при смене пароля от учетной записи, в противном случае заблокируется учетная
запись, из-за попыток обращения к прокси-серверу с неправильными данными.
- В последующем каждый раз, меняя файл cntlm.ini, не забывайте выполнять перезапуск сервиса *CNTLM Authentication Proxy*

5.Запустите сервис *CNTLM Authentication Proxy*, через Службы Windows или консольной командой (возможно будут необходимы права администратора)

```
net start cntlm
```

## Настройка *Npm*

В консоли выполнить следующие команды:

```
> npm config set proxy http://localhost:53128
> npm config set https-proxy http://localhost:53128
> npm config set registry https://registry.npmjs.org
```

## Настройка *Yarn*
Если Yarn ранее уже был установлен и его файл настроек *%USER_HOME%/.yarnrc* существует, то, поскольку следующей командой он будет полностью переписан, на всякий случай текущую версию этого файла лучше сохранить. Возможно, она понадобится для переноса старых настроек.

В консоли выполнить следующую команду:

```
> yarn config set registry https://registry.npmjs.org
```

При необходимости перенести старые настройки из сохранённой старой версии файла в *.yarnrc*.

## Настройка *Maven* 
Изменить настройки proxy в *%USER_HOME%/.m2/settings.xml* следующим образом:

```
<proxies>
    <!-- proxy
     | Specification for one proxy, to be used in connecting to the network.
     |-->
    <proxy>
      <active>true</active>
      <protocol>http</protocol>
      <host>127.0.0.1</host>
      <port>53128</port>
      <nonProxyHosts>local.net|some.host.com</nonProxyHosts>
    </proxy>
  </proxies>
```

При использование mvnw необходимо в jvm.config добавить:
```
-Dhttps.proxyHost=127.0.0.1 -Dhttps.proxyPort=53128
```