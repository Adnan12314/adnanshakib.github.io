# Yamin Portfolio Clone — Full Project

This single-file project document contains a minimal, production-ready Next.js + Tailwind + Framer Motion portfolio template inspired by the site you shared. Copy the files into a new Next.js project (or use `npx create-next-app`) and replace placeholders (name, projects, images) with your real content.

---

// File: package.json
{
  "name": "yamin-portfolio-clone",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "framer-motion": "^10.12.16",
    "next": "14.2.1",
    "react": "18.2.0",
    "react-dom": "18.2.0"
  },
  "devDependencies": {
    "autoprefixer": "^10.4.14",
    "postcss": "^8.4.24",
    "tailwindcss": "^3.6.2"
  }
}

---

// File: tailwind.config.js
module.exports = {
  content: [
    './pages/**/*.{js,ts,jsx,tsx}',
    './components/**/*.{js,ts,jsx,tsx}'
  ],
  theme: {
    extend: {
      colors: {
        primary: '#0ea5a4',
        accent: '#7c3aed'
      }
    }
  },
  plugins: []
};

---

// File: postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {}
  }
};

---

// File: pages/_app.js
import '../styles/globals.css'

export default function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />
}

---

// File: pages/index.js
import Head from 'next/head'
import Nav from '../components/Nav'
import Hero from '../components/Hero'
import Projects from '../components/Projects'
import Contact from '../components/Contact'

export default function Home() {
  return (
    <>
      <Head>
        <title>Yamin Raad — Portfolio</title>
        <meta name="description" content="Yamin Raad — Web Developer" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
      </Head>
      <div className="min-h-screen bg-gradient-to-b from-white to-gray-50 text-gray-900">
        <Nav />
        <main className="max-w-5xl mx-auto px-6 py-12">
          <Hero />
          <Projects />
          <Contact />
        </main>
      </div>
    </>
  )
}

---

// File: components/Nav.js
import Link from 'next/link'

export default function Nav() {
  return (
    <nav className="w-full py-6 border-b bg-white/60 backdrop-blur-sm sticky top-0 z-30">
      <div className="max-w-5xl mx-auto px-6 flex items-center justify-between">
        <Link href="/">
          <a className="font-bold text-lg">Yamin&nbsp;Raad</a>
        </Link>

        <div className="space-x-4">
          <a href="#projects" className="text-sm hover:underline">Projects</a>
          <a href="#contact" className="text-sm hover:underline">Contact</a>
          <a href="/resume.pdf" className="text-sm font-medium px-3 py-1 rounded-md border">Resume</a>
        </div>
      </div>
    </nav>
  )
}

---

// File: components/Hero.js
import { motion } from 'framer-motion'

export default function Hero() {
  return (
    <section className="mt-8 grid gap-8 md:grid-cols-2 items-center">
      <div>
        <motion.h1
          initial={{ opacity: 0, y: 10 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.5 }}
          className="text-4xl md:text-5xl font-extrabold leading-tight"
        >
          Hi, I’m <span className="text-primary">Yamin Raad</span> — a web developer building
          modern, fast and delightful experiences.
        </motion.h1>

        <motion.p
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ delay: 0.2 }}
          className="mt-6 text-gray-600"
        >
          I design and develop responsive web apps using Next.js, Tailwind CSS and Framer Motion.
          Currently available for freelance and full‑time roles.
        </motion.p>

        <div className="mt-6 flex gap-3">
          <a href="#projects" className="inline-block px-5 py-3 rounded-md bg-primary text-white font-medium">See projects</a>
          <a href="#contact" className="inline-block px-5 py-3 rounded-md border">Contact</a>
        </div>

        <div className="mt-8 text-sm text-gray-500">
          <strong>Tech:</strong> Next.js • Tailwind CSS • Framer Motion • JavaScript
        </div>
      </div>

      <motion.div
        initial={{ opacity: 0, scale: 0.98 }}
        animate={{ opacity: 1, scale: 1 }}
        transition={{ duration: 0.6 }}
        className="w-full flex justify-center md:justify-end"
      >
        <div className="w-72 h-72 rounded-2xl shadow-lg overflow-hidden bg-gradient-to-br from-indigo-100 to-teal-50 flex items-center justify-center">
          {/* Replace with your headshot or illustration inside public/hero.jpg */}
          <span className="text-gray-400">Your image here</span>
        </div>
      </motion.div>
    </section>
  )
}

---

// File: components/Projects.js
import { motion } from 'framer-motion'

const projects = [
  {
    id: 1,
    title: 'Project One',
    desc: 'A short description of project one. Built with Next.js and Tailwind CSS.',
    link: '#'
  },
  {
    id: 2,
    title: 'Project Two',
    desc: 'A short description of project two. Includes animation and API integration.',
    link: '#'
  },
  {
    id: 3,
    title: 'Project Three',
    desc: 'A short description of project three. Responsive and performant.',
    link: '#'
  }
]

export default function Projects() {
  return (
    <section id="projects" className="mt-16">
      <h2 className="text-2xl font-bold">Featured Projects</h2>
      <p className="mt-2 text-gray-600">Selected projects with short descriptions and links.</p>

      <div className="mt-6 grid gap-6 md:grid-cols-2">
        {projects.map((p, i) => (
          <motion.a
            key={p.id}
            href={p.link}
            className="block p-5 border rounded-xl hover:shadow-md transition-shadow bg-white"
            initial={{ opacity: 0, y: 8 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ delay: i * 0.08 }}
          >
            <h3 className="text-lg font-semibold">{p.title}</h3>
            <p className="mt-2 text-gray-600 text-sm">{p.desc}</p>
            <div className="mt-4 text-sm font-medium text-primary">View project →</div>
          </motion.a>
        ))}
      </div>
    </section>
  )
}

---

// File: components/Contact.js
export default function Contact() {
  return (
    <section id="contact" className="mt-16 mb-24">
      <h2 className="text-2xl font-bold">Get in touch</h2>
      <p className="mt-2 text-gray-600">Available for freelance or full‑time opportunities. Send me a message:</p>

      <div className="mt-6 max-w-xl">
        <form action="mailto:your-email@example.com" method="GET" encType="text/plain" className="space-y-4">
          <input placeholder="Your name" className="w-full px-4 py-2 border rounded-md" />
          <input placeholder="Email" className="w-full px-4 py-2 border rounded-md" />
          <textarea placeholder="Message" rows="4" className="w-full px-4 py-2 border rounded-md"></textarea>
          <div>
            <button type="submit" className="px-5 py-3 rounded-md bg-accent text-white">Send message</button>
          </div>
        </form>
      </div>
    </section>
  )
}

---

// File: styles/globals.css
@tailwind base;
@tailwind components;
@tailwind utilities;

html, body, #__next {
  height: 100%;
}

body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Small helper */
.container {
  max-width: 1200px;
  margin-left: auto;
  margin-right: auto;
  padding-left: 1.25rem;
  padding-right: 1.25rem;
}

---

// File: public/README.md
Place your static assets here:
- /public/hero.jpg -> hero image
- /public/project-1.png -> project thumbnails

---

# How to run
1. Save files into a new folder.
2. Run `npm install`.
3. Run `npm run dev`.
4. Open http://localhost:3000

---

# Notes & Customization
- Replace placeholder text (name, email, project descriptions) with your real content.
- Add real images into `/public` and swap the hero placeholder.
- To deploy on Vercel: connect the GitHub repo and push — Vercel detects Next.js automatically.

Good luck! Replace the contents with your own portfolio data and let me know if you want extra pages (blog, case study), CMS integration, or direct GitHub-ready repository structure.
