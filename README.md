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

Ahora para inicializar el chaincode, entramos al CLI container.

```
docker exec -it cli bash
```
Se instala el chaincode:

```
peer chaincode install -n mycc -v 1.0 -p "/opt/gopath/src/github.com/newcc" -l "node"
```

Inicializamos el chaincode:

```
peer chaincode instantiate -o orderer.example.com:7050 -C mychannel -n mycc -l "node" -v 1.0 -c '{"Args":[]}'
```

Invocamos una funcion del script de java para agregar notas a un estudiantes
```
peer chaincode invoke -o orderer.example.com:7050 -C mychannel -n mycc -c '{"function":"addMarks","Args":["Julian","3.9","4.4","4.5"]}'
```

Invocamos una funcion para ver las notas de Julian
```
peer chaincode query -o orderer.example.com:7050 -C mychannel -n mycc -c '{"function":"queryMarks","Args":["Julian"]}'
```

Eliminamos las notas del estudiante Julian

```
peer chaincode invoke -o orderer.example.com:7050 -C mychannel -n mycc -c '{"function":"deleteMarks","Args":["Julian"]}'
```

Ya podemos salir del container
```
exit
```

Finalmente se detiene la red ejecutando.
```
./stop.sh
```




