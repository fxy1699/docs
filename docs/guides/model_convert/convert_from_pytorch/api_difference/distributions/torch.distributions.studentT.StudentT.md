## [torch 参数更多 ]torch.distributions.studentT.StudentT

### [torch.distributions.studentT.StudentT](https://pytorch.org/docs/stable/distributions.html#studentt)

```python
torch.distributions.studentT.StudentT(df, loc=0.0, scale=1.0, validate_args=None)
```

### [paddle.distribution.StudentT](https://www.paddlepaddle.org.cn/documentation/docs/zh/api/paddle/distribution/StudentT_cn.html)

```python
paddle.distribution.StudentT(df, loc, scale, name=None)
```

PyTorch 相比 Paddle 支持更多其他参数，具体如下：

### 参数映射


| PyTorch       | PaddlePaddle | 备注                                                                                  |
| ------------- | ------------ | ------------------------------------------------------------------------------------- |
| df            | df           | 自由度，是一个正数。                                                                  |
| loc           | loc          | 分布的均值位置， Pytorch 中，可为 float 或 Tensor 类型，但在 Paddle 中， loc 应与 df 同类型。       |
| scale         | scale        | 分布的标准差的比例， Pytorch 中，可为 float 或 Tensor 类型，但在 Paddle 中， scale 应与 df 同类型。 |
| validate_args | -            | 是否添加验证环节。Paddle 无此参数，一般对训练结果影响不大，可直接删除。               |
| 返回值          | 返回值          | 当 df 为 Tensor 时，pytorch 返回值维度与 df 相同，而 Paddle 不同，需转写。                                  |

### 转写示例

#### 返回值

```python
# PyTorch 写法
y = torch.distributions.studentT.StudentT(df=torch.tensor(3), loc=0.0, scale=1.0).sample()

# Paddle 写法
x = paddle.to_tensor(3)
loc = paddle.to_tensor(0.0)
scale = paddle.to_tensor(1.0)
y = paddle.distribution.StudentT(df=x, loc=loc, scale=scale).sample()
y = paddle.reshape(y, x.shape)
```
