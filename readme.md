# pythonInterfacePyQt5
[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://github.com/JonathanJosa/pythonInterfacePyQt5/blob/Main/act4.py)

Código programado en python para el funcionamiento de una interfaz con dos funciones principales, creacion de un archivo con ext txt y analisis del mismo archivo que incluye numero de vocales y consonantes.

- **Entradas:**
- Nombre del archivo
- Numero de lineas
- Texto a excribir
- Numero de lineas en archivo
- **Salidas**
- Numero de vocales
- Numero de consonantes


## Instalación

Requiere instalacion basica de python [Python (.py)](https://www.python.org/downloads/) v3.7+ para ejecutar.

Instala igualmente las dependencias

```sh
pip install PyQt5
```
O para pip3
```sh
pip3 install PyQt5
```

## Construcción


Importamos las librerias necesarias:
```sh
import sys
from PyQt5 import QtCore, QtGui, QtWidgets
```

Primera ejecución, creacion de nuestro main y objeto de interfaz:
El código esta conectado a la clase Ui_MainWindow

```python
if __name__ == "__main__":
    app = QtWidgets.QApplication(sys.argv)
    MainWindow = QtWidgets.QMainWindow()
    ui = Ui_MainWindow()
    ui.main(MainWindow)
    MainWindow.show()
    sys.exit(app.exec_())
```

Declaramos en nuestra funcion Main dentro de nuestra clase los diferentes objetos:

```python
class Ui_MainWindow(object):

    def main(self, MainWindow):
        MainWindow.resize(600, 650)
        self.widgets = QtWidgets.QWidget(MainWindow)
```

Boton

```python
self.analizar = QtWidgets.QPushButton(self.widgets)
self.analizar.setGeometry(QtCore.QRect(225, 360, 150, 32))
self.analizar.setText("Analizar")
self.analizar.clicked.connect(self.detectData)
```

Label

```python
self.label_1 = QtWidgets.QLabel(self.widgets)
self.label_1.setGeometry(QtCore.QRect(350, 90, 150, 32))
self.label_1.setText("Nombre del archivo")
```

Line Edit

```python
self.input_1 = QtWidgets.QLineEdit(self.widgets)
self.input_1.setGeometry(QtCore.QRect(100, 90, 150, 32))
```


Jutamos todo:
Añadimos la función 
MainWindow.setCentralWidget(self.widgets)
Esto para unificar todos los elementos


```python
    def main(self, MainWindow):
        MainWindow.resize(600, 650)
        self.widgets = QtWidgets.QWidget(MainWindow)

        self.input_1 = QtWidgets.QLineEdit(self.widgets)
        self.input_1.setGeometry(QtCore.QRect(100, 90, 150, 32))

        self.input_2 = QtWidgets.QLineEdit(self.widgets)
        self.input_2.setGeometry(QtCore.QRect(100, 180, 150, 32))

        self.input_3 = QtWidgets.QLineEdit(self.widgets)
        self.input_3.setGeometry(QtCore.QRect(100, 270, 150, 32))

        self.label_1 = QtWidgets.QLabel(self.widgets)
        self.label_1.setGeometry(QtCore.QRect(350, 90, 150, 32))
        self.label_1.setText("Nombre del archivo")

        self.label_2 = QtWidgets.QLabel(self.widgets)
        self.label_2.setGeometry(QtCore.QRect(350, 180, 150, 32))
        self.label_2.setText("Texto a escribir")

        self.label_3 = QtWidgets.QLabel(self.widgets)
        self.label_3.setGeometry(QtCore.QRect(350, 270, 150, 32))
        self.label_3.setText("Numero de lineas en archivo")

        self.analizar = QtWidgets.QPushButton(self.widgets)
        self.analizar.setGeometry(QtCore.QRect(225, 360, 150, 32))
        self.analizar.setText("Analizar")
        self.analizar.clicked.connect(self.detectData)

        self.label_4 = QtWidgets.QLabel(self.widgets)
        self.label_4.setGeometry(QtCore.QRect(100, 450, 150, 32))
        self.label_4.setText("Numero de vocales")

        self.label_5 = QtWidgets.QLabel(self.widgets)
        self.label_5.setGeometry(QtCore.QRect(350, 450, 150, 32))
        self.label_5.setText("Numero de consonantes")

        self.input_4 = QtWidgets.QLineEdit(self.widgets)
        self.input_4.setGeometry(QtCore.QRect(100, 540, 150, 32))

        self.input_5 = QtWidgets.QLineEdit(self.widgets)
        self.input_5.setGeometry(QtCore.QRect(350, 540, 150, 32))

        MainWindow.setCentralWidget(self.widgets)
```



#### Añadimos las funciones 

Debemos hacer un conteo de las vocales y conteo de consonantes
Usamos la logica de consonantes = (longitud de palabra - cantidad de vocales) * cantidad de lineas
Añadimos esta funcion a nuestra clase

```Python
 def detectData(self, bool_I):
        f = open(self.input_1.text(), "w")
        data = self.input_2.text()
        lines = int(self.input_3.text())
        [f.write(data + "\n") for _ in range(lines)]
        con = 0
        for i in data:
            if(i == 'a' or i == 'e' or i == 'i' or i == 'o' or i == 'u'):
                con += 1
        self.input_4.setText(str(con*lines))
        self.input_5.setText(str((len(data) - con)*lines))
```

## Ejecutar

Para ejecución:

```sh
Python3 file.py
```

## License

ITESM PUE ®
Jonathan Josafat Vázquez Suárez - A01734225
