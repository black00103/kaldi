# taiwanese-speech-recognition-using-kaldi-toolkit-108618018
taiwanese-speech-recognition-using-kaldi-toolkit-108618018 created by GitHub Classroom

# 快速入門
先對Linux環境進行安裝

$ sudo apt-get install libtool  
$ sudo apt-get install autoconf  
$ sudo apt-get install wget  
$ sudo apt-get install perl  
$ sudo apt-get install subversion  
$ sudo apt-get install build-essential  
$ sudo apt-get install gfortran  
$ sudo apt-get install libatlas-base-dev  
$ sudo apt-get install zlib1g-dev  
$ sudo apt-get install gawk  

在root 權限下，用命令:  
$ sudo su  
$ apt-get update  
$ apt-get install git  
$ cd /你想安裝的位置  
$ git clone https://github.com/kaldi-asr/kaldi.git kaldi-trunnk  

安裝完後，檢查Kaldi-trunnk中的./tools,./src,./egs是否有資料，若有代表你已經完成一半了  
在來進入tools目錄:    
$ cd Kaldi-trunk/tools  
$ extras/check_dependencies.sh  
$ extras/install_irstlm.sh  
$ make -j X  
接著進入src目錄:
$ cd Kaldi-trunk/src  
$ ./configure --shared  
$ make depend  
$ make -j X  
等它跑完就代表Kaldi-trunnk已完成安裝  

# Data modification  
請參考Data modification.ppt  

# Training (可以選擇CPU或GPU來執行)  
CPU (run.sh裡的stage = -2)  
$ cd kaldi/egs/taiwanese/s5  
$ nohup ./run.sh >& run.sh.log &  
看及時輸出  
$ tail -f run.sh.log  
 
GPU (run.sh裡的stage = 7)  
$ cd kaldi/egs/taiwanese/s5  
$ nohup ./run.sh >& run.sh_gpu.log &  
看及時輸出  
$ tail -f run.sh_gpu.log  
  
注意:若是先執行CPU完在執行GPU時，需要將data/train_sp/feats.scp刪除，否則會出現error  

# Result  
CPU  
exp/chain/tdnn_1d_sp/decode_test/scoring_kaldi/penalty_1.0/*.txt  
GPU  
exp/chain/tdnn_1d_sp/decode_test/scoring_kaldi/penalty_1.0/*.txt  
可參考圖片1.jpg  

在Leaderboard的成績為4.55967 名次為第24名  
可參考圖片2.jpg


# References  
https://blog.csdn.net/liahuafu/article/details/79834635  


