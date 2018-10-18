# OpenSlava 2018
See the PDF  [FUGARO_OPENSLAVA2018-last](FUGARO_OPENSLAVA2018-last.pdf)

# Create Projects
./oc new-project dev --display-name="Tasks - Dev"
./oc new-project stage --display-name="Tasks - Stage"
./oc new-project cicd --display-name="CI/CD"

# Grant Jenkins Access to Projects
./oc policy add-role-to-group edit system:serviceaccounts:cicd -n dev
./oc policy add-role-to-group edit system:serviceaccounts:cicd -n stage

# Deploy Demo
./oc new-app -n cicd -f cicd-template.yaml

# Deploy Demo with Eclipse Che
./oc new-app -n cicd -f cicd-template.yaml --param=DEPLOY_CHE=true
./oc new-app -n cicd -f cicd-template.yaml --param DEV_PROJECT=dev-project-name --param STAGE_PROJECT=stage-project-name


