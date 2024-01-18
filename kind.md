set HTTP_PROXY=http://185.46.212.34:10015
set HTTPS_PROXY=http://185.46.212.34:10015
set NO_PROXY=130.147.217.0/24


curl https://api.github.com/repos/openshift-pipelines/pipelines-as-code/releases/latest  -vvv
oc get pods -A 
tkn-pac bootstrap
oc edit deploy gosmee (add env HTTPS_PORXY)

      - env:
        - name: HTTPS_PROXY
          value: http://185.46.212.34:10015
 oc -n pipelines-as-code edit deploy  pipelines-as-code-controller
      dnsConfig:
        nameservers:
        - 130.147.249.32
        - 130.147.236.5
        - 161.92.35.78

edit deployment/pipelines-as-code-controller K_SINK_TIMEOUT=300 


kubectl -n pipelines-as-code logs -f gosmee-7dd68dcff6-7ct5b & 
kubectl -n pipelines-as-code logs -f   pipelines-as-code-controller-59b759b87c-rt6p4 &
kubectl -n pipelines-as-code logs -f pipelines-as-code-watcher-86d9c59dbb-fw77g &
kubectl -n pipelines-as-code logs -f pipelines-as-code-webhook-7b676c75d6-l5fsh & 
