# Neighbourhood

Rede social hiperlocal de bairro — moradores reportam problemas, organizam eventos e acompanham o pulso da vizinhança em tempo real.

## Sobre o projeto

O Neighbourhood é um app mobile e web desenvolvido com React Native (Expo) e Supabase como backend. Moradores cadastram-se informando seu bairro e cidade, e passam a ver apenas o conteúdo relevante para a sua região. É possível reportar problemas urbanos (buracos, iluminação, lixo), criar eventos, deixar avisos e elogios — tudo com acompanhamento em tempo real e um dashboard de métricas do bairro.

Projeto desenvolvido como estudo prático de Supabase, cobrindo autenticação, banco de dados relacional com PostGIS, Row Level Security, Realtime e Storage.

## Tecnologias

- [Expo](https://expo.dev) com Expo Router (suporte mobile e web)
- [React Native](https://reactnative.dev)
- [Supabase](https://supabase.com) — Auth, PostgreSQL, PostGIS, Realtime, Storage
- TypeScript

## Funcionalidades

- Cadastro e login com e-mail
- Feed do bairro em tempo real
- Criação de posts por categoria: problema, evento, aviso, elogio
- Sistema de votos nos posts
- Comentários
- Acompanhamento de status dos reportes (aberto, em andamento, resolvido)
- Dashboard com métricas do bairro
- Perfil com sistema de reputação
- Filtro geoespacial por raio de distância (PostGIS)

## Pré-requisitos

- Node.js 20+
- Expo Go instalado no celular (para testar em dispositivo físico)
- Conta no [Supabase](https://supabase.com)

## Instalação

Clone o repositório e instale as dependências:

```bash
git clone https://github.com/seu-usuario/neighbourhood.git
cd neighbourhood
npm install --legacy-peer-deps
```

## Configuração

Crie um arquivo `.env` na raiz do projeto com as chaves do seu projeto no Supabase:

```env
EXPO_PUBLIC_SUPABASE_URL=https://seu-projeto.supabase.co
EXPO_PUBLIC_SUPABASE_ANON_KEY=eyJhbGci...
```

As chaves ficam em **Settings → API** no dashboard do Supabase.

## Banco de dados

No **SQL Editor** do Supabase, execute os scripts na seguinte ordem:

1. `sql/schema.sql` — cria as tabelas e extensão PostGIS
2. `sql/rls.sql` — configura as políticas de Row Level Security
3. `sql/triggers.sql` — cria o trigger de criação automática de perfil

## Rodando o projeto

```bash
npx expo start
```

Opções disponíveis no terminal:

- `i` — abre no simulador iOS (somente macOS)
- `a` — abre no emulador Android
- `w` — abre no navegador
- Escaneie o QR code com o app Expo Go no celular

## Estrutura do projeto

```
neighbourhood/
├── app/
│   ├── (auth)/          # Telas de login e cadastro
│   ├── (app)/           # Telas principais (feed, dashboard, perfil)
│   └── _layout.tsx      # Root layout com auth guard
├── lib/
│   └── supabase.ts      # Cliente Supabase
├── components/          # Componentes reutilizáveis
├── hooks/               # Hooks customizados
└── types/               # Tipagens TypeScript
```

## Variáveis de ambiente

| Variável | Descrição |
|---|---|
| `EXPO_PUBLIC_SUPABASE_URL` | URL do projeto no Supabase |
| `EXPO_PUBLIC_SUPABASE_ANON_KEY` | Chave pública anon do Supabase |

O arquivo `.env` não vai para o repositório. Use `.env.example` como referência.

## Licença

MIT
