# 3-tier-application
This repository contains code for a 3 tier architecture. It uses terraform to create Infra over AWS cloud and deploys a basic nginx server on proxy and a node app on Application servers.

Challenge 1:

To run:

./run.sh -e <ENVIRONMENT_NAME> --confirmation yes --<TERRAFORM_OPERATION>

If we pass --confirmation yes parameter then terraform will not ask before applying or destroying environment

Possible commands:
./run.sh -e dev --confirmation yes --plan
./run.sh -e dev --confirmation yes --apply
./run.sh -e dev --confirmation yes --destroy


Database connection can be tested using below commands
1 Create tunnel:
ssh -o StrictHostKeyChecking=no -M -S db-deploy-socket -fnNT -L 3306:DB_HOST:3306 ubuntu@<BASTION_IP> -i /home/chaitali/chaitali-kanetkar/task-1/configs/dev/dev_deploy_key

2 Connect with DB:
mysql -D chaitali -h 127.0.0.1  -P 3306 -u codiats  --password=chaitali123$

3 Exit tunnel
ssh -o StrictHostKeyChecking=no -S db-deploy-socket -O exit ubuntu@<BASTION_IP>
