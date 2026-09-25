# Loja de Jogos — projeto Capacitor (Android)

Isto é o site (`www/index.html`) já empacotado como projeto Capacitor,
pronto pra você gerar o APK na sua máquina.

## Pré-requisitos (na sua máquina, não aqui)
- Node.js + npm
- Android Studio (com Android SDK instalado)

## Passo a passo

1. Extraia esta pasta e abra um terminal dentro dela.

2. Instale as dependências:
   ```
   npm install
   ```

3. Adicione a plataforma Android (isso cria a pasta `android/`):
   ```
   npx cap add android
   ```

4. Sempre que editar `www/index.html`, sincronize:
   ```
   npx cap sync android
   ```

5. Abra o projeto no Android Studio:
   ```
   npx cap open android
   ```

6. Dentro do Android Studio: **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
   O `.apk` sai em `android/app/build/outputs/apk/debug/`.

   Pra um APK de release (assinado, pra distribuir fora da Play Store),
   use **Build → Generate Signed Bundle / APK**.

## Antes de gerar

- **Ícone e splash screen do app**: troque os arquivos em
  `android/app/src/main/res/mipmap-*` (ou use `npx @capacitor/assets generate`
  depois de colocar `icon.png` e `splash.png` na raiz do projeto).
- **Nome do app / appId**: já configurados em `capacitor.config.json`
  (`com.jtgames.lojadejogos` — troque se quiser outro pacote).
- **Links de APK no catálogo**: edite os campos `url:` dentro do
  `<script>` em `www/index.html` com os links reais dos seus jogos.
- Se algum link de download for `http://` (sem "s"), o
  `allowMixedContent: true` no `capacitor.config.json` já libera isso —
  mas o ideal é usar `https://` sempre que possível.

## Sobre o botão "Baixar"
Ele já abre o link real do APK no navegador do sistema
(`window.open(url, '_system')`) depois da animação de progresso —
funciona tanto no navegador quanto dentro do app empacotado.
