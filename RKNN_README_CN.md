# 导出 RKNPU2 适配模型说明

## Source

​本仓库基于 https://github.com/ChaoningZhang/MobileSAM 仓库的 c12dd83cbe26dffdcc6a0f9e7be2f6fb024df0ed commit 进行修改,验证.


## 模型差异

在不影响输出结果, 不需要重新训练模型的条件下, 有以下改动:

- 为优化推理速度，encoder模型输出尺寸修改为[1, 3, 448, 448](修改 `mobile_sam/build_sam.py`和`mobile_sam/modeling/tiny_vit_sam.py`)


## 导出onnx模型

在满足`MobileSAM`原仓库中导出模型的安装环境后，执行以下语句导出模型

``` sh
python scripts/export_onnx_model.py --checkpoint ./weights/mobile_sam.pt --model-type vit_t --output ./mobilesam_decoder.onnx

# checkpoint 为原始模型文件
# model-type 为encoder模型类型
# output 为decoder模型输出路径
# 执行完毕后，会生成 mobilesam_encoder.onnx和mobilesam_decoder.onnx模型.
```

## 转RKNN模型、Python demo、C demo

请参考 https://github.com/airockchip/rknn_model_zoo

