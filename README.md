### Используя исходники лабораторной работы номер 6.

```bash
$ mkdir -p cmake
$ wget https://raw.githubusercontent.com/cpp-pm/gate/master/cmake/HunterGate.cmake -O cmake/HunterGate.cmake
$ gsed -i '/cmake_minimum_required(VERSION 3.4)/a\

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/cpp-pm/hunter/archive/v0.23.251.tar.gz"
    SHA1 "5659b15dc0884d4b03dbd95710e6a1fa0fc3258d"
)
' CMakeLists.txt
```

```bash
vim CMakeLists.txt
```
```cmake
cat hunter.cmake                                                        ─╯
include(hunter_add_version)
include(hunter_cacheable)
include(hunter_download)
include(hunter_pick_scheme)
hunter_add_version(
	PACKAGE_NAME
	banking
	VERSION
	1.0.0
	URL
	"https://github.com/sk3pta/lab05/archive/refs/tags/v1.0.0.tar.gz"
	SHA1
	4efa7f02b08548183457c99d8af6fb79a1391a77
)


hunter_pick_scheme(DEFAULT url_sha1_cmake)
hunter_cacheable(hunter_box_1)
hunter_download(PACKAGE_NAME hunter_box_1)



```

## 1. Необходимо сделать форк исходного репозитория hunter. Далее редактируем hunter.cmake 
### Предварительно создаем релиз нашего проекта (lab07), и посчитать его хэш SHA1

```bash 
wget https://github.com/sk3pta/lab05/archive/refs/tags/v1.0.0.tar.gz 

openssl sha1 v1.0.0.tar.gz 
```


```bash
vim hunter.cmake
```

```cmake
                                                      ─╯
include(hunter_add_version)
include(hunter_cacheable)
include(hunter_download)
include(hunter_pick_scheme)
hunter_add_version(
	PACKAGE_NAME
	banking
	VERSION
	1.0.0
	URL
	"https://github.com/sk3pta/lab05/archive/refs/tags/v1.0.0.tar.gz"
	SHA1
	4efa7f02b08548183457c99d8af6fb79a1391a77
)


hunter_pick_scheme(DEFAULT url_sha1_cmake)
hunter_cacheable(hunter_box_1)
hunter_download(PACKAGE_NAME hunter_box_1)
```


## Далее,hunter пакет готов. Остаётся сделать pull request в исходный репозиторий hunter
