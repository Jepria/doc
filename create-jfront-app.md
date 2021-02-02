# Создание jfront-приложения

### Генерация основного кода
1. Вручную написать спецификацию API приложения в формате `swagger.json` или взять существующий файл. 
    Пример расположения: 
    `C:\work\TargetProject\App\service-rest\src\main\api-spec\entity\swagger.json`
2. Загрузить [шаблоны генерации](https://github.com/Jepria/tool-generator-core/tree/main/src/main/resources/mustache-templates) на рабочую станцию.
    Пример расположения: 
    `C:\work\mustache-templates`
3. Запустить генератор из бинарного файла через командную строку
    Пример расположения: 
    `C:\work\bin-ext\build\org\jepria\tools\generator\generator-cli\1.0.0-SNAPSHOT\generator-cli-1.0.0-SNAPSHOT.jar`
    Пример запуска команды: 
    `java -jar "C:\work\bin-ext\build\org\jepria\tools\generator\generator-cli\1.0.0-SNAPSHOT\generator-cli-1.0.0-SNAPSHOT.jar" --api-specs "C:\work\TargetProject\App\service-rest\src\main\api-spec\entity\swagger.json" --template-root-mst "C:\work\mustache-templates\client-react" --partials-root-mst "C:\work\mustache-templates\partials" --output-project-root "C:\work\TargetProject\App"`
    После выполнения сгенерированный код находится в папке
    `C:\work\TargetProject\App\client-react`
4. Вручную прописать текстовые ресурсы в файлах папки `C:\work\TargetProject\App\client-react\public\locales`
5. После этого собрать и развернуть проект можно штатными средствами. Для полноценной работы приложения необходимо наличие работоспособного модуля `service-rest`

### Добавление нового поля на форму в существующем приложении
1. Добавить поле в соответствующий форме тип в файле `EntityTypes.tsx`
    Пример добавления поля:
    ```
    export interface EntityCreate {
      ...
      newField: string;
      ...
    }
    ```
2. Добавить поле на необходимую UI-форму по шаблону
    Пример формы: `EntityCreatePage.tsx`
    Пример шаблонного поля типа `string`:
    ```
    <Form.Field>
      <Form.Label required>{t("entity.fields.newField")}</Form.Label>
      <Form.Control error={formik.errors.newField as string}>
        <TextInput
          name="newField"
          value={formik.values.newField}
          onChange={formik.handleChange}
        />
      </Form.Control>
    </Form.Field>
    ```
3. При необходимости добавить начальное значение нового поля в блок `initialValues` формика
    Пример:
    ```
    initialValues: {
      ...
      newField: "abc",
      ...
    },
    ```
4. Добавить текстовые ресурсы для поля в файлах папки `C:\work\TargetProject\App\client-react\public\locales`
5. После этого собрать и развернуть проект можно штатными средствами. Для полноценной работы приложения необходимы соответствующие изменения в модуле `service-rest`
