# Executando o projeto no WSL2
### 3\. **Instalar o Google Chrome no WSL2**

Se ainda não tiver o Google Chrome instalado em seu WSL2, você pode instalá-lo seguindo estas etapas:

*   Abra o terminal do WSL2 e atualize seus pacotes:
    
    `sudo apt update && sudo apt upgrade`
    
*   Baixe o pacote mais recente do Google Chrome:
    
    `wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb`
    
*   Instale o pacote baixado:
    
    `sudo apt install ./google-chrome-stable_current_amd64.deb`
    
*   Caso enfrente problemas com dependências, você pode corrigi-las com:
    
    `sudo apt --fix-broken install`
    

### 4\. **Executar o Google Chrome no WSL2**

Você precisará iniciar o Chrome com algumas opções específicas para evitar problemas com o ambiente gráfico:

*   No seu terminal WSL2, execute:
    
    `google-chrome --no-sandbox --disable-gpu`
    
*   Essas flags ajudam a rodar o Chrome em um ambiente que originalmente não suporta uma interface gráfica diretamente.

### 5\. **Carregar sua Extensão**

*   No Chrome aberto, vá para `chrome://extensions/`.
*   Ative o "Modo de desenvolvedor" no canto superior direito.
*   Clique em "Carregar sem compactação" e selecione a pasta da sua extensão no sistema de arquivos do WSL que você abriu no VSCode.

### 6\. **Desenvolvimento e Teste**

*   Faça alterações no seu código usando o VSCode no WSL2.
*   Para ver as alterações refletidas no Chrome, você pode precisar recarregar a extensão manualmente através da página `chrome://extensions/` clicando em "Atualizar" sob a listagem da sua extensão.

### 7\. **Depuração**

*   Use as Ferramentas do Desenvolvedor do Chrome (F12) para inspecionar sua extensão e depurar quaisquer problemas.

# Estrutura de Diretórios

Copy code
PromptPerfector/
│
├── src/                    # Código fonte da extensão
│   ├── background/         # Scripts de background
│   │   └── background.js
│   ├── content/            # Scripts de conteúdo
│   │   └── content.js
│   ├── popup/              # HTML/CSS/JS para a UI do popup
│   │   ├── popup.html
│   │   ├── popup.js
│   │   └── popup.css
│   └── lib/                # Bibliotecas de terceiros
│       └── tensorflow.js   # Exemplo de biblioteca de IA
│
├── icons/                  # Ícones para a extensão
│   ├── icon16.png
│   ├── icon48.png
│   └── icon128.png
│
├── manifest.json           # Manifesto da extensão
└── README.md               # Documentação do projeto
```

- Descrição dos Componentes
- manifest.json: Define os metadados, scripts de background, permissões, etc.
- background.js: Pode hospedar listeners para eventos da extensão ou lógica de IA que não precisa interagir diretamente com as páginas.
- content.js: Pode ser usado para injetar e modificar o DOM de uma página web, talvez para coletar exemplos de prompts que podem ser aprimorados.
- popup/: Contém todos os arquivos relacionados à interface do usuário que aparece quando o usuário clica no ícone da extensão.
- lib/: Armazena bibliotecas de terceiros, como frameworks de IA (TensorFlow.js, por exemplo), que podem ser utilizados para processar e aprimorar os prompts diretamente no navegador.