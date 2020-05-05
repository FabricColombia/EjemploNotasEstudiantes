# Ejemplo de ejecución de un contrato escrito en JavaScript en Hyperlegger fabric

Para el ejemplo ejecutaremos el codigo creado por Salman Dabbakuti donde crea una red blockchain que almacena las notas de unos estudiantes.
Basicamente el contrato inteligente consiste en tres metodos: Agregar nota, eliminar nota y mostrar las notas de un estudiante en específico.

lo primero que se hace es clonar el seguiente repositorio:
```
git clone https://github.com/Salmandabbakuti/hlf-chaincodeTest.git
```
Se accede a la carpeta basic-network de la siguiente manera.

```
cd hlf-chaincodeTest/basic-network
```

Finalmente iniciamos la red
```
./start.sh
```

Ahora para inicializar el chaincode 
