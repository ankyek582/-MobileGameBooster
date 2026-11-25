# Mobile Game Booster

Aplicativo Android nativo em Kotlin, sem root, com interface minimalista.

## O que já está implementado
- Painel com RAM disponível, nível da bateria, temperatura informada pela bateria e armazenamento livre.
- Perfis locais Econômico, Equilibrado e Desempenho (salvos no aparelho).
- Lista de apps com atividade de inicialização e botão para abrir.
- Atalhos para configurações de bateria, armazenamento e tela.
- Compatibilidade a partir do Android 6.0 (API 23), sujeito às APIs e restrições do fabricante.

## Limitações importantes
O Android não permite que um aplicativo comum:
- aumente diretamente frequência de CPU/GPU ou faça overclock;
- reserve mais RAM para um jogo por meio de um botão genérico;
- encerre à força processos de outros aplicativos;
- garanta aumento de FPS ou reduza temperatura por software.

Os perfis desta primeira versão são preferências salvas no app e recomendações de uso. Eles não alteram parâmetros internos do sistema. O app evita permissões invasivas e não usa root.

## Como gerar o APK

1. Instale o **Android Studio** e o Android SDK Platform 35.
2. Extraia a pasta `MobileGameBooster`.
3. No Android Studio, escolha **Open** e selecione essa pasta.
4. Aguarde a sincronização do Gradle. Use JDK 17.
5. Se o Android Studio solicitar, aceite instalar/atualizar Android Gradle Plugin e SDK.
6. Para testar: conecte um Android com depuração USB ativada e pressione **Run**.
7. Para gerar APK: **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
8. O APK de debug será criado em:
   `app/build/outputs/apk/debug/app-debug.apk`

## Gerar APK de lançamento
No Android Studio, use **Build > Generate Signed Bundle / APK...**, escolha APK, crie ou selecione uma chave de assinatura e conclua o assistente. Guarde a chave e as senhas em local seguro; elas serão necessárias para futuras atualizações.

## Requisitos do projeto
- Android Studio compatível com AGP 8.7.3
- JDK 17
- Android SDK Platform 35
- Gradle será baixado pelo Android Studio na primeira sincronização.

## Próximas evoluções possíveis
- Tela de detalhes por jogo e perfis configuráveis por aplicativo.
- Histórico de bateria/temperatura durante a sessão (com serviço em primeiro plano e notificação, respeitando as regras do Android).
- Integração opcional com modos de jogo fornecidos pelo fabricante, quando houver API pública.


## Compilar pelo GitHub (sem Android Studio)

1. Crie um repositório no GitHub pelo navegador e envie todos os arquivos desta pasta, incluindo a pasta oculta `.github/workflows`.
2. Abra a aba **Actions** do repositório.
3. Se aparecer uma tela pedindo autorização, habilite GitHub Actions para o repositório.
4. Abra o workflow **Build Android APK** e toque em **Run workflow**. Um push na branch `main` também inicia a compilação.
5. Aguarde o workflow ficar verde e abra a execução concluída.
6. Na seção **Artifacts**, baixe `MobileGameBooster-debug`.
7. Extraia o ZIP do artifact para encontrar `app-debug.apk` e instale no celular. Se o Android pedir, permita instalação dessa fonte.

O APK gerado é de depuração (debug). Para distribuir publicamente, gere uma versão release assinada com uma chave própria.
