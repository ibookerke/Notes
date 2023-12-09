
fc layers usually comes after [[Conv Layer]]s and [[Pooling layer]]s that in the following manner:
![[Pasted image 20230927082925.png]]
After [[Pooling layer]] the images are flattened into one-dimensonal array, which will be used as an input to the fully connected layers. 
Called fully connected because they are fully connected to inputs and to the next fully connected layers.

Also the number of the of outputs on the last fully connected layer will always have a number of outputs equal to the number of classes the model trying to identify(if model tries to identify 3 images -> there will be 3 outputs)
Also for last layer we are using the [[SoftMax]]

