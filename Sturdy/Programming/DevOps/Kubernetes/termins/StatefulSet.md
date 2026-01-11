k8s component needed for stateful applications.
Basically making sure that database reads and writes are synchronized.
Just like [[Deployment]] - it'a blueprint for [[Pod]]s, but for stateful apps and databases.

## Description

Commonly in k8s there is a need to replicate [[Pod]]s and we are managing it with the [[Deployment]].
However, we cannot replicate databases with [[Deployment]] since databases are stateful and there is a need to control which [[Pod]] is reading or writing to the storage to avoid data inconsistencies. And this need is being covered with the StatefulSet.

