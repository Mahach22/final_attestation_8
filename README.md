**Данный проект создан в рамках выполнения итогового задания № 8**

**Задание 8. Развертывание Apache Airflow в Minikube и создание простого DAG**
Цель: Научиться разворачивать Apache Airflow в Kubernetes с использованием Minikube и создавать простой Directed Acyclic Graph (DAG) для автоматизации задач.

**Описание задания:**
* Запустите Minikube с достаточными ресурсами.
* Установите Helm, если он еще не установлен.
* Добавьте репозиторий Apache Airflow.
* Создайте пространство имен для Airflow.
* Используем Helm для развертывания Airflow с базовыми настройками.
* Получите URL для доступа к веб-интерфейсу Airflow.
* Создайте DAG и подложите его в git (как это показывалось в лекционном материале).
*  В DAG создайте 2 любых оператора. Запуск DAG — ежедневный в 12:45 по Москве.

В качестве решения необходимо сделать отчет, в котором видно Ваш DAG в git, а также видно DAG в Airflow. Обязательно сделайте скрин вашего DAG в работе, что он отбежал.<br>
Результат задания — после выполнения задания у вас будет развернутая в Minikube среда Apache Airflow, где вы сможете создавать и управлять DAG для автоматизации задач.


**Выполнение задания:**
Ранее Minikube и Helm были установлены, а также добавлен репозиторий Apache Airflow.

Установил Airflow в пространстве airflow, указав репозиторий с нашим DAG
```
helm install airflow apache-airflow/airflow \
--debug \
--namespace airflow \
--create-namespace \
--set dags.gitSync.enabled=true \
--set dags.gitSync.repo=https://github.com/Mahach22/final_attestation_8.git \
--set dags.gitSync.branch=main \
--set dags.gitSync.subPath="/"
```

```
kubectl port-forward svc/airflow-webserver 8888:8080 --namespace airflow
```
