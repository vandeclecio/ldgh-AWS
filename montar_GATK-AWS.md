# GATK-AWS
Pipeline GATK aplicado na AWS


## Criar storage EFS (Elastic File System)

### Tutorial EFS aws:
1. Criar EFS: https://docs.aws.amazon.com/efs/latest/ug/gs-step-two-create-efs-resources.html
2. Criar EC2: https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html

## Criar EC2 AmazonLinux




## Configurar S3 no EC2

aws configure

- Access key ID: 
- Secret access key : 
- zone : us-east-1 
- output : json

# Instalando ferramentas do Pipeline

1. Python3
 - sudo yum -y install gcc openssl-devel bzip2-devel libffi-devel  ncurses-devel  xz-devel
 - sudo yum install autoconf automake make gcc perl-Data-Dumper zlib-devel bzip2 bzip2-devel xz-devel curl-devel openssl-devel ncurses-devel
 - cd /opt 
 - sudo wget https://www.python.org/ftp/python/3.9.4/Python-3.9.4.tgz 
 - sudo tar xzf Python-3.9.4.tgz
 - cd Python-3.9.4 
 - sudo ./configure --enable-optimizations 
 - sudo make altinstall 
 - sudo rm -f /opt/Python-3.9.4.tgz 
  
2. java
 - sudo amazon-linux-extras install java-openjdk11


  
1. trimmomatics
 - wget http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip
 - unzip Trimmomatic-0.39.zip
 - sudo mv Trimmomatic-0.39/ /lib/
 - ln -s /lib/Trimmomatic-0.39/trimmomatic-0.39.jar /bin/.
  
  
2. samtools

- wget https://github.com/samtools/samtools/releases/download/1.12/samtools-1.12.tar.bz2
- bunzip samtools-1.12.tar.bz2
- tar -xvf samtools-1.12.tar
- cd  samtools-1.12.tar
- ./configure --prefix=/lib/
- make
- sudo make install
- cd
- sudo mv samtools-1.12/ /lib
- sudo ln -s /lib/samtools-1.12/samtools /bin/
- rm samtools-1.12.tar
  
 
- wget https://github.com/samtools/bcftools/releases/download/1.12/bcftools-1.12.tar.bz2
- bunzip2 bcftools-1.12.tar.bz2
- tar -vxf bcftools-1.12.tar
- cd bcftools-1.12/
- ./configure
- make
- sudo makde install
  
- git clone --recurse-submodules git://github.com/samtools/htslib.git
- git clone git://github.com/samtools/bcftools.git
- cd bcftools
     

2. Git
- sudo yum install git
 
3. bwa
- git clone https://github.com/lh3/bwa.git
- cd bwa; make
- cd
- sudo mv /bwa/ /lib/
- sudo ln -s /lib/bwa/bwa /bin/
  
  
4. picard
 - wget https://github.com/broadinstitute/picard/releases/download/2.25.4/picard.jar
 - sudo mv picard.jar /lib/
 - sudo ln -s /lib/picard.jar /bin/
  
5. gatk
 - wget https://github.com/broadinstitute/gatk/releases/download/4.2.0.0/gatk-4.2.0.0.zip
 - unzip gatk-4.2.0.0.zip
 - sudo mv gatk-4.2.0.0/ /lib/
 - sudo ln -s /lib/gatk-4.2.0.0/gatk /bin/

6. 

