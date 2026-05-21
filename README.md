import { motion } from 'motion/react';
import { Github, ExternalLink } from 'lucide-react';

const projects = [
  {
    title: "Telemetría IoT Industrial",
    description: "Desarrollo de nodo IoT con ESP32-S3 para monitorear sensores vía Modbus RTU. Transmite datos mediante MQTT sobre TLS hacia dashboard web.",
    tech: "C++ / FreeRTOS",
    tags: ["#mqtt", "#iot", "#react"],
    github: "https://github.com",
    live: "#"
  },
  {
    title: "Controlador Motor BLDC",
    description: "Diseño esquemático y PCB para controlador Brushless DC basado en STM32G4. Implementa algoritmos FOC (Field Oriented Control).",
    tech: "STM32 / Altium",
    tags: ["#hardware", "#foc"],
    github: "https://github.com"
  },
  {
    title: "Mini-OS RISC-V",
    description: "Sistema operativo educativo tipo UNIX desde cero para arquitectura RISC-V. Incluye manejador de memoria virtual y multihilo.",
    tech: "C / Assembly",
    tags: ["#os", "#risc-v"],
    github: "https://github.com",
    live: "https://example.com"
  },
  {
    title: "Analizador Lógico USB",
    description: "Hardware Open Source. Analizador lógico de 8 canales usando RP2040 integrado con Sigrok/PulseView para decodificación.",
    tech: "RP2040 / KiCad",
    tags: ["#oshw", "#usb"],
    github: "https://github.com"
  }
];

export default function Projects() {
  return (
    <section id="projects" className="flex flex-col flex-1">
      <div className="flex items-center justify-between mb-4">
        <h2 className="text-xs font-mono font-bold tracking-[0.2em] text-white uppercase italic">
          [01] Featured_Repositories
        </h2>
        <div className="h-[1px] flex-1 bg-slate-800 mx-4"></div>
        <a href="https://github.com" className="hidden md:flex items-center gap-1 text-cyan-500 hover:text-cyan-400 font-mono text-[10px] transition-colors uppercase">
          Ver_Archivo <ExternalLink className="w-3 h-3" />
        </a>
      </div>

      <div className="grid grid-cols-1 xl:grid-cols-2 gap-4">
        {projects.map((project, index) => (
          <motion.div
            key={index}
            initial={{ opacity: 0, y: 10 }}
            whileInView={{ opacity: 1, y: 0 }}
            viewport={{ once: true }}
            transition={{ duration: 0.3, delay: index * 0.1 }}
            className="group bg-slate-900/80 border border-slate-800 p-5 rounded-xl hover:border-cyan-500/50 transition-colors flex flex-col"
          >
            <div className="flex justify-between items-start mb-2">
              <h4 className="text-lg font-bold text-white group-hover:text-cyan-400 transition-colors cursor-pointer flex items-center gap-2">
                {project.title}
                {project.live && <ExternalLink className="w-4 h-4 opacity-0 group-hover:opacity-100 transition-opacity" />}
              </h4>
              <span className="text-[10px] font-mono px-2 py-1 border border-cyan-900 rounded text-cyan-400 whitespace-nowrap">
                {project.tech}
              </span>
            </div>
            
            <p className="text-sm text-slate-400 mb-4 flex-grow">
              {project.description}
            </p>
            
            <div className="flex justify-between items-center text-[10px] font-mono italic">
              <div className="flex gap-3 text-slate-500">
                {project.github && (
                  <a href={project.github} className="hover:text-cyan-400 transition-colors flex items-center gap-1 uppercase">
                    <Github className="w-3 h-3" /> Source
                  </a>
                )}
              </div>
              <div className="flex gap-2 text-cyan-600">
                {project.tags.map(tag => <span key={tag}>{tag}</span>)}
              </div>
            </div>
          </motion.div>
        ))}
      </div>
      
      <div className="mt-4 md:hidden text-center">
        <a href="https://github.com" className="inline-flex items-center gap-1 text-cyan-500 hover:text-cyan-400 font-mono text-[10px] transition-colors uppercase">
          Ver_Archivo_Completo <ExternalLink className="w-3 h-3" />
        </a>
      </div>
    </section>
  );
}
