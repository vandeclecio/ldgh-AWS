# PIPELINE GATK-AWS

Documentação da implementação do pipelino do GATK no AWS.

Aqui, vocês vão encontrar:
- Criar uma documentação;
  - uma visão geral do que ja tem implementado
  - Descrição detalhada de modulo, serviço AWS implementados
- Cada modulo terá um Readme descreendo-os. 
- Criar um tutorial com acessar a AWS


# Passos Principais 

* [Tutorial AWS](https://github.com/vandeclecio/GATK-AWS/blob/main/Tutorial%20AWS/README.md)
  - Acesso ao console na AWS
  - Criar storage EFS
  - Criar storage S3
  - Criar instância EC2
  - Instalar programas em uma instância EC2 
  
# Diagrama Workflow
  ![WorkFlow Pipeline](https://github.com/vandeclecio/GATK-AWS/blob/main/workflow_GATK-AWS.png?raw=true "Workflow")

# Referencias:
- O pipeline utilizado foi obtido do repositorio https://github.com/ThiagoPL/GATK
- Documentação oficial do GATK-Broad Institute [Best Practices Workflows](https://gatk.broadinstitute.org/hc/en-us/sections/360007226651-Best-Practices-Workflows)

 
# [Conectar com instancia EC2 (ldghGATK_EC2-EFS)]()
  * Via Console
  * Via SSH
 
    ## i-0a5ad90df97788c1e (ldghGATK_EC2-EFS)
    
    Open an SSH client.
    
    Locate your private key file. The key used to launch this instance is ldghKeyPair.pem
    
    Run this command, if necessary, to ensure your key is not publicly viewable.

        chmod 400 ldghKeyPair.pem
    
    ### Connect to your instance using its Public DNS:

       ~~ec2-54-146-232-87~~.compute-1.amazonaws.com
    
    **Example:**

        ssh -i "ldghKeyPair.pem" ec2-user@ec2-54-146-232-87.compute-1.amazonaws.com

Obs.: 
 * É necessario ter o arquivo .pem para conectar usando o ssh.
 * O IP da maquina irá mudar toda vez que a maquina for desligada.
 

# Run Pipeline (comando)
 
 *Devido ao grande volume de dado que o pipeline gera,
 ele não pode ser executado no diretorio principal*
 ## Passo-a-Passo Executar Pipeline
 
 1. Apos ter se conectato a maquina (ldghGATK_EC2-EFS) na AWS, siga para proximo passo;
 2. montar diretorio EFS:  `sudo mount -t efs -o tls fs-969f3322:/ database/` ou  `bash mount_Storage.sh`
 3. Criar um diretorio no ~/database/:
 
    `mkdir database/TestePipeline/`. Local onde serão armazenados os arquivos processados;
 4. Exectur o pipeline:
    
    `cd Gatk-master/`
    
    `python3 GATK.py  -c  configuration -r reference  -f /home/ec2-user/database/TestePipeline/ -p programs  -j`
    
    ou 
    
    `./runPipeline.sh`
    
5. As amostras para testes estão no diretorio **~/database/sample/**

# [Relatório Custo-Desempeho AWS]()

- 2 amostras
- chr22
- custo CPU ~= 11 dolares 

