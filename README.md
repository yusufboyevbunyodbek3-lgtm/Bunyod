/saytds-anime
├── /components      # UI elementlari (Player, Card, Navbar)
├── /pages           # Sahifalar (Home, Watch, Search)
├── /public          # Rasmlar va ikonlar
├── /styles          # CSS dizaynlari
└── package.json     # Kutubxonalar ro'yxati
// pages/watch/[id].js
import { useRouter } from 'next/router';

export default function Watch() {
  const router = useRouter();
  const { id, episode } = router.query; // Anime ID va qism raqami

  // Bu yerda video manbasi (masalan, Telegram yoki player linki)
  const videoSrc = `https://your-video-provider.com/embed/${id}?ep=${episode}`;

  return (
    <div className="video-container">
      <h1>Anime ko'rish: {id}</h1>
      <div className="player-wrapper">
        <iframe 
          src={videoSrc} 
          width="100%" 
          height="500px" 
          allowFullScreen 
          frameBorder="0">
        </iframe>
      </div>
      <div className="episode-list">
        <h3>Qismlar:</h3>
        {/* Qismlar tugmachalari shu yerda bo'ladi */}
      </div>
    </div>
  );
}
{
  "anime_name": "Naruto",
  "poster": "https://image.url/poster.jpg",
  "description": "Ninja haqida sarguzashtlar",
  "episodes": [
    {"number": 1, "link": "https://vido.uz/e/123"},
    {"number": 2, "link": "https://vido.uz/e/124"}
  ]
}
git clone https://github.com/riimuru/gogoanime.git
cd gogoanime
npm install
npm run dev
