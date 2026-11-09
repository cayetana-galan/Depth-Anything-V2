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
cd /home/s5908297/workshop02_projects/Depth-Anything-V2

```text
python run.py \
  --encoder vits \
  --img-path /home/s5908297/workshop02_projects/Depth-Anything-V2/depth_anything_v2/images/london.jpg \
  --outdir /home/s5908297/workshop02_projects/Depth-Anything-V2/depth_vis \
  --input-size 518 \
  --pred-only \
  --grayscale
```
cd /home/s5908297/workshop02_projects/Depth-Anything-V2/depth_vis
cd depth_vis/london.png


**One real failure**

Category: Version conflict

Root cause: the full declared dependency set is not resolvable for Python 3.8 because the optional export extra includes keras>=3.5.0,<=3.12.0, which requires Python >=3.9 / >=3.10 depending on version. So the effective minimum for the full dependency set is Python 3.9+, while the repo metadata still says >=3.8.

Minimal fix: change to Python 3.10

**AI agent check**

Which AI coding agent did you use?: copilot

What did it change?: only venv python version

How did you verify the change?: I asked it to do this

**One real failure**

Category: Output path

Root cause: if the input is london.jpg and --outdir is the same folder as the image, the result becomes london.png in that same folder, not a failure. The issue is that the user expected the original file to be replaced or the app to fail when output is written alongside the input.

Minimal fix: Save results to a separate output folder, such as depth_vis, and keep the original image in place

**AI agent check**

Which AI coding agent did you use?: copilot

What did it change?: Confirmed the project behavior by reading run.py:39-73 and explained that the script saves a new PNG using the same file stem in --outdir, rather than modifying the original source file.

How did you verify the change?: I asked it to do this

