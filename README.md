# Apresentação

Olá, sou o M20. Um entusiasta de Linux e amante da customização de interfaces gráficas. Nesse artigo irei lhe apresentar o caminho das pedras para sair de um KDE plasma padrão:

![[Captura de tela de 2023-12-20 11-14-59.png]]

Para o KDE Plasma mais semelhante ao MacOS já feito: 

![[Captura de tela de 2023-12-20 11-17-59.png]]

# Por que um KDE Plasma com visual MacOS?

Acredito que o melhor ambiente desktop para uso cotidiano é, além de tudo, aquele que você se sente mais confortável em utilizar, e por que não reproduzir tal customização em um *Desktop Environment* que lhe dar muito mais liberdade de personalização?

A DE Plasma é perfeita para realizarmos essa customização no Linux.

# Introdução

Nesse artigo será utilizado a distro Manjaro Linux, você poderá utilizar outra caso deseje, também serão usadas ferramentas, pacotes, scripts e temas de terceiros com todos os créditos devidamente citados ao final. Meu trabalho foi apenas reuni-los nessa coletânea apelidada por mim de **MyMacQt** que demorou 6 meses para adquirir tal maturidade, espero que aproveitem. 

Vamos dar início a customização **MyMacQt** \0/

# Download, Instalação e Atualização

Esse artigo foi testado em hardware real e através de VMs, seguindo dessa configuração:

```bash
Versão do KDE Plasma: Plasma 5.27.10
Versão do KDE Frameworks: 5.112.0
Versão da Qt: 5.15.11
Versão do Kernel: 6.5.13-4-MANJARO (64-bit)
Plataforma de gráficos: X11
```

---

01 - Faça o download da ISO do Manjaro Linux no site oficial: https://manjaro.org/ (Selecione a ISO com o PLASMA DESKTOP).

02 - Dê boot na ISO em um pendrive ou em uma máquina virtual, siga as instruções de instalação do sistema e reinicie.

03 - Abra o gerenciador de pacotes **Pamac** (geralmente representado como **Adicionar/remover programas**):
![[Captura de tela de 2023-12-20 11-56-09.png]]

04 - Ir até *Preferências < Terceiros* e habilitar o suporte ao AUR e Flatpak:
![[Captura de tela de 2023-12-20 12-01-23.png]]
![[Captura de tela de 2023-12-20 12-01-32.png]]

05 - Atualize o banco de dados do **Pamac**:
![[Pasted image 20231220184903.png]]

06 - Após a atualização reinicie o sistema. É importante antes de logar alterar a plataforma de gráficos para X11 / X.org (Utilizaremos ela pois possui mais compatibilidade com temas GTK utilizados no MyMacQt, visto mais a frente).

07 - Abra o Konsole (ou terminal preferido) e acesse com a ferramenta VI/VIM:

```bash
sudo vim /etc/pacman.conf
```

Descomente as linhas *Color, ParallelDownloads*. Recomendo aumentar o número de *ParallelDownloads = 10* (download de + pacotes simultaneamente) e adicionar uma linha com a frase *ILoveCandy* (Eu adoro doces) para o nosso amiguinho pacman sair comendo as bolinhas toda vez que for rodar no terminal.
![[Pasted image 20231220121801.png]]

# Baixando pacotes e apps essenciais 

08 - Abra o Konsole e rode esses comandos:

```bash
sudo pacman -Syu ; sudo pacman -S base-devel yay git cmake extra-cmake-modules vim pamac-gtk3 adw-gtk3 gnome-settings-daemon xsettingsd kde-gtk-config gsettings-desktop-schemas gsettings-qt
```

Observação: Alguns pacotes só terão serventia para a distro Manjaro Linux, como é o caso do pacote *pamac-gtk3*.

09 - Abra o **Pamac** e instale os seguintes programas:
![[Pasted image 20231220122455.png]]

Observação: O Amberol é apenas um tocador de música alternativo, que ficará bem mais "Cool" que o tocador padrão do Plasma.

# Flatseal e permissões
Será essencial para conseguirmos ter aplicativos GTK em harmonia com os em Qt. 

10 - Clique em **Todos os Aplicativos** e selecione as seguintes opções:
![[Screenshot_20231220_123844.png]]
Em **Outros arquivos** adicione as seguintes pastas:

```
~/.themes
```
```
~/.icons
```

![[Screenshot_20231220_123929.png]]
Em **Environment** adicione as seguintes variáveis:

```
ICON_THEME=WhiteSur
```
```
GTK_THEME=WhiteSur-Dark
```

![[Screenshot_20231220_123944.png]]

# Baixando temas WhiteSur

11 - Abra o terminal e rode esse comando:
```bash
cd ~
mkdir .themes .icons
```

12 - Faça download do tema e pacote de ícones do GitHub:

https://github.com/vinceliuice/WhiteSur-icon-theme

https://github.com/vinceliuice/WhiteSur-gtk-theme (Usaremos apenas o arquivo *WhiteSur-Dark.tar.xz* localizado na pasta *release*).
![[Pasted image 20231220130943.png]]

Lembre-se de extrair cada pasta para seu respectivo local:
*~/home/.icons/WhiteSur-icon-theme
~/home/.themes/WhiteSur-Dark*

Atenção: Pode acontecer de não ser possível aplicar o tema GTK com os arquivos baixados localmente, caso isso aconteça apague as pastas dos repositórios baixados acima (que estão dentro das pastas *~/.icons* e *~/.themes*).
# Kvantum Manager

13 - Faça download do tema *Kvantum MacSonoma* do GitHub:

https://github.com/vinceliuice/MacSonoma-kde (Usaremos somente os arquivos dentro da pasta *Kvantum/MacSonoma*)
![[Pasted image 20231220141030.png]]

14 - Abra o **Kvantum Manager** e clique em **Selecione uma pasta de tema Kvantum**:
![[Pasted image 20231220130359.png]]

Selecione o tema que foi baixado e clique em **Instalar este tema**.

---

15 - Siga as demais instruções para **Kvantum Manager:**
![[Screenshot_20230718_003417.png]]
![[Screenshot_20230718_003425.png]]

![[Screenshot_20230718_003432.png]]
![[Screenshot_20230718_003437.png]]
![[Screenshot_20230718_003441.png]]

# Aplicando Tema global

16 - Abra as *Configurações < Aparência < Tema global e busque por:
```
apple-monterey
```

Instale este da imagem:
![[Pasted image 20231220131824.png]]

Também busque e instale:
```
macsonoma
```
![[Pasted image 20231220131936.png]]

Observação: Recomendo habilitar momentaneamente esta opção (para visualizar em que partes do sistema estamos aplicando modificações):
![[Pasted image 20231220132048.png]]

17 - Ainda em *Configurações < Aparência < Tema global*, aplique o tema **Apple-Monterey-Dark**
![[Pasted image 20231220132221.png]]

18 - Após o tema carregar entre no modo de edição e remova o painel inferior:
![[Pasted image 20231220140012.png]]
![[Pasted image 20231220140037.png]]

Você também pode remover o ícone de bateria caso não esteja utilizando um laptop:
![[Pasted image 20231220140115.png]]

Reinicie o sistema.

---

# Aplicando tema GTK

19 -  Abra *Configurações < Aparência < Tema global < Estilo do aplicativo*
Aplique o **kvantum-dark**:
![[Pasted image 20231220140550.png]]

20 - Clique em **Configurar estilo de aplicativos GNOME/GTK** e selecione o tema **WhiteSur-Dark**:
![[Pasted image 20231220140641.png]]

Atenção: Poderá acontecer uma situação após reiniciar a máquina, seu sistema não irá conseguir setar o tema WhiteSur em aplicativos Flatpak. Se esse problema acontecer apague o tema WhiteSur-Dark: 
![[Pasted image 20231220141930.png]]

Clique em **Baixar novos estilos de aplicativos GNOME/GTK**, busque por:
```
WhiteSur
```
![[Pasted image 20231220142105.png]]

Instale a versão correta **(WhiteSur-Dark.tax.xz)**:
![[Pasted image 20231220142702.png]]

Abra o terminal e edite os seguintes arquivos, alterando os campos para o que está sendo apresentado na print:
```
sudo vim /usr/share/gtk-3.0/settings.ini
```
![[Pasted image 20231220165636.png]]

```
sudo vim ~/.config/gtk-3.0/settings.ini
```
![[Pasted image 20231220165707.png]]

Atenção: O tema **WhiteSur-Dark** (GTK) em meus testes só funcionou corretamente na Plataforma de gráficos X11, caso você opte por usar Wayland fique ciente que o tema pode não funcionar nos apps Flatpak's! Recomendo alterar para X11 e usar como padrão.

---

# Decorações da janela

21 - Mude para o tema **MacSonoma-Dark**, selecione o **Tamanho da borda da tela** para o valor **Sem bordas**, clique em Aplicar:
![[Pasted image 20231220143328.png]]

Observação: Em temas estilo MacOS criados para o Plasma você acaba encontrando uma variedade de **Decorações da janela** para instalar e testar, porém todos que testei até hoje possuem o mesmo problema:
- A - Bordas da janela de cima redondas e bordas da janela de baixo quadradas.
![[Pasted image 20231220144153.png]]

- B - Bordas da janela de cima redondas e bordas da janela de baixo redondas com uma extensão inferior. 
![[Pasted image 20231220144231.png]]

Em particular, nunca me contentei com ambos! pois se afastam de como as janelas em um MacOS são (com ambas as bordas redondas). A extensão inferior (item B) acaba aumentando o tamanho das janelas desnecessariamente, isso pode causar estranhamento na hora de usar alguns aplicativos.

Porém vamos consertar isso mais a frente =)

---

# Ícones

22 - Selecione o tema de ícones **WhiteSur-dark**, clique em Aplicar:
![[Pasted image 20231220144834.png]]

# Cursores

23 - Selecione o cursor **Apple-cursors**, clique em Aplicar:
![[Pasted image 20231220153541.png]]
# Tela de apresentação

24 - Selecione o tema **Apple-Monterey-Dark**, clique em Aplicar:
![[Pasted image 20231220145008.png]]

# Comportamento do espaço de trabalho

25 - Em *Comportamento do espaço < Bordas da tela* ative a opção **Permanecer ativo quando as janelas estiverem em tela cheia**, clique em Aplicar:
![[Pasted image 20231220151354.png]]

# Efeitos da área de trabalho

26 - Substitua **Achatar** por **Lâmpada mágica**, clique em Aplicar:
![[Pasted image 20231220145424.png]]

E selecione **Escurecer a tela no modo administrador**, clique em Aplicar:
![[Pasted image 20231220151608.png]]

---
# Áreas de trabalho virtuais
Essa sessão é opcional, eu gosto de usar 4 áreas de trabalho com bind no Alt+[1,2,3,4], dessa forma posso ter tudo organizado e navegar igual em um bspwm.

*Áreas de trabalho virtuais < + Adicionar (x2)*

---

# Atalhos

27 - Recomendo adicionar alguns atalhos para facilitar o uso (totalmente opcional):
![[Pasted image 20231220152551.png]]
![[Pasted image 20231220152631.png]]

# Inicialização e desligamento

28 - Em *Inicialização e desligamento < Tela de autenticação (SDDM) < Clique nos 3 pontos < Baixar novos temas SDDM*:
![[Pasted image 20231220152912.png]]

Busque por **Monterey** e instale o pacote **Monterey.tar.xz**:
```
monterey
```
![[Pasted image 20231220153004.png]]
![[Pasted image 20231220153110.png]]

Após a instalação, selecione o tema e clique em Aplicar.

# Notificações

29 - Em *Notificações < Escolher posição personalizada...* selecione o canto superior direito:
![[Pasted image 20231220153342.png]]

# Konsole

30 - Abra o *Konsole < Configurações* e desative os itens em **Barras de ferramentas visíveis**:
![[Pasted image 20231220153852.png]]

31 - Em *Konsole < Configurações < Gerenciar perfis... < + Novo* altere o Comando para */bin/zsh* e selecione **Perfil padrão**, clique em Aplicar:
![[Pasted image 20231220154052.png]]

32 - Em **Mouse**, selecione **Copiar ao selecionar** em **Opções de cópia**, clique em Aplicar:
![[Pasted image 20231220154111.png]]

33 - Em **Aparência**, selecione o tema **Breeze** e clique em **Editar**, altere o **Plano de fundo** de **Cor, Cor intensa e Cor fraca** para preto. Selecione **Borrar o plano de fundo** e adicione 30% de **Transparência da cor de fundo**, clique em Aplicar:
![[Pasted image 20231220154738.png]]

Feche o terminal e abra novamente para ver as modificações.

---

# KRunner

34 - Abra o KRunner com Alt+Space, clique no simbolo de engrenagem:
![[Pasted image 20231220155101.png]]

Selecione a opção **Centro**, clique em Aplicar:
![[Pasted image 20231220155201.png]]

# Latte Dock

35 - Abra a **Latte Dock**, *Clique com botão direito na sua borda < Configurar o Latte...* :
![[Pasted image 20231220155316.png]]

Em **Configurações** selecione as seguintes opções, por final clique em Aplicar:
- Usar estilo 3D para os emblemas das notificações e atalhos.
- Pressione {MASTER} para ativar o lançador de aplicativos.
- Efeito parabólico: Baixa
![[Pasted image 20231220155404.png]]

Em **Editor de layouts** clique em **Importar de arquivo local...**, selecione o tema local e clique em Aplicar e Mudar:
![[Pasted image 20231220160700.png]]

Observação: No final deste artigo deixarei o meu preset no GitHub para o Latte Dock, mas você pode buscar por temas na loja online se preferir.

Meu preset possui essa aparência:
![[Apple Dock 2.png]]

---

# Active application
Semelhante ao Finder do MacOS iremos adicionar um texto falso para imitar o comportamento na Mesa ou Área de trabalho:

36 - *Clique com botão direito no painel superior < Configurar Active application...* :
![[Pasted image 20231220164918.png]]

Em **No window text**, apague **Desktop** e cole o texto abaixo, clique em Aplicar:

```
Dolphin      Arquivo    Editar    Exibir    Ir    Ferramentas    Configurações    Ajuda
```

Ficará com esse visual:
![[Pasted image 20231220165143.png]]

---

# KDE Rounded Corners

37 - Faça download do repositório **KDE-Rounded-Corners** do GitHub:
https://github.com/matinlotfali/KDE-Rounded-Corners

Você pode seguir o próprio tutorial do repositório, mas encurtando, rode esses comandos para compilar o programa (se você baixou todos os pacotes no começo desse artigo e está utilizando Manjaro Linux):
```
cd ~
git clone https://github.com/matinlotfali/KDE-Rounded-Corners
cd KDE-Rounded-Corners
mkdir build
cd build
cmake .. --install-prefix /usr
make
sudo make install
```

Abra *Configurações < Comportamento do espaço de trabalho < Efeitos da área de trabalho*, busque por **ShapeCorners** e ative, clique em Aplicar:
![[Pasted image 20231220171243.png]]

Reinicie o sistema e aproveite a coletânea MyMacQt =) 

---

# Bônus do MyMacQt
Tutorial completo em vídeo:
https://youtu.be/vXqN42TWU9E

Todos os arquivos e presets utilizados:
https://github.com/MyMacQt/mymacqt

Precisa de ajuda? Abra uma **New issue** no GitHub da coletânea.
# Créditos


