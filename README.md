"use client"

import { useState } from "react"
import { Shield, Search, Code, Wifi, Terminal, Apple, Monitor, Globe } from "lucide-react"

const skills = [
  { name: "Metasploit", icon: Shield },
  { name: "Burp Suite", icon: Search },
  { name: "Python", icon: Code },
  { name: "Wireshark", icon: Wifi },
  { name: "Linux", icon: Terminal },
  { name: "macOS", icon: Apple },
  { name: "Windows", icon: Monitor },
]

export default function GitHubPortfolio() {
  const [language, setLanguage] = useState<"rus" | "eng">("eng")

  const toggleLanguage = () => {
    setLanguage((prev) => (prev === "eng" ? "rus" : "eng"))
  }

  const translations = {
    skills: language === "eng" ? "Skills" : "Навыки",
    language: language === "eng" ? "Language" : "Язык",
  }

  return (
    <div className="min-h-screen bg-black text-white flex flex-col items-center justify-center p-8">
      {/* Animated Username */}
      <div className="mb-16">
        <h1 className="text-6xl md:text-8xl font-thin tracking-wider animate-pulse">0dayloran</h1>
      </div>

      <div className="flex flex-col lg:flex-row gap-16 items-start">
        {/* Skills Section */}
        <div className="flex flex-col items-center">
          <h2 className="text-2xl font-light mb-8 tracking-wide">{translations.skills}</h2>

          <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
            {skills.map((skill, index) => {
              const IconComponent = skill.icon
              return (
                <div
                  key={skill.name}
                  className="group flex flex-col items-center p-4 border border-white/20 rounded-lg 
                           hover:border-white/40 hover:scale-105 transition-all duration-300 
                           cursor-pointer min-w-[120px]"
                >
                  <IconComponent
                    size={32}
                    className="mb-3 text-white/80 group-hover:text-white transition-colors duration-300"
                  />
                  <span className="text-sm font-light text-center text-white/80 group-hover:text-white transition-colors duration-300">
                    {skill.name}
                  </span>
                </div>
              )
            })}
          </div>
        </div>

        {/* Language Section */}
        <div className="flex flex-col items-center lg:ml-8">
          <h2 className="text-2xl font-light mb-8 tracking-wide">{translations.language}</h2>

          <div className="flex flex-col gap-3">
            <button
              onClick={toggleLanguage}
              className={`px-6 py-3 border rounded-lg transition-all duration-300 min-w-[100px]
                         ${
                           language === "eng"
                             ? "border-white bg-white text-black"
                             : "border-white/20 hover:border-white/40 hover:scale-105"
                         }`}
            >
              <div className="flex items-center justify-center gap-2">
                <Globe size={16} />
                <span className="font-light">ENG</span>
              </div>
            </button>

            <button
              onClick={toggleLanguage}
              className={`px-6 py-3 border rounded-lg transition-all duration-300 min-w-[100px]
                         ${
                           language === "rus"
                             ? "border-white bg-white text-black"
                             : "border-white/20 hover:border-white/40 hover:scale-105"
                         }`}
            >
              <div className="flex items-center justify-center gap-2">
                <Globe size={16} />
                <span className="font-light">RUS</span>
              </div>
            </button>
          </div>
        </div>
      </div>

      {/* Subtle footer */}
      <div className="mt-16 text-white/30 text-sm font-light">GitHub Portfolio UI</div>
    </div>
  )
}
