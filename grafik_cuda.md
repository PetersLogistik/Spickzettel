# Nutzbarmachung der Grfischen Schnittstelle 
## Vorwort/ requirements ##
Zum Nutzen der Schnittstelle der Grafikkarte sind folgende Installationen vorzunehemen:

CUDA Toolkit. Ich nutze es in der Version 11.6. Zur Versionspprüfung `nvcc --version` nutzen. [https://developer.nvidia.com/cuda-toolkit-archive](https://developer.nvidia.com/cuda-toolkit-archive "CUDA Toolkit") 

Python nutze ich in der Version 3.11. Welche Version auf dem Pc bereits installiert ist kann hierüber ermittelt werden: `python --version` [https://www.python.org/downloads/](https://www.python.org/downloads/ "Python") 

Für weitergehende Programmierer: [https://developer.nvidia.com/nvidia-nsight-visual-studio-edition](https://developer.nvidia.com/nvidia-nsight-visual-studio-edition "NVIDIA Nsight Visual Studio Edition")

Ziel des Vorganges ist speziell für OpenTrafficCam die Schnittstelle der Grafikkarte zur beschleunigten Bildverarbeitung zu nutzen.

Für weitergehende Programmierer: [https://developer.nvidia.com/nvidia-nsight-visual-studio-edition](https://developer.nvidia.com/nvidia-nsight-visual-studio-edition "NVIDIA Nsight Visual Studio Edition")

Ziel des Vorganges ist speziell für OpenTrafficCam die Schnittstelle der Grafikkarte zur beschleunigten Bildverarbeitung zu nutzen.

<h3>Voraussetzungen für GPU-Beschleunigung</h3>
<h5>Kompatible GPU-Hardware:</h5>

- NVIDIA-GPU: Die meisten ML-Frameworks (z. B. TensorFlow, PyTorch) unterstützen CUDA, das nur mit NVIDIA-GPUs funktioniert. 
- AMD-GPUs oder andere Marken werden oft nicht unterstützt.
<br>
<h5>Installierte GPU-Treiber:</h5>
Stelle sicher, dass der neueste NVIDIA-Treiber installiert ist:

    nvidia-smi

Dieser Befehl zeigt Informationen zu deiner GPU und ihrer aktuellen Nutzung:
![cmd_Psre1orIG4.png](./grafik/cmd_Psre1orIG4.png)
<br>
<h5>Framework-Unterstützung:</h5>
OpenTrafficCam verwendet Frameworks wie TensorFlow oder PyTorch. Stelle sicher, dass du die GPU-Version des Frameworks installiert hast:

    pip install tensorflow-gpu
    # oder für PyTorch
    pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cuXX
    # (ersetze "cuXX" durch deine CUDA-Version, z. B. cu118 für CUDA 11.8)
<br>
Folgende install-Befehle haben ohne Fehlermeldung bei mir funktioniert:

    pip install tensorflow
    pip install torch

<h5>Ursachen für CPU-Nutzung statt GPU</h5>
- GPU wird nicht erkannt

    import tensorflow as tf
    print("GPU available:", tf.config.list_physical_devices('GPU'))

    import torch
    print("GPU available:", torch.cuda.is_available())

- Falsche Framework-Version
- Fehlende CUDA-Unterstützung
- Konfiguration des Tools:
    OpenTrafficCam könnte explizit so eingestellt sein, dass die CPU genutzt wird. Überprüfe die Konfigurationsdateien oder den Code, ob es eine Einstellung wie `use_gpu` gibt, die aktiviert werden muss.

Wenn sich keine Lösung abzeichnet, alles einmal updaten und PC neustarten.