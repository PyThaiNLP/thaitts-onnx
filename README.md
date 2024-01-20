# thaitts-onnx
Thai Text-to-speech by ONNX runtime

Today, Thai Text-to-speech doesn't have any onnx model for onnxruntime. We use TTS model from [lunarlist/tts-thai-last-step](https://huggingface.co/lunarlist/tts-thai-last-step) but the model is lockout that needs has NeMo (and NeMo doesn't support [export Tacotron2 to ONNX model since 2020](https://github.com/NVIDIA/NeMo/issues/531)). We found the way to export Thai TTS model to ONNX model. It will create the way to use Thai TTS model in many devices.
