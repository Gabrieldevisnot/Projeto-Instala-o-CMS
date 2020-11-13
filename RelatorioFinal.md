<h1><b>Relatório de instalação do CMS Wordpress</b></h1>

<p> Inicialmente abordaremos os pré-requisitos para a instalação e utilização do CMS Wordpress</p>
<p> Logo após, será descrito, passo a passo, os procedimentos realizados para a instalação do mesmo</p>

<h2><b> Pré-requisitos </h2>

<p> Primeiramente deverá ter um Usuário "Sudo" no seu sistema,<br>
 Feito isso, o seu Servidor precisará ter uma pilha <B>LAMP</B>(Linux, Apache, MySQL, e PHP) instalada e configurada,<br> e por ultimo, mas não menos importante, o protocolo ssl configurado para proteger seu site no Wordpress.</p>

<h2> <b>Instalação e Configuração</h2>

<h3>Criando um banco de dados do MySQL</h3>
<p>Esta instalação é necessária pois o Wordpress Utiliza do Banco de dados Para gerenciar as informações do site e do usuário</p>
<p> Inicialmente acessaremos com uma conta com privilegios administrativos no meu caso é a conta "Magal"</p>
<code>mysql -u Magal -p</code>
<p> Ira pedir para digitar a senha na qual foi definida na configuração inicial do MYSQL</p>
<p>Primeiramente, criamos um banco de dados separado que o WordPress irá controlar. O nome é de sua preferencia, no meu caso, deixei "wordpress". Crie o banco de dados para o WordPress digitando:</p>
<code>CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;</code>

<p> O indicado para a administração do banco de dados do Worpress, é que se crie um usuario exclusivo para a administração do mesmo, mas preferencialmente deixei o meu próprio usuario.</p>
<p> Para criar um usuario especifico para o wordpress deve se digitar:</p>
<code> GRANT ALL ON wordpress.* TO 'wordpressuser'@'localhost' IDENTIFIED BY 'password';

</code>
<p> Atualizando os privilegios deste usuario:</p>
<code>FLUSH PRIVILEGES;</code>
<p>Saia do MySQL digitando:</p>
<code>EXIT;</code>

<h2>Adicionando novas extensões para o PHP</h2>

<p>O PHP quando é configurado na Pilha LAMP vem somente com os plug-ins básicos. O WordPress e muitos dos seus plug-ins potencializam extensões adicionais do PHP.</p>

<p>Podemos baixar e instalar algumas das extensões PHP mais populares para serem usadas com o WordPress digitando:</p>
<code>sudo apt update</code>

<code>sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip
</code>

<p>Vamos reiniciar o Apache para carregar essas novas extensões na próxima seção. Se estiver retornando aqui para instalar plug-ins adicionais, reinicie o Apache agora digitando:</p>

<code>sudo systemctl restart apache2</code>

<h2>Instalando o Wordpress</h2>

<H3><p><b> No console Linux digite os seguintes comandos:</b></p></h3>
<code>mkdir /downloads

<code>cd /downloads</code>
 
 <code>wget https://wordpress.org/latest.tar.gz</code>
 
 <code>tar -zxvf latest.tar.gz</code>
 
 <code>ls</code>

<code>latest.tar.gz wordpress</code>

<p> Agora iremos mover todos os arquivos de instalação do CMS WordPress</p>
<p>Temos que definir a permissão necessaria para todos os arquivos a serem movidos:</p>
<code> mkdir /var/www/html/wordpress</code>

<code>mv wordpress/* /var/www/html/wordpress</code>

<code> chown www-data.www-data /var/www/html/wordpress/* -R</code>

<H3><p><b>Edite o arquivo de configuração do WordPress.</p></b></h3>

<code> cd /var/www/html/wordpress</code>

<code> mv wp-config-sample.php wp-config.php</code>

<code> vi wp-config.php</code>

<p>Aqui está o arquivo original, antes da nossa configuração.<p>

<code>define('DB_NAME', 'database_name_here');</code>
<code>define('DB_USER', 'username_here');</code>
<code>define('DB_PASSWORD', 'password_here');</code>
<code>define('DB_HOST', 'localhost');</code>
<code>define('DB_CHARSET', 'utf8');</code>
<code>define('DB_COLLATE', '');</code>

<p>Aqui está o novo arquivo com nossa configuração No meu caso com o usuario Magal.<p>

<code>define('DB_NAME', 'wordpress');</code>
<code>define('DB_USER', 'Magal');</code>
<code>define('DB_PASSWORD', 'Magal123');</code>
<code>define('DB_HOST', 'localhost');</code>
<code>define('DB_CHARSET', 'utf8');</code>
<code>define('DB_COLLATE', '');</code>

<h2>Referencias</h2>

<a href="https://techexpert.tips/pt-br/wordpress-pt-br/instalacao-wordpress-no-ubuntu-linux/#:~:text=no%20Ubuntu%20Linux.-,No%20console%20do%20Linux%2C%20use%20os%20seguintes%20comandos,baixar%20o%20pacote%20do%20WordPress.&text=Mova%20todos%20os%20arquivos%20do,em%20todos%20os%20arquivos%20movidos.&text=Edite%20o%20arquivo%20de%20configura%C3%A7%C3%A3o%20do%20WordPress.">TechExpert Tips: Instalação WordPress no Ubuntu Linux</a>

<a href="https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-18-04-pt">DigitalOcean:  Como instalar o WordPress com o LAMP no Ubuntu 18.04</a>

<a href="https://blog.da2k.com.br/2015/02/08/aprenda-markdown/">DA2K blog: Aprenda Markdown</a>

