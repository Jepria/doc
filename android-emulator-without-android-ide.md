# Установка эмулятора без установки android studio
*Позволяет работать не устанавливая лишнего*

## Скачиваем SDK tools
Зайдя на сайт с дистрибутивами https://developer.android.com/studio мы сразу увидим массу информации, касающейся android studio, но то что нам нужно, в данный момент (*01.2020*), находится в самом низу под названием "Command line tools only".
Скачиваем SDK tools package и распаковываем архив в удобное место.

## Прописываем переменные окружения
Для удобства работы и корректного функционирования смежных программ прописываем в переменные окружения пути к SDK:
- ANDROID_SDK = <Путь к развернутому SDK>
- ANDROID_SDK_ROOT =  <Путь к развернутому SDK>
- Добавляем в PATH <Путь к развернутому SDK>\tools\bin;<Путь к развернутому SDK>\tools

## Устанавливаем необходимые приложения для SDK
- Устанавливаем компоненты для графической системы 
```
sdkmanager "extras;google;Android_Emulator_Hypervisor_Driver" --no_https --proxy=http --proxy_host=127.0.0.1 --proxy_port=3128
sdkmanager "extras;android;m2repository" --no_https --proxy=http --proxy_host=127.0.0.1 --proxy_port=3128
```

- Устанавливаем утилиты для работы с платформой и сборки
```
sdkmanager "platform-tools" --no_https --proxy=http --proxy_host=127.0.0.1 --proxy_port=3128
sdkmanager "build-tools;29.0.2" --no_https --proxy=http --proxy_host=127.0.0.1 --proxy_port=3128
```
- Устанавливаем эмулятор
```
sdkmanager "emulator" --no_https --proxy=http --proxy_host=127.0.0.1 --proxy_port=3128
```

- Устанавливаем платформу и образ android 10
```
sdkmanager "platforms;android-29" --no_https --proxy=http --proxy_host=127.0.0.1 --proxy_port=3128
sdkmanager "system-images;android-29;default;x86_64" --no_https --proxy=http --proxy_host=127.0.0.1 --proxy_port=3128
```

Для того, чтобы посмотреть список всех пакетов с описаниями можно выполнить:
```
sdkmanager --list  --no_https --proxy=http --proxy_host=127.0.0.1 --proxy_port=3128
```

*Как нетрудно было заметить, в примере установка происходит через прокси. Если сеть не требует прокси, то параметры прокси можно опустить.*

## Создаем виртуальную машину

Для создания виртуальной машины воспользуемся утилитой "android", входящей в состав SDK
```
android create avd --name android10 --package "system-images;android-29;default;x86_64"
```
## Запускаем виртуальную пашину
Если все прошло гладко то можем попробовать запустить нашу машину. Правда для этого следует еще убедиться что у Вас правильно настроена виртуализация. Для этого я использовал информацию со следующего ресурса: https://facebook.github.io/react-native/docs/getting-started.html

Для запуска машины следует выполнить:
```
emulator -avd android10
```

*В заключении привожу ссылки на ресурсы, которые мне помогли настроить работу с react-native: VS Code for ReactNative https://medium.com/react-native-training/vscode-for-react-native-526ec4a368ce;  https://medium.com/@jasonwang_26533/get-started-with-react-native-in-vs-code-part-1-8ecd654a1562; https://facebook.github.io/react-native/docs/getting-started.html*
