# projeto56500 — Sistema de Videoconferência Básico

## Descrição

Sistema de videoconferência simples desenvolvido para fins de aprendizado e prototipagem.
Permite capturar e exibir a câmera do usuário diretamente pelo navegador, sem necessidade de instalação de software adicional.

## Status atual

> **Por enquanto, o sistema somente captura a câmera local.**
> Funcionalidades como transmissão entre usuários, áudio e chat ainda não foram implementadas.

---

## Objetivo do projeto

Criar uma videoconferência funcional e minimalista, rodando no navegador, sem backend complexo, sem autenticação e sem dependência de serviços externos.

---

## Tecnologias necessárias

### Frontend (tudo que é necessário por enquanto)

| Tecnologia               | Finalidade                                                                            |
| ------------------------ | ------------------------------------------------------------------------------------- |
| **HTML5**                | Estrutura da página e elemento `<video>` para exibir a câmera                         |
| **CSS3**                 | Estilização básica da interface                                                       |
| **JavaScript (vanilla)** | Lógica de captura e controle do stream de vídeo                                       |
| **MediaDevices API**     | API nativa do navegador para acessar câmera e microfone (`getUserMedia`)              |
| **WebRTC**               | Protocolo para transmissão de áudio/vídeo peer-to-peer _(necessário na próxima fase)_ |

### Backend _(para a fase de transmissão entre usuários)_

| Tecnologia            | Finalidade                                                                    |
| --------------------- | ----------------------------------------------------------------------------- |
| **Node.js + Express** | Servidor HTTP simples para servir os arquivos estáticos                       |
| **Socket.IO**         | Comunicação em tempo real para sinalização WebRTC (troca de offer/answer/ICE) |

### Infraestrutura _(mínima)_

| Tecnologia            | Finalidade                                                    |
| --------------------- | ------------------------------------------------------------- |
| **Laragon**           | Servidor local de desenvolvimento                             |
| **Navegador moderno** | Chrome, Firefox ou Edge com suporte a WebRTC e `getUserMedia` |

---

## Como funciona (fase atual)

1. O navegador solicita permissão de acesso à câmera.
2. A API `navigator.mediaDevices.getUserMedia()` captura o stream de vídeo.
3. O stream é exibido em um elemento `<video>` na página.

```js
navigator.mediaDevices
  .getUserMedia({ video: true, audio: false })
  .then((stream) => {
    document.querySelector("video").srcObject = stream;
  });
```

---

## Roadmap (próximas etapas)

- [ ] Captura de câmera (fase atual)
- [ ] Captura de microfone
- [ ] Transmissão peer-to-peer via WebRTC
- [ ] Sala simples com URL compartilhável
- [ ] Chat de texto básico

---

## Observações

- Sem login.
- Sem autenticação.
- Sem criptografia.
- Projeto educacional e de protótipo — não apto para uso em produção.
