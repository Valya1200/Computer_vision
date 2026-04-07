# Лабораторная работа №5

Цель: Разработать нейронную сеть для сегментации участков подстилающей поверхности

## ШАГ 1 Загрузка данных 
За основу был составлен датасет по сегментации участков подстилающих поверхностей 
Состояющий из 10 классов: синий, красный, зеленый, розовый, серый, белый, светло-серый, светло-зеленый, бордовый, черный

Тестовая выборка – 15 изображений
Тренировочная выборка – 222 изображений
Валидационная выборка -34 изображений
Фотографии размером 256x256 

Выборка данных

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/7a0e9ae4-85a4-4032-a5e6-6d39877493ce" />

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/fd771cb2-d0df-4bfe-b9c6-10944915175f" />


## Общие характеристики разработанной модели с архитектурой U-Net 

<img width="850" height="229" alt="image" src="https://github.com/user-attachments/assets/7771e8a6-a8aa-404b-856a-85d3b4229d55" />

Энкодер реализован на основе ResNet и включает: 5 уровней даунсэмплинга, Использование strided convolutions
Декодер включает: 5 уровней апсэмплинга, Механизмы внимания (SCSE-блоки), Skip-connections 
Всего 230 обучаемых параметров в полной архитектуре

Выходной слой: Softmax-активация
Параметры обучения: Оптимизатор: Adam (lr = 0.0005), Функция потерь: DiceLoss, Размер батча: 32,Количество эпох: 80

<img width="1068" height="681" alt="image" src="https://github.com/user-attachments/assets/84ae0e2b-65fb-483d-a983-9233ed7b1731" />



Аугментация данных -> 1548 изображений
горизонтальное отражение, изменение размера,  случайная обрезка, добавление паддинга, добавление одной из аугментации из групп: размытие, шум, резкость и цвет, яркость, контраст.

Пример аугментации данных цветовой импульсный шум и размытие 

<img width="800" height="378" alt="image" src="https://github.com/user-attachments/assets/90a6a137-e9c6-457e-8840-321ee9b9184f" />


### Наглядная схема этапов

<img width="897" height="391" alt="2026-04-06_00-37-52" src="https://github.com/user-attachments/assets/522cb6ce-8925-4675-a680-3490a124e1d9" />


## Результаты работы 

<img width="1330" height="512" alt="image" src="https://github.com/user-attachments/assets/61f12c25-2539-4a4a-9f82-93574b1611d0" />

Метрика IoU

<img width="500" height="384" alt="image" src="https://github.com/user-attachments/assets/34e938fb-5f09-4534-8636-0ee26294b12a" />


<img width="1070" height="555" alt="image" src="https://github.com/user-attachments/assets/666f7be5-8499-44e9-aefd-f0e5c1857b71" />


