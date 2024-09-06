# RKNN optimization for exporting model

## Source
Base on https://github.com/ChaoningZhang/MobileSAM with commit id as c12dd83cbe26dffdcc6a0f9e7be2f6fb024df0ed


## What different
With inference result values unchanged, the following optimizations were applied:

- To optimize inference speed, the encoder model's output size has been changed to [1, 3, 448, 448]. (Modify `mobile_sam/build_sam.py` and `mobile_sam/modeling/tiny_vit_sam.py`).


## Export ONNX model

After meeting the installation environment requirements in the original `MobileSAM` repository for exporting the model, execute the following command to export the model:


``` sh
python scripts/export_onnx_model.py --checkpoint ./weights/mobile_sam.pt --model-type vit_t --output ./mobilesam_decoder.onnx

# checkpoint refers to the original model file
# model-type refers to the type of the encoder model
# output refers to the path where the decoder model will be saved
After execution, the models mobilesam_encoder.onnx and mobilesam_decoder.onnx will be generated.
```

## Convert to RKNN model, Python demo, C demo

Please refer to https://github.com/airockchip/rknn_model_zoo.
