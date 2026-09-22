# Ensaio — frontend

O piloto de análise de discurso, agora como site próprio (fora do Claude),
conectado de verdade ao backend em ensaio-backend.onrender.com.

## O que mudou em relação à versão de dentro do Claude

- Upload de vídeo no módulo de voz agora também manda o arquivo pro
  servidor automaticamente — a transcrição e a leitura de rosto/corpo
  preenchem sozinhas, sem precisar rodar `analise_corporal.py` na mão nem
  colar JSON (esse campo continua existindo como reserva, caso o servidor
  esteja fora do ar).
- "Salvar e comparar sessões" agora usa o armazenamento do próprio
  navegador (`localStorage`) em vez de conta do Claude — funciona sem
  login, mas fica só nesse navegador/computador, não sincroniza entre
  dispositivos.

## Publicar no Render (mesmo jeito do backend)

1. Crie um repositório novo no GitHub — por exemplo `ensaio-frontend` —
   e suba esse `index.html` (arraste o arquivo pra área de upload, igual
   fizemos com o backend).
2. No Render, clique em **New +** → **Static Site** (não é "Web Service"
   dessa vez — site estático não roda servidor, só entrega arquivos).
3. Conecte o repositório `ensaio-frontend`.
4. Em **Build Command**, deixe em branco (não tem nada pra construir,
   é só HTML puro).
5. Em **Publish Directory**, coloque `.` (a raiz do repositório).
6. Clique em **Create Static Site**.

Site estático é ainda mais rápido de publicar que o backend — geralmente
menos de um minuto, sem instalar nada.

## Depois de publicado

O Render te dá uma URL tipo `https://ensaio-frontend-xxxx.onrender.com`
— esse é o link que vocês vão passar pros alunos, não mais o link do
Claude.

## Se precisar trocar o endereço do backend

Se o backend mudar de endereço no futuro, é só editar uma linha no
`index.html`:

```js
var ENSAIO_BACKEND_URL = 'https://ensaio-backend.onrender.com';
```
