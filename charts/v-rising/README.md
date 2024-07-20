# v-rising Helm Chart

This Helm chart provides default values for deploying the v-rising application. Below are the key configuration options:

| Configuration Key                  | Description                                                                                    | Default Value                   |
|------------------------------------|------------------------------------------------------------------------------------------------|---------------------------------|
| `replicaCount`                     | Number of replicas for the v-rising deployment.                                                | `1`                             |
| `image.repository`                 | Docker image repository for v-rising.                                                          | `ghcr.io/joaop221/v-rising-docker-arm64` |
| `image.pullPolicy`                 | Image pull policy for the v-rising container.                                                  | `IfNotPresent`                  |
| `image.tag`                        | Tag of the v-rising Docker image.                                                              | `v0.0.16`                       |
| `imagePullSecrets`                 | List of image pull secrets (empty in this case).                                               | `[]` (empty list)               |
| `nameOverride`                     | Override for the release name (empty in this case).                                            | `""` (empty string)             |
| `fullnameOverride`                 | Override for the full release name (empty in this case).                                       | `""` (empty string)             |
| `serviceAccount.create`            | Whether to create a service account.                                                           | `true`                          |
| `serviceAccount.annotations`       | Annotations to add to the service account (empty in this case).                                | `{}` (empty object)             |
| `serviceAccount.name`              | Name of the service account (empty in this case, auto-generated).                              | `""` (empty string)             |
| `podAnnotations`                   | Annotations to add to the pods (empty in this case).                                           | `{}` (empty object)             |
| `podSecurityContext`               | Pod security context.                                                                          | `{}` (empty object)             |
| `securityContext.allowPrivilegeEscalation` | Whether to allow privilege escalation for pods.                                        | `false`                         |
| `securityContext.capabilities.drop` | Capabilities to drop for the container.                                                       | `ALL`                           |
| `securityContext.runAsNonRoot`    | Whether to run the container as a non-root user.                                                | `true`                          |
| `securityContext.runAsGroup`      | Group ID for the container security context.                                                    | `1001`                          |
| `securityContext.runAsUser`       | User ID for the container security context.                                                     | `1001`                          |
| `securityContext.seccompProfile.type` | Seccomp profile type for the container.                                                     | `RuntimeDefault`                |
| `service.annotations`              | Annotations for the Kubernetes service (empty in this case).                                   | `{}` (empty object)             |
| `service.type`                     | Type of Kubernetes service for v-rising.                                                       | `ClusterIP`                     |
| `service.gamePort`                 | Port for the game service.                                                                     | `9876`                          |
| `service.queryPort`                | Port for the query service.                                                                    | `9877`                          |
| `ingressRoute.enabled`             | Whether to enable ingress routing.                                                             | `false`                         |
| `ingressRoute.nativeLB`            | Whether to use a native load balancer for ingress.                                             | `true`                          |
| `ingressRoute.entryPointNames`     | Entry points for the ingress (game and query).                                                 | `vrising` and `vrisingquery`    |
| `resources`                        | Compute resources used by pod.                                                                 | `vrising` and `vrisingquery`    |
| `persistence.enabled`              | Whether to enable persistence (data storage).                                                  | `true`                          |
| `persistence.existingClaim`        | Name of an existing persistent volume claim (empty in this case).                              | `""` (empty string)             |
| `persistence.storageClass`         | Storage class for persistent volume provisioning (empty in this case).                         | `""` (empty string)             |
| `persistence.accessMode`           | Access mode for the persistent volume.                                                         | `ReadWriteOnce`                 |
| `persistence.size`                 | Size of the persistent volume.                                                                 | `10Gi`                          |
| `config.TZ`                        | Timezone for the v-rising application.                                                         | `America/Sao_Paulo`             |
| `config.VR_NAME`                   | Name of the v-rising server.                                                                   | `V Rising Kubernetes`           |
| `config.VR_DIFFICULTY_PRESET`      | Difficulty preset for the game.                                                                | `Difficulty_Normal`             |
| `config.VR_MAX_USERS`              | Maximum number of users allowed.                                                               | `10`                            |
| `config.VR_FPS`                    | Frames per second for the game.                                                                | `30`                            |
| `config.VR_LOWER_FPS_WHEN_EMPTY`   | Whether to lower FPS when the server is empty.                                                 | `true`                          |
| `config.VR_LOWER_FPS_WHEN_EMPTY_VALUE` | FPS value when the server is empty.                                                        | `5`                             |
| `config.VR_LIST_ON_EOS`            | Whether to list the server on EOS.                                                             | `true`                          |
| `config.VR_LIST_ON_STEAM`          | Whether to list the server on Steam.                                                           | `true`                          |
| `config.VR_SAVE_NAME`              | Name for the saved game                                                                        | `world1`                        |
| `config.VR_SAVE_COUNT`             | Number of saved game slots.                                                                    | `1`                             |
| `config.VR_SAVE_INTERVAL`          | Interval (in seconds) for saving the game.                                                     | `300`                           |
| `secrets.VR_PASSWORD`              | Secret password for the v-rising server (empty in this case).                                  | `""` (empty string)             |
| `autoscaling.enabled`              | Whether to enable autoscaling.                                                                 | `false`                         |
| `autoscaling.minReplicas`          | Minimum number of replicas for autoscaling.                                                    | `1`                             |
| `autoscaling.maxReplicas`          | Maximum number of replicas for autoscaling.                                                    | `3`                             |
| `autoscaling.targetCPUUtilizationPercentage` | Target CPU utilization percentage for autoscaling.                                   | `80`                            |
| `autoscaling.targetMemoryUtilizationPercentage` | Target memory utilization percentage for autoscaling.                             | `80`                            |
| `nodeSelector`                     | Node selector for pod placement (empty in this case).                                          | `{}` (empty object)             |
| `tolerations`                      | Tolerations for pod scheduling (empty in this case).                                           | `[]` (empty list)               |
| `affinity`                         | Affinity rules for pod placement (empty in this case).                                         | `{}` (empty object)             |

For `config.VR_` and `/secrets.VR_` you can use any Environment Variable as specified at [V Rising Dedicated Server Instructions for v1.0.x](https://github.com/StunlockStudios/vrising-dedicated-server-instructions/blob/master/1.0.x/INSTRUCTIONS.md).

Feel free to adjust these values according to your specific deployment needs. If you have any further questions or need additional assistance, feel free to ask! 😊
