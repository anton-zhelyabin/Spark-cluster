# Локальный Spark кластер
## О проекте
В этом репозитории приведён алгоритм по развёртыванию кластера Greenplum на выиртуальных машинах.

### Клонирование роепозитория
```
git clone git@github.com:anton-zhelyabin/Spark-cluster.git
```
### Загрузка датасета
датасет устанавливается с помощью curl.
```
cd Spark-cluster/build/workspace && \
mkdir -p data && \
curl -L -o data/uk-housing-prices-paid.zip \
  https://www.kaggle.com/api/v1/datasets/download/hm-land-registry/uk-housing-prices-paid

# распаковываем архив
unzip data/uk-housing-prices-paid.zip -d data/ && rm data/uk-housing-prices-paid.zip
cd ~/Spark-cluster
```
### Перед развёртыванием spark'а необходимо (следующие команды предназначены для Linux):
1. Установить Java 11+ и настроить переменную среды JAVA_HOME
```
sudo apt install -y openjdk-11-jdk

# Находим путь к Java
update-java-alternatives -l

# Обычно путь такой (для OpenJDK 11):
# /usr/lib/jvm/java-11-openjdk-amd64

# Добавляем в ~/.bashrc
echo 'export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc

# Применяем изменения
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
### Запускаем Spark кластер
Запускаем docker compose
```
docker compose up -d
```
Запускаем Jupyter
```
jupyter lab
```
Ноутбук с задачами здесь
- [Spark Notebook](https://github.com/anton-zhelyabin/Spark-cluster/blob/main/build/workspace/spark.ipynb)



