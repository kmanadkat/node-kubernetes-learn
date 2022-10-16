# Overview

This is a very simple, bare-bones NodeJS project created for you to use with Docker.

### EKS Setup On AWS Steps
0. Prerequisites - Install [Kubetctl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html) & [aws-iam authenticator](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html), IAM user with Administrator access

1. Create IAM Role For [EKS-Cluster](https://docs.aws.amazon.com/eks/latest/userguide/service_IAM_role.html) from Administrator account (not root)

2. Create IAM Role for [Nodes](https://docs.aws.amazon.com/eks/latest/userguide/create-node-role.html#create-worker-node-role) from Administrator account (not root)

   > Attach `AmazonEKS_CNI_Policy` to the role.

3. Create Cluster on AWS EKS from administrator account

   - Use default VPC & Subnets
   - Donot link existing security group (default), instead aws will create dedicated security group
   - Allow public access.
   - Add Node Group > t3.micro > max & min nodes > default subnets
   - Enable SSH > Allow SSH for All

4. [Create kubeconfig file](https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html) automatically

5. Link `deployment.yaml` & `service.yaml`
   ```shell
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   ```

6. Fetch Pods information with 
   `kubectl get pods` 
   `kubectl describe services`

7. Fetch Logs from pods
   `kubectl logs <pod-id>`