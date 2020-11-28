## 一个一次函数的拟合

```python
import tensorflow as tf
import numpy as np

#creat data
x_data = np.random.rand(100).astype(np.float32)
y_data = x_data*0.1+0.3

#
Weights = tf.Variable(tf.random_uniform([1],-1.0,1.0))
baises = tf.Variable(tf.zeros([1]))

y = Weights*x_data+baises;

loss = tf.reduce_mean(tf.square(y-y_data))
optimizer = tf.train.GradientDescentOptimizer(0.5)
train = optimizer.minimize(loss)

init = tf.initialize_all_variables()

sess = tf.Session()
sess.run(init)

for step in range(201):
    sess.run(train)
    if step%20 ==0:
        print(step,sess.run(Weights),sess.run(baises))

0 [0.5643553] [0.06086658]
20 [0.23667549] [0.22587171]
40 [0.1406953] [0.2779282]
60 [0.11211708] [0.2934281]
80 [0.10360787] [0.29804322]
100 [0.10107425] [0.29941738]
120 [0.10031987] [0.29982653]
140 [0.10009526] [0.29994833]
160 [0.10002838] [0.29998463]
180 [0.10000844] [0.29999542]
200 [0.10000252] [0.29999864]
```

