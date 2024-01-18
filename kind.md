set HTTP_PROXY=http://185.46.212.34:10015
set HTTPS_PROXY=http://185.46.212.34:10015
set NO_PROXY=130.147.217.0/24



export HTTP_PROXY=http://185.46.212.34:10015
export HTTPS_PROXY=http://185.46.212.34:10015
export NO_PROXY=130.147.217.0/24


curl https://api.github.com/repos/openshift-pipelines/pipelines-as-code/releases/latest  -vvv
oc get pods -A 
tkn-pac bootstrap
oc -n pipelines-as-code edit deploy gosmee (add env HTTPS_PORXY)

      - env:
        - name: HTTPS_PROXY
          value: http://185.46.212.34:10015

oc -n pipelines-as-code edit deployment/pipelines-as-code-controller K_SINK_TIMEOUT=300 
oc -n pipelines-as-code edit deploy gosmee


kubectl -n pipelines-as-code logs -f  gosmee-7dd68dcff6-xhd45 & 
kubectl -n pipelines-as-code logs -f  pipelines-as-code-controller-f7f4c8bd6-hkd2d &
kubectl -n pipelines-as-code logs -f pipelines-as-code-watcher-86d9c59dbb-x9cv4 &
kubectl -n pipelines-as-code logs -f pipelines-as-code-webhook-7b676c75d6-2vl7f & 
