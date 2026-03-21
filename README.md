# scBERT
conda create -n scbert python=3.7 -y
conda activate scbert

conda install -y \
  numpy=1.20 \
  pandas=1.1.5 \
  scikit-learn=0.24.2 \
  matplotlib=3.5 \
  scanpy=1.7.2 \
  anndata=0.7.6

pip install scipy==1.5.4
pip install torch==1.8.1
pip install torchvision==0.9.1
pip install transformers==4.6.1
pip install einops==0.6.0

conda install -c conda-forge libtiff=4.2.0 -y

pip uninstall -y pillow
pip install pillow==9.4.0

pip uninstall -y get-version legacy-api-wrap
pip install legacy-api-wrap==1.2 get-version==2.1

pip install local-attention==1.4.3
pip install performer-pytorch==1.1.4
pip install product-key-memory==0.1.10

사용 환경에 따라 gpu 관련 torch 버전이 달라질 수 있음.
# 리눅스 기반 설치 프로그램.
# fine-tune 실행 시에 셋팅 상태 . RTX 3060 Ti
# 명령어
predict.py 명령어 python predict.py --data_path pbmc_ready_for_predict.h5ad --model_path ckpts/finetune_best.pth --novel_type True --output_path output_data/pbmc1k_pre.h5ad

finetune.py 명령어 python -m torch.distributed.launch --nproc_pre_node=1 finetune.py --data_path "fine-tune_data_path" --model_path "pretrained_model_path" --batch_size 1 --grad_acc 180

scbert(change form) 명령어 python scbert.py pbmc1k_norm_log1p.h5ad panglao_10000.h5ad pbmc_ready_for_predict.h5ad  python scbert.py "바꾸려는 파일" "기준 파일" "출력파일 이름"

export_csv.py 명령어  python export_csv.py "output_data/pbmc1k_pre.h5ad" result_expression.csv
