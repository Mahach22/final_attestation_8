# final_attestation_8




helm install airflow apache-airflow/airflow \
--debug \
--namespace airflow \
--create-namespace \
--set dags.gitSync.enabled=true \
--set dags.gitSync.repo=https://github.com/Mahach22/final_attestation_8.git \
--set dags.gitSync.branch=main \
--set dags.gitSync.subPath="/"



kubectl port-forward svc/airflow-webserver 8888:8080 --namespace airflow
