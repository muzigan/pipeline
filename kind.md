set HTTP_PROXY=http://185.46.212.34:10015
set HTTPS_PROXY=http://185.46.212.34:10015
set NO_PROXY=130.147.217.0/24


curl https://api.github.com/repos/openshift-pipelines/pipelines-as-code/releases/latest  -vvv
oc get pods -A 
tkn-pac bootstrap
oc edit deploy gosmee (add env HTTPS_PORXY)