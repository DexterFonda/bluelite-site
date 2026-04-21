# bluelite-site
Site de BlueLiteRp le serveur menta US rp  Fun crée par Yasko , Tirvin &amp; Rapido
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Users, Image, ShoppingCart, Shield, Server, Copy } from "lucide-react";

export default function BlueLiteSite() {
  const [players] = useState(128);
  const [page, setPage] = useState("home");

  const logo = "/6df735e4-22df-4c9c-b9f6-4bcf7e7226eb.png";

  const staff = [
    { name: "Fondateur", role: "Owner" },
    { name: "Admin 1", role: "Admin" },
    { name: "Dev 1", role: "Dev" },
    { name: "Modérateur 1", role: "Mod" },
  ];

  const copyIP = () => {
    navigator.clipboard.writeText("connect 127.0.0.1");
    alert("IP copiée !");
  };

  const NavBar = () => (
    <nav className="flex justify-center gap-6 p-4 bg-black border-b border-zinc-800 relative z-20">
      <button onClick={() => setPage("home")} className="hover:text-blue-400">Accueil</button>
      <button onClick={() => setPage("staff")} className="hover:text-blue-400">Staff</button>
      <button onClick={() => setPage("shop")} className="hover:text-blue-400">Boutique</button>
      <button onClick={() => setPage("connect")} className="hover:text-blue-400">Connexion</button>
    </nav>
  );

  return (
    <div className="min-h-screen text-white bg-black relative overflow-hidden">

      {/* 🎥 VIDEO BACKGROUND GTA */}
      <video
        autoPlay
        muted
        loop
        className="absolute w-full h-full object-cover opacity-30"
      >
        <source src="/gta-trailer.mp4" type="video/mp4" />
      </video>

      <div className="absolute inset-0 bg-gradient-to-b from-black via-black/70 to-black"></div>

      <div className="relative z-10">

        <NavBar />

        {/* HOME */}
        {page === "home" && (
          <>
            <header className="text-center py-16">
              <img src={logo} className="w-24 mx-auto mb-4" />
              <h1 className="text-5xl font-bold">🔵 BlueLite</h1>
              <p className="text-gray-300">Serveur FiveM Roleplay</p>
              <p className="text-green-400 mt-2">🟢 Joueurs en ligne : {players}</p>
            </header>

            <section className="grid md:grid-cols-3 gap-6 p-10">
              <Card><CardContent className="p-6 text-center"><Server /><p>Serveur RP sérieux</p></CardContent></Card>
              <Card><CardContent className="p-6 text-center"><Users /><p>Communauté active</p></CardContent></Card>
              <Card><CardContent className="p-6 text-center"><Shield /><p>Staff actif 24/7</p></CardContent></Card>
            </section>

            <section className="p-10 text-center">
              <h2 className="text-3xl font-bold mb-4">🎮 Se connecter</h2>
              <Button onClick={copyIP} className="bg-blue-600">
                <Copy className="mr-2" /> Copier IP
              </Button>
              <p className="mt-4 text-gray-400">connect 127.0.0.1</p>
            </section>
          </>
        )}

        {/* STAFF */}
        {page === "staff" && (
          <section className="p-10">
            <h2 className="text-3xl font-bold mb-6">👮 Staff</h2>
            <div className="grid md:grid-cols-4 gap-4">
              {staff.map((s, i) => (
                <Card key={i} className="bg-zinc-900 text-center">
                  <CardContent className="p-4">
                    <p className="font-bold">{s.name}</p>
                    <span className={`text-sm px-2 py-1 rounded ${
                      s.role === "Owner" ? "bg-red-600" :
                      s.role === "Admin" ? "bg-blue-600" :
                      s.role === "Dev" ? "bg-purple-600" : "bg-green-600"
                    }`}>{s.role}</span>
                  </CardContent>
                </Card>
              ))}
            </div>
          </section>
        )}

        {/* SHOP */}
        {page === "shop" && (
          <section className="p-10 text-center bg-black/60">
            <img src={logo} className="w-20 mx-auto mb-4" />
            <h2 className="text-3xl font-bold">🛒 Boutique Coins</h2>

            <div className="grid md:grid-cols-3 gap-4 max-w-4xl mx-auto mt-6">
              <Card><CardContent className="p-4"><p>1000 Coins</p><p className="text-green-400">10€</p></CardContent></Card>
              <Card><CardContent className="p-4"><p>2000 Coins</p><p className="text-green-400">20€</p></CardContent></Card>
              <Card><CardContent className="p-4"><p>5000 Coins</p><p className="text-green-400">50€</p></CardContent></Card>
            </div>
          </section>
        )}

        {/* CONNECT */}
        {page === "connect" && (
          <section className="p-10 text-center">
            <h2 className="text-3xl font-bold">🎮 Connexion Serveur</h2>
            <div className="bg-zinc-900 p-4 mt-6 inline-block rounded">
              connect 127.0.0.1
            </div>
          </section>
        )}

        <footer className="text-center p-6 text-gray-500">
          © 2026 BlueLite RP
        </footer>
      </div>
    </div>
  );
}

