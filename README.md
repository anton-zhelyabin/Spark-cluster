# Локальный Spark кластер
## О проекте
В этом репозитории приведён алгоритм по развёртыванию кластера Greenplum на выиртуальных машинах.

### Перед развёртыванием spark'а необходимо (следующие команды предназначены для Linux):
1. Установить Java 11+ и настроить переменную среды JAVA_HOME
```
sudo apt install -y openjdk-11-jdk

\# Находим путь к Java
update-java-alternatives -l

\# Обычно путь такой (для OpenJDK 11):
\# /usr/lib/jvm/java-11-openjdk-amd64

\# Добавляем в ~/.bashrc
echo 'export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc

\# Применяем изменения
source ~/.bashrc
```
2. Установить pyspark и Jupyter Lab, для Jupyter
```
pip install pyspark jupyterlab

# Добавляем путь Jupyter в ~/.bashrc
echo 'export PATH=$HOME/.local/bin:$PATH' >> ~/.bashrc

# Применяем изменения
source ~/.bashrc
```

### Загрузка датасета
датасет устанавливается с помощью curl.
```
curl -L -o ~/Downloads/uk-housing-prices-paid.zip\
  https://www.kaggle.com/api/v1/datasets/download/hm-land-registry/uk-housing-prices-paid
```
