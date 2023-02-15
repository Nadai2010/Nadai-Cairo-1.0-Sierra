 A diferencia de los contratos 0.x, donde compilamos directamente a ensamblador Cairo (casm), con Cairo 1.0, la compilación de nuestros contratos se hará en dos etapas:

1. Cairo > Sierra
2. Sierra > Casm

Sierra significa Safe Intermediate Representation (Representación Intermedia Segura) y pretende constituir una capa de representación entre los programas Cairo y sus bytecodes. Sierra abre la posibilidad de probar cada ejecución de Cairo, permitiendo así una robusta protección contra ataques de Denegación de Servicio (DoS).

En este caso nos centraremos en dos contratos, [ERC20.cairo](src/ERC20.cairo) y [ENS.cairo](src/ens.cairo)

Para compilar a Sierra, ejecute el siguiente comando:

```bash
cargo run --bin starknet-compile -- src/ERC20.cairo src/ERC20.sierra --replace-ids
```

![Graph](imágenes/erc20si.png)

Si la compilación fue exitosa, debería ver la salida de Sierra en su src/ERC20.sierra.

![Graph](imágenes/erc20si2.png)

Para seguir compilando de Sierra a Casm, ejecute el siguiente comando:

```bash
cargo run --bin starknet-sierra-compile -- src/ERC20.sierra src/ERC20.casm
```

![Graph](imágenes/hellocasm.png)

Si la compilación fue exitosa, deberías ver la salida casm en tu src/hello.casm.

![Graph](imágenes/helloscasm2.png)

---

Después de conseguir compilar ERC20.cairo a Sierra y a Casm, podemos probar con ens.cairo

Para compilar a Sierra, ejecute el siguiente comando:

```bash
cargo run --bin starknet-compile -- src/ens.cairo src/ens.sierra --replace-ids
```

![Graph](imágenes/enssi.png)

Si la compilación fue exitosa, debería ver la salida de Sierra en su src/ens.sierra.

![Graph](imágenes/enssi2.png)

Para seguir compilando de Sierra a Casm, ejecute el siguiente comando:

```bash
cargo run --bin starknet-sierra-compile -- src/ens.sierra src/ens.casm
```

![Graph](imágenes/enscasm.png)

Si la compilación fue exitosa, deberías ver la salida casm en tu src/ens.casm.

![Graph](imágenes/enscasm2.png)




 


