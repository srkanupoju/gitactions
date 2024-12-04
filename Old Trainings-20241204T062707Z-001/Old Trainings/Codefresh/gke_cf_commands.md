
# In IAM user add role Kubernetes Admin for current user.

# Open gcloud cluster cli 

$ kubectl apply -f codefresh-role-sa-bind.yml

$ export CURRENT_CONTEXT=$(kubectl config current-context) && export CURRENT_CLUSTER=$(kubectl config view -o go-template="{{\$curr_context := \"$CURRENT_CONTEXT\" }}{{range .contexts}}{{if eq .name \$curr_context}}{{.context.cluster}}{{end}}{{end}}") && echo $(kubectl config view -o go-template="{{\$cluster_context := \"$CURRENT_CLUSTER\"}}{{range .clusters}}{{if eq .name \$cluster_context}}{{.cluster.server}}{{end}}{{end}}")

$ echo $(kubectl get secret -n codefresh-system -o go-template='{{index .data "ca.crt" }}' codefresh-user-token)

$ echo $(kubectl get secret -n codefresh-system -o go-template='{{index .data "token" }}' codefresh-user-token)