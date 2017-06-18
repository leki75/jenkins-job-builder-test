### Prerequisites

* python3
* docker
* docker-compose


### Installation

```
python3 -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt
docker-compose up -d
```

Do not forget to set user and password in jenkins_jobs.ini file.
https://docs.openstack.org/infra/jenkins-job-builder/execution.html
