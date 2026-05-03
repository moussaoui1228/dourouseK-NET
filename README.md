# dourouseK-NET
Key Features

    Dual Roles: Tailored experiences for both Students and Professors.
    Session Management: Easily schedule, confirm, or cancel tutoring sessions.
    Resource Hub: Centralized sharing of assignments, corrections, and documents (PDF support).
    Modern UI: A stunning glassmorphic design with smooth animations powered by Framer Motion.
    Real-time Backend: Powered by Supabase for secure authentication and real-time data management.

Tech Stack

    Frontend: Next.js 15+ (App Router), React 19
    Styling: Vanilla CSS with Glassmorphism and Custom Design Tokens
    Animations: Framer Motion
    Icons: Lucide React
    Database & Auth: Supabase
    Language: TypeScript

Getting Started
Prerequisites

    Node.js 18.x or later
    npm or yarn
    A Supabase account and project

Installation

    Clone the repository:

    git clone https://github.com/yourusername/dourousek_net.git
    cd dourousek_net

    Install dependencies:

    npm install

    Set up Environment Variables: Create a .env.local file in the root directory and add your Supabase credentials:

    NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
    NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

    Initialize Database:
        Option A (SQL Editor): Run the SQL scripts located in the /supabase directory within your Supabase SQL editor to set up the schema.
        Option B (Browser Seed): Once the app is running, navigate to /seed to automatically create demo professor accounts.

    Run the development server:

    npm run dev

    Open http://localhost:3000 with your browser to see the result.

Seeding Data

To quickly get started with sample data, DourousNet includes a built-in seeding utility:

    Ensure your Supabase environment variables are set.
    Visit http://localhost:3000/seed in your browser.
    Click the "Créer les 4 professeurs" button to automatically populate your database with expert demo profiles.

Project Structure

    src/app: Next.js App Router pages and layouts.
    src/lib: Shared utility functions and Supabase client configuration.
    supabase/: SQL migration and seed files for the database schema.
    public/: Static assets.

Design Philosophy

DourousNet uses a Glassmorphic design language, characterized by:

    Translucent backgrounds with background-blur effects.
    Multi-layered approach with subtle shadows.
    Vibrant, curated gradients.
    Modern typography using the 'Outfit' font family.



 1. Mapping de notre Thème
Thème du projet :" DourousNet" est une plateforme moderne de mise en relation et de gestion pour le soutien scolaire, permettant de connecter professeurs et étudiants tout en facilitant la planification des cours et le partage de ressources.

*   Table A : `professors` (Les enseignants/tuteurs proposant leurs services sur la plateforme).
*   Table B :*`students` (Les élèves inscrits recherchant du soutien scolaire).
*   Table C : `sessions` (Les séances de cours planifiées, agissant comme table d'événement/liaison entre un professeur et un étudiant).
*   Fichier : Les documents pédagogiques (PDFs de devoirs, corrections, supports de cours) gérés via Supabase Storage.

 2. Analyse d'Architecture

-Financement (OPEX vs CAPEX)
Le choix du couple Vercel + Supabase s'avère bien plus logique financièrement pour le lancement de ce projet par rapport à l'achat d'un serveur classique. L'acquisition d'un serveur physique implique un investissement de départ conséquent, appelé **CAPEX** (Capital Expenditure) : achat du matériel serveur, licences, installation. À l'inverse, Vercel et Supabase reposent sur le modèle Cloud et Serverless. Cela permet de transformer ces coûts en **OPEX** (Operational Expenditure), c'est-à-dire des dépenses d'exploitation courantes. Avec une tarification "Pay-as-you-go" (paiement à l'usage), le projet peut démarrer sans frais initiaux avec les tiers gratuits, et nous ne paierons que pour les ressources réellement consommées si l'application rencontre du succès.

-Scalabilité (Vercel vs Data Center local)
Dans un Data Center physique local, absorber un pic soudain d'utilisateurs nécessite d'anticiper la charge en achetant et en installant manuellement de nouveaux serveurs en rack, tout en redimensionnant l'infrastructure environnante (puissance de la climatisation, alimentation électrique, onduleurs). C'est un processus lourd et très rigide. Vercel gère la scalabilité de manière automatique et "élastique". La plateforme déploie les fonctions Serverless et les assets sur son réseau mondial. Si le trafic explose soudainement, Vercel alloue instantanément et automatiquement la puissance de calcul et la bande passante nécessaires, sans aucune intervention humaine et sans contraintes de place ou de climatisation.

-Données Structurées vs Non-structurées
Dans notre application DourousNet :
*   **Les données Structurées :** Il s'agit des informations stockées dans notre base de données relationnelle PostgreSQL (Supabase). Elles respectent un schéma strict avec des colonnes et des types définis : les informations des utilisateurs (`professors`, `students`) ou les métadonnées des cours (`sessions` avec date, heure, statut).
*   **Les données Non-structurées :** Il s'agit des fichiers bruts stockés. Dans notre cas, ce sont les supports de cours, les devoirs ou les corrections au format PDF uploadés par les professeurs et les étudiants, qui sont gérés via Supabase Storage. Ils n'ont pas de structure de base de données inhérente.