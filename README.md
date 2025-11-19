# Pintor Caro — Projeto Next.js + Tailwind

Abaixo está uma estrutura completa de projeto Next.js (App Router) com Tailwind. Cada arquivo está separado por cabeçalhos para facilitar a cópia.

---

## package.json
```json
{
  "name": "pintorcaro-site",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  },
  "dependencies": {
    "next": "14.1.0",
    "react": "18.2.0",
    "react-dom": "18.2.0"
  },
  "devDependencies": {
    "tailwindcss": "^3.4.1",
    "postcss": "^8.4.27",
    "autoprefixer": "^10.4.14"
  }
}
```

---

## tailwind.config.js
```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./app/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}"
  ],
  theme: {
    extend: {
      colors: {
        primary: "#1f7a6f",
        primaryLight: "#2fb6a1"
      }
    }
  },
  plugins: []
};
```

---

## postcss.config.js
```js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {}
  }
};
```

---

## app/globals.css
```css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  @apply bg-gray-100 text-gray-900;
}
```

---

## app/layout.tsx
```tsx
import "./globals.css";
import { ReactNode } from "react";

export const metadata = {
  title: "Pintor Caro — Pintores Profissionais",
  description: "Pintura residencial e comercial com entrega rápida e garantia.",
};

export default function RootLayout({ children }: { children: ReactNode }) {
  return (
    <html lang="pt-BR">
      <body className="font-sans">{children}</body>
    </html>
  );
}
```

---

## app/components/Header.tsx
```tsx
export default function Header() {
  return (
    <header className="max-w-6xl mx-auto p-6 flex items-center justify-between">
      <div className="flex items-center gap-3">
        <div className="w-14 h-14 rounded-xl bg-gradient-to-br from-primaryLight to-primary flex items-center justify-center text-white font-bold text-xl">
          PC
        </div>
        <div>
          <div className="font-bold text-lg">Pintor Caro</div>
          <div className="text-xs text-gray-500">Curitiba e Região Metropolitana • Reformas • Acabamento</div>
        </div>
      </div>
      <nav className="hidden md:flex gap-6 text-gray-500 font-medium">
        <a href="#servicos" className="hover:text-primary">Serviços</a>
        <a href="#projetos" className="hover:text-primary">Projetos</a>
        <a href="#contato" className="hover:text-primary">Contato</a>
      </nav>
    </header>
  );
}
```

---

## app/components/Hero.tsx
```tsx
export default function Hero() {
  return (
    <section className="bg-white shadow-md rounded-xl max-w-6xl mx-auto p-8 grid md:grid-cols-2 gap-8 mt-6">
      <div>
        <div className="text-primary font-semibold">Pintura Profissional</div>
        <h1 className="text-3xl font-bold mt-2 mb-3 leading-tight">
          Pintura residencial e comercial com entrega rápida e garantia
        </h1>
        <p className="text-gray-600">
          Serviços completos: preparação de superfícies, pintura interna e externa,
          texturas, grafiato e retoques. Orçamento transparente e equipe qualificada. Atendemos Curitiba e toda a Região Metropolitana do Paraná.
        </p>

        <div className="flex flex-wrap gap-2 mt-4">
          <span className="bg-primary/10 text-primary font-semibold px-3 py-1 rounded-full">Orçamento grátis</span>
          <span className="bg-primary/10 text-primary font-semibold px-3 py-1 rounded-full">Marcas confiáveis</span>
          <span className="bg-primary/10 text-primary font-semibold px-3 py-1 rounded-full">Garantia</span>
        </div>

        <div className="flex flex-wrap gap-3 mt-5">
          <a className="bg-primary text-white px-4 py-2 rounded-lg font-semibold" href="#">Ver orçamentos</a>
          <a className="border-2 border-primary text-primary px-4 py-2 rounded-lg font-semibold" href="#contato">Pedir orçamento</a>
          <a className="bg-primary text-white px-4 py-2 rounded-lg font-semibold" href="https://wa.me/5541984791324" target="_blank">WhatsApp</a>
        </div>
      </div>

      <aside className="bg-white border p-5 rounded-xl h-fit">
        <h3 className="text-xl font-semibold mb-4">Peça seu orçamento</h3>
        <form className="space-y-3">
          <input className="w-full border rounded-lg px-3 py-2" placeholder="Nome" />
          <input className="w-full border rounded-lg px-3 py-2" placeholder="Telefone/WhatsApp" />
          <input className="w-full border rounded-lg px-3 py-2" placeholder="Endereço (cidade/bairro)" />
          <select className="w-full border rounded-lg px-3 py-2">
            <option>Pintura interna</option>
            <option>Pintura externa</option>
            <option>Textura / Grafiato</option>
            <option>Retoques / Reforma</option>
          </select>
          <textarea className="w-full border rounded-lg px-3 py-2 h-24" placeholder="Descreva o serviço"></textarea>
          <button className="bg-primary text-white px-4 py-2 rounded-lg font-semibold w-full">Enviar pedido</button>
        </form>
      </aside>
    </section>
  );
}
```

---

## app/components/Servicos.tsx
```tsx
export default function Servicos() {
  return (
    <section id="servicos" className="max-w-6xl mx-auto mt-10 p-4">
      <h2 className="text-2xl font-bold mb-4">Nossos serviços</h2>
      <div className="grid md:grid-cols-3 gap-4">
        {[{
          title: "Pintura Interna",
          desc: "Preparação, massa corrida, lixa e acabamento impecável.",
          price: "A partir de R$ 30/m²*"
        },{
          title: "Pintura Externa",
          desc: "Selantes, impermeabilização, primer e tinta para fachadas.",
          price: "A partir de R$ 30/m²*"
        },{
          title: "Texturas e Grafiato",
          desc: "Aplicação de texturas decorativas e grafiato.",
          price: "Orçamento sob medida"
        }].map((s, i) => (
          <div key={i} className="bg-white p-4 rounded-xl shadow-sm">
            <h4 className="font-semibold">{s.title}</h4>
            <p className="text-gray-600 mt-2">{s.desc}</p>
            <div className="font-semibold mt-2">{s.price}</div>
          </div>
        ))}
      </div>
      <p className="text-gray-500 text-sm mt-2">*Valores aproximados. O preço final depende do estado da superfície.</p>
    </section>
  );
}
```

---

## app/page.tsx
```tsx
import Header from "./components/Header";
import Hero from "./components/Hero";
import Servicos from "./components/Servicos";

export default function Page() {
  return (
    <>
      <Header />
      <Hero />
      <Servicos />
      <footer className="text-center text-gray-500 text-sm mt-10 p-6">
        © {new Date().getFullYear()} Pintor Caro — Todos os direitos reservados
      </footer>
    </>
  );
}
```

---

Se quiser, posso adicionar:
✅ Animações com Framer Motion
✅ Página de portfólio completa
✅ Sistema de depoimentos
✅ SEO completo (Open Graph, Rich Snippets)
✅ Envio real do formulário via WhatsApp ou API

Basta pedir! 🚀