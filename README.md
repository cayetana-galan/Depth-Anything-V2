**Project**

Repository: https://github.com/DepthAnything/Depth-Anything-V2

Inference task: Monocular depth estimation

**Repo map**

Environment: requirements.txt

Entry point: run.py

Model:  DepthAnythingV2 need to be download 

Input: photo.jpg

Output: depth_vis/

**Environment setup**
```text
git clone https://github.com/DepthAnything/Depth-Anything-V2
cd Depth-Anything-V2
uv python install 3.10
uv venv --python 3.10
source .venv/bin/activate
uv pip install -r requirements.txt
```

**Inference** 
```text
python run.py \
  --encoder vits \
  --img-path /home/s5915807/Desktop/workshop02_projects/Depth-Anything-V2/depth_anything_v2/images/london.jpg \
  --outdir /home/s5915807/Desktop/workshop02_projects/Depth-Anything-V2/depth_anything_v2/images/ \
  --input-size 518 \
  --pred-only \
  --grayscale
```

**One real failure**

Category: Version conflict

Root cause: the full declared dependency set is not resolvable for Python 3.8 because the optional export extra includes keras>=3.5.0,<=3.12.0, which requires Python >=3.9 / >=3.10 depending on version. So the effective minimum for the full dependency set is Python 3.9+, while the repo metadata still says >=3.8.

Minimal fix: change to Python 3.10

**AI agent check**

Which AI coding agent did you use?: copilot

What did it change?: only venv python version

How did you verify the change?: I asked it to do this