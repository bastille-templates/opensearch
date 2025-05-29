# Opensearch
Opensearch is a fork of Elasticsearch that functions as a database/NoSQL with a focus on search engine databases.

## Now apply template to container
Include:
- Opensearch
- Logstash&Filebeats
- Opensearch-Dashboards
```sh
git clone https://github.com/bastille-templates/opensearch.git; cd opensearch

J_IP=172.16.1.10
J_NAME=opensearch
FBSD_R=14.2-RELEASE
bastille create ${J_NAME} ${FBSD_R} ${J_IP}
J_PATH="/usr/local/bastille/jails/${J_NAME}"
cp jail.conf ${J_PATH}/
sed -e "s,%%SERVER_NAME%%,${J_NAME},g" -i "" ${J_PATH}/jail.conf
sed -e "s,%%RELEASE%%,${FBSD_R},g" -i "" ${J_PATH}/jail.conf
sed -e "s,%%SERVER_IP%%,${J_IP},g" -i "" ${J_PATH}/jail.conf
cp rdr.conf ${J_PATH}/

bastille stop opensearch; bastille start opensearch

bastille bootstrap https://github.com/bastille-templates/opensearch
bastille template opensearch bastille-templates/opensearch
bastille pkg opensearch info -D -x opensearch | less
```
test
```sh
curl https://your.host.address:9200 -u admin:yournewpassword -k
```

## License
This project is licensed under the BSD-3-Clause license.