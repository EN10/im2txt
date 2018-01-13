# im2txt
A Neural Image Caption Generator.    

* Based on [KranthiGV Show and Tell](https://github.com/KranthiGV/Pretrained-Show-and-Tell-model)     
* Which is based on [Google Show and Tell GitHub](https://github.com/tensorflow/models/tree/master/research/im2txt)  
* [Show and Tell Google Blog](https://research.googleblog.com/2016/09/show-and-tell-image-captioning-open.html)

## Install

### Bazel:

    sudo apt update
    sudo apt install git software-properties-common python-software-properties curl
    
    sudo add-apt-repository ppa:webupd8team/java
    sudo apt update && sudo apt install oracle-java8-installer
    
    echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
    curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -
    
    sudo apt update && sudo apt install bazel
    
## Tensorflow
    
    sudo pip install -U pip
    sudo pip install tensorflow==1.0
    
### im2txt

    svn export https://github.com/tensorflow/models/trunk/research/im2txt
    
    CHECKPOINT_PATH="/home/ubuntu/workspace/model.ckpt-2000000"
    VOCAB_FILE="/home/ubuntu/workspace/word_counts.txt"
    IMAGE_FILE="/home/ubuntu/workspace/image.jpg"
    
    cd im2txt/
    bazel build -c opt //im2txt:run_inference
    
### Run:

    bazel-bin/im2txt/run_inference \
      --checkpoint_path=${CHECKPOINT_PATH} \
      --vocab_file=${VOCAB_FILE} \
      --input_files=${IMAGE_FILE}
      
**ERROR:**

ERROR: `python': double free or corruption (!prev)`
    
    sudo apt-get install libtcmalloc-minimal4
    export LD_PRELOAD="/usr/lib/libtcmalloc_minimal.so.4"