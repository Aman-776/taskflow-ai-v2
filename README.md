TaskFlow AI

Next.js Tailwind CSS Supabase Gemini AI
🚀 The Elevator Pitch

A high-performance, full-stack Kanban task manager that seamlessly blends real-time database syncing with generative AI. Built to demonstrate advanced React state management, asynchronous server-client communication, and clean API architecture.
🧠 Why I Built It

Most task managers are static CRUD apps. I wanted to build something that feels alive. TaskFlow AI proves I can handle complex state (managing separate inputs for 3 different columns without bleeding state), wire up a relational database (Projects -> Tasks) using Supabase, and securely pass that data to an LLM to generate actionable insights—all in a sleek, dark-mode interface.
🛠️ The Architecture

    Frontend: Next.js 15 (App Router), Tailwind CSS. Minimalist, dark-mode UI built for focus.
    State Management: React useState and useEffect. Handles optimistic UI updates and asynchronous database fetching without flickering or state collision.
    Database: Supabase (Postgres). Relational schema connecting Projects to Tasks with a status enum (todo, in_progress, done).
    AI Integration: Next.js API Routes securely proxy requests to Google Gemini 1.5 Flash. The frontend sends the current task array, and the backend returns a formatted, context-aware summary.
    Development Speed: Vibe-coded architecture using AI-augmented workflows to ship production-ready features in hours, not weeks.

🚀 Local Setup

Requires Node.js, a Supabase project, and a Google AI Studio API key.

git clone https://github.com/Aman-776/taskflow-ai-v2.gitcd taskflow-ai-v2npm installnpm run dev

 
Environment Variables (.env.local) 
text
 
  
 
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_key
GOOGLE_AI_KEY=your_gemini_key
 
 
 
Database Schema 

Run this in your Supabase SQL Editor to generate the tables: 
sql
 
  
 
create table projects (
  id uuid default gen_random_uuid() primary key,
  title text not null,
  created_at timestamptz default now()
);

create table tasks (
  id uuid default gen_random_uuid() primary key,
  title text not null,
  status text default 'todo' check (status in ('todo', 'in_progress', 'done')),
  project_id uuid references projects(id) on delete cascade,
  position integer default 0,
  created_at timestamptz default now()
);
 
 
 
📫 Contact 

Built by Amanuel | Full-Stack Vibe Coder & Web3 Security Researcher 
