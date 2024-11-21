# Instalação do software **CODESYS** no Raspberry Pi para uso como controlador lógico programável (PLC). 

O CODESYS é uma plataforma de desenvolvimento que suporta diversos controladores de automação, incluindo o Raspberry Pi, desde que esteja rodando uma distribuição compatível de Linux, como o Raspberry Pi OS.

## 1. **Preparar o Raspberry Pi**

   - **Atualize o sistema operacional**

	   - Abra o terminal no Raspberry Pi e execute os seguintes comandos para garantir que o sistema está atualizado:

       ```bash
       sudo apt-get update
       sudo apt-get upgrade
       sudo reboot
       ```

   - **Configuração do IP fixo (opcional)**

     - Caso você queira ter um IP fixo para facilitar a comunicação com o Raspberry Pi, configure um IP estático no arquivo de configuração de rede ou através do seu roteador.

## 2. **Instalar o CODESYS Runtime**

   - **Acesse o site oficial do CODESYS**
   
	     - Vá ao site oficial do CODESYS ([CODESYS Store](https://store.codesys.com/)) e crie uma conta ou faça login.

    	 - Procure por "CODESYS Control for Raspberry Pi SL".

   - **Baixe o pacote para o Raspberry Pi**

     - Após adquirir (gratuitamente) o produto, baixe o arquivo ".deb" apropriado para a arquitetura do Raspberry Pi (geralmente ARM).

   - **Transferir o arquivo para o Raspberry Pi**
   
     - Se você baixou o arquivo em outro computador, use SCP, FTP, um pendrive ou outro método para transferir o arquivo ".deb" para o Raspberry Pi.

   - **Instalar o CODESYS Control Runtime**
   
     - Navegue até o diretório onde o arquivo foi transferido e execute o seguinte comando para instalar:
     
       ```bash
       sudo dpkg -i codesyscontrol_arm_raspberrypi.deb
       ```
     - Após a instalação, execute o comando abaixo para garantir que as dependências estão instaladas corretamente:

       ```bash
       sudo apt-get install -f
       ```

## 3. **Configurar o CODESYS Runtime**

   - **Licenciamento**
   
     - Para usar o CODESYS no Raspberry Pi, você precisará de uma licença. Para isso, após instalar, acesse a interface do CODESYS no seu computador e conecte-se ao Raspberry Pi.

     - No CODESYS, configure a licença ou use o período de avaliação gratuito.

   - **Verificar o status do serviço**

     - Verifique se o serviço do CODESYS Runtime está ativo executando:
     
       ```bash
       sudo systemctl status codesyscontrol
       ```

     - Se o serviço não estiver rodando, você pode iniciá-lo com:

       ```bash
       sudo systemctl start codesyscontrol
       ```

## 4. **Desenvolver e Transferir Projetos**

   - **Configurar um projeto no CODESYS**
   
     - No seu computador, abra o CODESYS Development System.

     - Crie um novo projeto e selecione o Raspberry Pi como dispositivo alvo.

     - Configure as entradas/saídas e programe a lógica PLC desejada.

   - **Conectar ao Raspberry Pi**

     - No CODESYS, conecte ao Raspberry Pi através do IP configurado anteriormente.

     - Faça o download do projeto para o Raspberry Pi e inicie o runtime.

#### 5. **Testar e Operar**

   - **Testar seu programa**
   
     - Com o projeto rodando no Raspberry Pi, teste a lógica programada para garantir que tudo está funcionando como esperado.
   
   - **Monitoramento**
   
     - Você pode monitorar e depurar o programa diretamente no CODESYS Development System enquanto ele está em execução no Raspberry Pi.
