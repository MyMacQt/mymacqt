# Apresentação

Olá, sou o M20. Um entusiasta de Linux e amante da customização de interfaces gráficas. Nesse artigo irei lhe apresentar o caminho das pedras para sair de um KDE plasma padrão:

![image](https://github.com/MyMacQt/mymacqt/assets/154471821/d3d5007c-1919-4b68-882b-20378f58783e)


Para o KDE Plasma mais semelhante ao MacOS já feito: 

![image](https://github.com/MyMacQt/mymacqt/assets/154471821/6d3521ff-0b65-478f-bbdc-cc180ab62f0f)


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
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/10dedbe7-d3a1-43d1-9ea8-f8e6ca289900)

04 - Ir até *Preferências < Terceiros* e habilitar o suporte ao AUR e Flatpak:
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/38620ddc-68cf-4a1c-96ac-60696b716a26)
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/6f8c6b64-4ceb-4098-989b-9c4833823c44)

05 - Atualize o banco de dados do **Pamac**:
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/d2a45a0c-2dad-47ec-a264-62f4c5ff1867)

06 - Após a atualização reinicie o sistema. É importante antes de logar alterar a plataforma de gráficos para X11 / X.org (Utilizaremos ela pois possui mais compatibilidade com temas GTK utilizados no MyMacQt, visto mais a frente).

07 - Abra o Konsole (ou terminal preferido) e acesse com a ferramenta VI/VIM:

```bash
sudo vim /etc/pacman.conf
```

Descomente as linhas *Color, ParallelDownloads*. Recomendo aumentar o número de *ParallelDownloads = 10* (download de + pacotes simultaneamente) e adicionar uma linha com a frase *ILoveCandy* (Eu adoro doces) para o nosso amiguinho pacman sair comendo as bolinhas toda vez que for rodar no terminal.
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/8255d9a4-ead2-4a8f-9e2c-95fb498a7616)

# Baixando pacotes e apps essenciais 

08 - Abra o Konsole e rode esses comandos:

```bash
sudo pacman -Syu ; sudo pacman -S base-devel yay git cmake extra-cmake-modules vim pamac-gtk3 adw-gtk3 gnome-settings-daemon xsettingsd kde-gtk-config gsettings-desktop-schemas gsettings-qt
```

Observação: Alguns pacotes só terão serventia para a distro Manjaro Linux, como é o caso do pacote *pamac-gtk3*.

09 - Abra o **Pamac** e instale os seguintes programas:
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/fae61942-478d-4aca-bfdd-6395a0aa6ee5)

Observação: O Amberol é apenas um tocador de música alternativo, que ficará bem mais "Cool" que o tocador padrão do Plasma.

# Flatseal e permissões
Será essencial para conseguirmos ter aplicativos GTK em harmonia com os em Qt. 

10 - Clique em **Todos os Aplicativos** e selecione as seguintes opções:
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/579a5c9d-ddab-4c56-80f9-3912bda9ca04)

Em **Outros arquivos** adicione as seguintes pastas:

```
~/.themes
```
```
~/.icons
```

![image](https://github.com/MyMacQt/mymacqt/assets/154471821/2261c628-408c-4079-9634-919bacc68e61)
Em **Environment** adicione as seguintes variáveis:

```
ICON_THEME=WhiteSur
```
```
GTK_THEME=WhiteSur-Dark
```

![image](https://github.com/MyMacQt/mymacqt/assets/154471821/2fe57c9a-d771-4635-a8bf-cb9a2505a401)

# Baixando temas WhiteSur

11 - Abra o terminal e rode esse comando:
```bash
cd ~
mkdir .themes .icons
```

12 - Faça download do tema e pacote de ícones do GitHub:

https://github.com/vinceliuice/WhiteSur-icon-theme

https://github.com/vinceliuice/WhiteSur-gtk-theme (Usaremos apenas o arquivo *WhiteSur-Dark.tar.xz* localizado na pasta *release*).
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/3b799a89-0cab-48f3-bfce-e256f5186bf0)

Lembre-se de extrair cada pasta para seu respectivo local:
*~/home/.icons/WhiteSur-icon-theme
~/home/.themes/WhiteSur-Dark*

Atenção: Pode acontecer de não ser possível aplicar o tema GTK com os arquivos baixados localmente, caso isso aconteça apague as pastas dos repositórios baixados acima (que estão dentro das pastas *~/.icons* e *~/.themes*).
# Kvantum Manager

13 - Faça download do tema *Kvantum MacSonoma* do GitHub:

https://github.com/vinceliuice/MacSonoma-kde (Usaremos somente os arquivos dentro da pasta *Kvantum/MacSonoma*)
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/c2bc01e8-51c4-4632-b4c1-16acf655c4ec)

14 - Abra o **Kvantum Manager** e clique em **Selecione uma pasta de tema Kvantum**:
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/cf3ce589-865d-4dd1-a0b3-f37470b9b40d)

Selecione o tema que foi baixado e clique em **Instalar este tema**.

---

15 - Siga as demais instruções para **Kvantum Manager:**
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/be8d0c80-eeec-460f-8a5e-89e6a6d69dcc)

![image](https://github.com/MyMacQt/mymacqt/assets/154471821/94af6607-914f-45d6-a9b7-97e697e67a48)

![image](https://github.com/MyMacQt/mymacqt/assets/154471821/8f8e1d8c-be27-420d-b02d-da1ad2adc679)

![image](https://github.com/MyMacQt/mymacqt/assets/154471821/791a995e-12af-47c9-ad28-584a8388cd1f)

![image](https://github.com/MyMacQt/mymacqt/assets/154471821/4a7b3c11-4faf-403b-8494-41ed7d463121)

---

# Aplicando Tema global

16 - Abra as *Configurações < Aparência < Tema global e busque por:
```
apple-monterey
```

Instale este da imagem:
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/aabe551c-15fd-419c-89f3-4bba4e22210a)

Também busque e instale:
```
macsonoma
```
![image](https://github.com/MyMacQt/mymacqt/assets/154471821/a0cf48c8-197a-48e1-911c-861bce97b8e7)

Observação: Recomendo habilitar momentaneamente esta opção (para visualizar em que partes do sistema estamos aplicando modificações):
![[Captura de tela 22.png]]

17 - Ainda em *Configurações < Aparência < Tema global*, aplique o tema **Apple-Monterey-Dark**
![[Captura de tela 23.png]]

18 - Após o tema carregar entre no modo de edição e remova o painel inferior:
![[Captura de tela 24.png]]
![[Captura de tela 25.png]]

Você também pode remover o ícone de bateria caso não esteja utilizando um laptop:
![[Captura de tela 26.png]]

Reinicie o sistema.

---

# Aplicando tema GTK

19 -  Abra *Configurações < Aparência < Tema global < Estilo do aplicativo*
Aplique o **kvantum-dark**:
![[Captura de tela 27.png]]

20 - Clique em **Configurar estilo de aplicativos GNOME/GTK** e selecione o tema **WhiteSur-Dark**:
![[Captura de tela 28.png]]

Atenção: Poderá acontecer uma situação após reiniciar a máquina, seu sistema não irá conseguir setar o tema WhiteSur em aplicativos Flatpak. Se esse problema acontecer apague o tema WhiteSur-Dark: 
![[Captura de tela 29.png]]

Clique em **Baixar novos estilos de aplicativos GNOME/GTK**, busque por:
```
WhiteSur
```
![[Captura de tela 30.png]]

Instale a versão correta **(WhiteSur-Dark.tax.xz)**:
![[Captura de tela 31.png]]

Abra o terminal e edite os seguintes arquivos, alterando os campos para o que está sendo apresentado na print:
```
sudo vim /usr/share/gtk-3.0/settings.ini
```
![[Captura de tela 32.png]]

```
sudo vim ~/.config/gtk-3.0/settings.ini
```
![[Captura de tela 33.png]]

Atenção: O tema **WhiteSur-Dark** (GTK) em meus testes só funcionou corretamente na Plataforma de gráficos X11, caso você opte por usar Wayland fique ciente que o tema pode não funcionar nos apps Flatpak's! Recomendo alterar para X11 e usar como padrão.

---

# Decorações da janela

21 - Mude para o tema **MacSonoma-Dark**, selecione o **Tamanho da borda da tela** para o valor **Sem bordas**, clique em Aplicar:
![[Captura de tela 34.png]]

Observação: Em temas estilo MacOS criados para o Plasma você acaba encontrando uma variedade de **Decorações da janela** para instalar e testar, porém todos que testei até hoje possuem o mesmo problema:
- A - Bordas da janela de cima redondas e bordas da janela de baixo quadradas.
![[Captura de tela 35.png]]

- B - Bordas da janela de cima redondas e bordas da janela de baixo redondas com uma extensão inferior.
![[Captura de tela 36.png]]

Em particular, nunca me contentei com ambos! pois se afastam de como as janelas em um MacOS são (com ambas as bordas redondas). A extensão inferior (item B) acaba aumentando o tamanho das janelas desnecessariamente, isso pode causar estranhamento na hora de usar alguns aplicativos.

Porém vamos consertar isso mais a frente =)

---

# Ícones

22 - Selecione o tema de ícones **WhiteSur-dark**, clique em Aplicar:
![[Captura de tela 37.png]]

# Cursores

23 - Selecione o cursor **Apple-cursors**, clique em Aplicar:
![[Captura de tela 38.png]]
# Tela de apresentação

24 - Selecione o tema **Apple-Monterey-Dark**, clique em Aplicar:
![[Captura de tela 39.png]]

# Comportamento do espaço de trabalho

25 - Em *Comportamento do espaço < Bordas da tela* ative a opção **Permanecer ativo quando as janelas estiverem em tela cheia**, clique em Aplicar:
![[Captura de tela 40.png]]

# Efeitos da área de trabalho

26 - Substitua **Achatar** por **Lâmpada mágica**, clique em Aplicar:
![[Captura de tela 41.png]]

E selecione **Escurecer a tela no modo administrador**, clique em Aplicar:
![[Captura de tela 42.png]]

---
# Áreas de trabalho virtuais
Essa sessão é opcional, eu gosto de usar 4 áreas de trabalho com bind no Alt+[1,2,3,4], dessa forma posso ter tudo organizado e navegar igual em um bspwm.

*Áreas de trabalho virtuais < + Adicionar (x2)*

---

# Atalhos

27 - Recomendo adicionar alguns atalhos para facilitar o uso (totalmente opcional):
![[Captura de tela 43.png]]
![[Captura de tela 44.png]]

# Inicialização e desligamento

28 - Em *Inicialização e desligamento < Tela de autenticação (SDDM) < Clique nos 3 pontos < Baixar novos temas SDDM*:
![[Captura de tela 45.png]]

Busque por **Monterey** e instale o pacote **Monterey.tar.xz**:
```
monterey
```
![[Captura de tela 46.png]]
![[Captura de tela 47.png]]

Após a instalação, selecione o tema e clique em Aplicar.

# Notificações

29 - Em *Notificações < Escolher posição personalizada...* selecione o canto superior direito:
![[Captura de tela 48.png]]

# Konsole

30 - Abra o *Konsole < Configurações* e desative os itens em **Barras de ferramentas visíveis**:
![[Captura de tela 49.png]]

31 - Em *Konsole < Configurações < Gerenciar perfis... < + Novo* altere o Comando para */bin/zsh* e selecione **Perfil padrão**, clique em Aplicar:
![[Captura de tela 50.png]]

32 - Em **Mouse**, selecione **Copiar ao selecionar** em **Opções de cópia**, clique em Aplicar:
![[Captura de tela 51.png]]

33 - Em **Aparência**, selecione o tema **Breeze** e clique em **Editar**, altere o **Plano de fundo** de **Cor, Cor intensa e Cor fraca** para preto. Selecione **Borrar o plano de fundo** e adicione 30% de **Transparência da cor de fundo**, clique em Aplicar:
![[Captura de tela 52.png]]

Feche o terminal e abra novamente para ver as modificações.

---

# KRunner

34 - Abra o KRunner com Alt+Space, clique no simbolo de engrenagem:
![[Captura de tela 53.png]]

Selecione a opção **Centro**, clique em Aplicar:
![[Captura de tela 54.png]]

# Latte Dock

35 - Abra a **Latte Dock**, *Clique com botão direito na sua borda < Configurar o Latte...* :
![[Captura de tela 55.png]]

Em **Configurações** selecione as seguintes opções, por final clique em Aplicar:
- Usar estilo 3D para os emblemas das notificações e atalhos.
- Pressione {MASTER} para ativar o lançador de aplicativos.
- Efeito parabólico: Baixa
![[Captura de tela 56.png]]

Em **Editor de layouts** clique em **Importar de arquivo local...**, selecione o tema local e clique em Aplicar e Mudar:
![[Captura de tela 57.png]]

Observação: No final deste artigo deixarei o meu preset no GitHub para o Latte Dock, mas você pode buscar por temas na loja online se preferir.

Meu preset possui essa aparência:
![[Apple Dock 2.png]]

---

# Active application
Semelhante ao Finder do MacOS iremos adicionar um texto falso para imitar o comportamento na Mesa ou Área de trabalho:

36 - *Clique com botão direito no painel superior < Configurar Active application...* :
![[Captura de tela 58.png]]

Em **No window text**, apague **Desktop** e cole o texto abaixo, clique em Aplicar:

```
Dolphin      Arquivo    Editar    Exibir    Ir    Ferramentas    Configurações    Ajuda
```

Ficará com esse visual:
![[Captura de tela 59.png]]

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
![[Captura de tela 60.png]]

Reinicie o sistema e aproveite a coletânea MyMacQt =) 

---

# Bônus do MyMacQt
Tutorial completo em vídeo:
https://youtu.be/vXqN42TWU9E

Todos os arquivos e presets utilizados:
https://github.com/MyMacQt/mymacqt

Precisa de ajuda? Abra uma **New issue** no GitHub da coletânea.

---

# Créditos
https://manjaro.org/

https://github.com/vinceliuice (WhiteSur-gtk-theme, WhiteSur-icon-theme, MacSonoma-kde Kvantum)

https://store.kde.org/u/zayronXIO (Apple Monterey Dark 5.27 or superior)

https://store.kde.org/u/vinceliuice (MacSonoma KDE Dark theme, WhiteSur Gtk theme, Monterey sddm theme)

https://github.com/matinlotfali (KDE Rounded Corners)
