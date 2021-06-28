# Virtual Try-On

Репозиторий содержит код для для установки и совместного запуска моделей [FrankMocap](https://github.com/facebookresearch/frankmocap) и [MultiGarmentNetwork](https://github.com/bharat-b7/MultiGarmentNetwork), позволяющий реализовать виртуальную примерку 3D модели одежды на видео. 

- FrankMocap позволяет производить захват движения человека по видео и оценивать 3D позу человека. 
- MultiGarmentNetwork используется для покадрового наложения меша одежды на SMPL модель человека, полученную от FrankMocap. 
- В качестве источника 3D моделей одежды используется Digital Wardrode из репозитория MultiGarmentNetwork.

## Примеры работы модели:
![First dancing man](https://github.com/LukashevichIlya/Virtual-Try-On/blob/master/media/dancing_man_1.gif?raw=true)
![Second dancing man](https://github.com/LukashevichIlya/Virtual-Try-On/blob/master/media/dancing_man_2.gif?raw=true)
![Third dancing man](https://github.com/LukashevichIlya/Virtual-Try-On/blob/master/media/dancing_man_3.gif?raw=true)

## Особенности

- Основной код для запуска моделей доступен в ноутбуке `Virtual-Try-On.ipynb`, который запускался на Google Colab. Также используется немного измененный код модели FrankMocap, который доступен в [моем fork-е их репозитория](https://github.com/LukashevichIlya/frankmocap/tree/virtual-try-on).
- Время обработки одного кадра видео с рендерингом двух 3D моделей одежды – около 5-6 секунд при запуске с GPU на Google Colab. Удалось увеличить скорость обработки по сравнению со стандратными функциями из библиотек за счет передачи загруженной SMPL модели в качестве параметра в функции (подробнее в ноутбуке).
- Возможное улучшение – добавить проверку пересечения меша SMPL и меша одежды для того, чтобы не производить рендеринг невидимой части одежды, которая, к примеру, закрыта телом человека на видео.
