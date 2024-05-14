## Данные

Данные взяты из нескольких открытых источников: [Сообщество Натуралистов](https://www.inaturalist.org/), [iNat2021](https://paperswithcode.com/dataset/inat2021) и [ImageNet-tiny](https://paperswithcode.com/dataset/tiny-imagenet). 

В итоговом датасете 3 поля:
1) `tree_types` с тремя классами: название дерева из 41 наиболее распространенных видов в окрестности г.Минска, класс с другими растениями "Other",  и класс "not_plant", если загружаемое фото НЕ РАСТЕНИЕ.
2) `file_paths` - путь к папке, в которой лежит изображение.
3) `labels` содержит числовые метки каждого класса из `tree_types`, присвоенные с помощью "Target label encoding".

## Задача
Создать модель компьютерного зрения, определяющая по загружаемому пользователем фото, относится ли оно к 41 классу наиболее встречающихся деревьев в округе г.Минска(Республика Беларусь). 
Для создания модели нужно применить библиотеку `PyTorch`, как наиболее современную и удобная для глубокого обучения нейросетей. 
В качестве обработчика изображений - использовать `Vision transformer`.

## Результаты
- Данные из 3-ех источников собраны и обработаны, в результате сформирован итоговый датасет.
- Локации картинок на диске преобразованы в датасет тензоров, для дальнейшей загрузки в `data loader`.
- Вся выборка разбита на тестовую и тренировочную.
- Создана модель `многоклассовой классифиикации` на основании `предобученной модели из библиотеки "Timm"`, с применением ее весов.
- В результате обучения на 4-ех эпохах получены стабильные результаты метрик, без допущения переобучения.
- Ошибка модели на тестовых данных `= 0.077`; точность(accuracy) = `0.977`.
- Модель проверена на точность определение класса случайного изображения.
- Дополнительно исследована метрика `"top-k accuracy"`, т.к. классификация многоклассовая.
- Сделан отчет по метрикам по каждому из 42 меток классов.
- Определено `топ-10 растений` из списка с наиболее часто встречающихся в Минской области, на основании `метрики f1-score`. 
- Сделан `прототип API` для интеграции модели и проверки ее работы на практике(ссылка доступна по запросу).

## Используемые инструменты и библиотеки
- *pandas*
- *PyTorch*
- *numpy*
- *PIL*
- *timm*
- *sklearn*
- *seaborn*
- *tqdm*
- *time*
- *Vision transformer*

