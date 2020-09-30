# Simple-Chat-Program
Share data between docker containers using serial ports (proof of concept).

1) Create a pair of virtual COM ports using com0com.
2) Build the images of Bob and Alice:
```sh
docker build -t bob .
docker build -t alice .
```
3) Run the containers with "device" flag (who indicate Interface Class GUID):
```sh
docker run --rm -ti --isolation=process --device="class/86E0D1E0-8089-11D0-9CE4-08003E301F73" bob
docker run --rm -ti --isolation=process --device="class/86E0D1E0-8089-11D0-9CE4-08003E301F73" alice
```


| Device Type | Interface Class GUID |
| ------ | ------ |
| GPIO | 916EF1CB-8426-468D-A6F7-9AE8076881B3 |
| I2C Bus | A11EE3C6-8421-4202-A3E7-B91FF90188E4 |
| COM Port | 86E0D1E0-8089-11D0-9CE4-08003E301F73 |
| SPI Bus | DCDE6AF9-6610-4285-828F-CAAF78C424CC |
| DirectX GPU Acceleration | [See GPU acceleration docs][direckLink] |


[direckLink]: <https://docs.microsoft.com/virtualization/windowscontainers/deploy-containers/gpu-acceleration>
