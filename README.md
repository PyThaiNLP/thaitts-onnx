# thaitts-onnx
Thai Text-to-speech by ONNX runtime

Google colab: [https://colab.research.google.com/github/PyThaiNLP/thaitts-onnx/blob/main/demo.ipynb](https://colab.research.google.com/github/PyThaiNLP/thaitts-onnx/blob/main/demo.ipynb)


Today, Thai Text-to-speech doesn't have any onnx model for onnxruntime. We use TTS model from [lunarlist/tts-thai-last-step](https://huggingface.co/lunarlist/tts-thai-last-step) but the model is lockout that needs has NeMo (and NeMo doesn't support [export Tacotron2 to ONNX model since 2020](https://github.com/NVIDIA/NeMo/issues/531)). We found the way to export Thai TTS model to ONNX model. It will create the way to use Thai TTS model in many devices.

## How to export

We use the patch from [#7366 at NVIDIA/NeMo](https://github.com/NVIDIA/NeMo/pull/7466) and fixed a bug in the patch.

### Install

```sh
pip install -r https://github.com/RobinDong/NeMo/raw/add_onnx_export/requirements/requirements_tts.txt
pip install hydra-core
pip install pytorch-lightning==1.9.5
pip install youtokentome webdataset
pip install pyannote.audio
pip install pytorch-lightning==2.0.9
```

### Export

Run onnx-export.ipynb and vocoder-export.ipynb.

You will found the patch has a bug. It is wrong for setting high number at the line 100 in https://github.com/RobinDong/NeMo/blob/0113c8268594fa0e61901409235ff33ea5d39beb/nemo/collections/tts/models/tacotron2.py#L98 (Path: /usr/local/lib/python3.10/dist-packages/nemo/collections/tts/models/tacotron2.py) and fixed by config high number https://github.com/PyThaiNLP/thaitts-onnx/blob/main/tacotron2.py#L100.
