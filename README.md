# airflow-sensors-project

![arquitetura-projeto-final](https://github.com/thyagomanhaes/airflow-sensors-project/assets/5121307/39c8180e-13b3-4cf7-880c-e1e08a0773cc)

Os dados são gerados em arquivo JSON


File_sensor_task: 
- Verifica o arquivo em intervalos regulares
- Não monitora a pasta indefinitivamente
- Não inicializa a DAG quando o arquivo for disponibilizado
- Não tem conhecimento das eecuções anteriores da DAG

PythonOperator: 
- Deverá ler o JSON
- Colocar as 5 variáveis no Xcom
- Excluir o arquivo

BranchPythonOperator: 
- Se a temperatura for >= 24 graus manda e-mail de alerta
- Senão, manda um e-mail informativo

PostgresOperator:
- Cria a tabela
- Insere os dados

Pré-condições:
- Criar conexões para file_sensor_task
- Criar variável com caminho do arquivo
