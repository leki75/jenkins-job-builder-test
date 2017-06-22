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

### Post installation steps
1. Jenkins
* Manage User -> Create User
    ** create jjb user (jenkins-job-builder)
* Configure Global Security -> Access Control -> Matrix-based security
    ** add full access to admin user
    ** add Overall Read, Job Configure, Job Create, Job Delete and Job Read access for jjb user
* People -> jjb -> Configure
    ** log in as jjb user and write down API Token
* Configure Global Security -> Access Control -> Crumbs -> Enable proxy compatibility
    ** set crumb check more permissive (access with 127.0.0.1 and localhost)

2. Gerrit
* create zuul user
```
cat zuul/ssh/id_rsa.pub | ssh -l <AdminUser> -p 29418 localhost gerrit create-account zuul \
    --email zuul@examle.com \
    --full-name "Zuul\ daemon" \
    --group "Non-Interactive\ Users" \
    --ssh-key -
```

Do not forget to set user and password in jenkins_jobs.ini file.
https://docs.openstack.org/infra/jenkins-job-builder/execution.html
