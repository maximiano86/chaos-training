# max-chaos-traning

1.- Create a namespace named chaos

    kubectl create namespace chaos

2.- Create 1st pod

    kubectl apply -f k8s/terminate-pods/pod.yaml

3.- Install k8s plugin

    pip3 install -U chaostoolkit-kubernetes

4.- Check what plugin can do:

    chaos discover chaostoolkit-kubernetes

    cat ./discovery.json

5.- Destroy pod

    cat chaos/terminate-pod.yaml

    chaos run chaos/terminate-pod.yaml

6.- Destroy pod stady state hypotesis (checks action before executing)

    chaos run chaos/terminate-pod-ssh.yaml
    
    kubectl apply -f k8s/terminate-pods/pod.yaml

    chaos run chaos/terminate-pod-ssh.yaml

7.- Pause steps to allow time to terminate a pod:

    kubectl apply -f k8s/terminate-pods/pod.yaml

    chaos run chaos/terminate-pod-pause.yaml

8.- Probes liveness/readiness:

    kubectl apply -f k8s/terminate-pods/pod.yaml

    chaos run chaos/terminate-pod-phase.yaml

    kubectl apply -f k8s/db

    kubectl go-demo-8 rollout deployment go-demo-8-db

    chaos run chaos/terminate-pod-phase.yaml

8.- Fault tolerante pod (deployment.yaml)

    kubectl apply -f k8s/terminate-pods/deployment.yaml

    chaos run chaos/terminate-pod-phase.yaml

