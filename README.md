# scBERT
# 리눅스 기반 설치 프로그램.
# fine-tune 실행 시에 셋팅 상태 . RTX 3060 Ti
# 명령어
#predict 명령어 python predict.py --data_path pbmc_ready_for_predict.h5ad --model_path ckpts/finetune_best.pth --novel_type True --output_path output_data/pbmc1k_pre.h5ad
#fine_tune 명령어 python -m torch.distributed.launch finetune.py --data_path "fine-tune_data_path" --model_path "pretrained_model_path" --batch_size 1 --grad_acc 180
#change form 명령어 python scbert.py pbmc1k_norm_log1p.h5ad panglao_10000.h5ad pbmc_ready_for_predict.h5ad  python scbert.py "바꾸려는 파일" "기준 파일" "출력파일 이름"
