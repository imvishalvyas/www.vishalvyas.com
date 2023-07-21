**Error** : 

`Warning    FailedMount    35 minutes ago    kubelet    Unable to attach or mount volumes: unmounted volumes=[data], unattached volumes=[kube-api-access-zv4 configuration data]: timed out waiting for the condition`

`Warning    FailedAttachVolume    5 minutes ago    attachdetach-controller    AttachVolume.Attach failed for volume "pvc-7091b8b4-407e-b695-9909fa106fda" : timed out waiting for external-attacher of ebs.csi.aws.com CSI driver to attach volume vol-8d326adf6d`


This error occurs when no Add-ons for `Amazon EBS CSI Driver` are installed. If you have already installed 'Amazon EBS CSI Driver' and it is in a degraded state, you must upgrade that Add-on. If you have not installed the Amazon EBS CSI Driver Add-On, you must install it. Navigate to the `EKS kubernetes cluster > Add-ons` and update the Amazon EBS CSI Drive.
