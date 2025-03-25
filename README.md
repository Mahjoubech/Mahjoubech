import React, { useState } from 'react';
import { 
  Code, 
  Database, 
  Globe, 
  Server, 
  Terminal, 
  Layers, 
  Cpu, 
  GitHub, 
  Linkedin, 
  Mail, 
  FileText 
} from 'lucide-react';

const DeveloperProfile = () => {
  const [activeSection, setActiveSection] = useState('about');

  const technologies = [
    { name: 'Laravel', icon: <Code color="#FF2D20" size={48} />, level: 90 },
    { name: 'React', icon: <Layers color="#61DAFB" size={48} />, level: 85 },
    { name: 'Node.js', icon: <Server color="#339933" size={48} />, level: 80 },
    { name: 'TypeScript', icon: <Terminal color="#3178C6" size={48} />, level: 75 }
  ];

  return (
    <div className="min-h-screen bg-gradient-to-br from-indigo-900 via-purple-900 to-black text-white p-8 font-sans">
      {/* Header Section */}
      <div className="flex items-center justify-between mb-12">
        <div className="flex items-center space-x-4">
          <img 
            src="/api/placeholder/150/150" 
            alt="Developer Profile" 
            className="rounded-full border-4 border-purple-500 shadow-2xl transform hover:scale-110 transition-transform"
          />
          <div>
            <h1 className="text-4xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
              Cherkaoui Mahjoub
            </h1>
            <p className="text-xl text-purple-300">
              Full Stack Developer | Tech Innovator
            </p>
          </div>
        </div>
        <div className="flex space-x-4">
          <a href="https://github.com/mahjoubech" target="_blank" className="hover:scale-125 transition-transform">
            <GitHub size={36} className="text-white" />
          </a>
          <a href="https://linkedin.com/in/mahjoub-cherkaoui" target="_blank" className="hover:scale-125 transition-transform">
            <Linkedin size={36} className="text-blue-500" />
          </a>
          <a href="mailto:charkaouielmahjoub50@gmail.com" className="hover:scale-125 transition-transform">
            <Mail size={36} className="text-red-500" />
          </a>
        </div>
      </div>

      {/* Navigation */}
      <div className="flex justify-center mb-8 space-x-4">
        {['about', 'skills', 'projects', 'contact'].map(section => (
          <button 
            key={section}
            onClick={() => setActiveSection(section)}
            className={`px-4 py-2 rounded-full transition-all ${
              activeSection === section 
                ? 'bg-purple-600 text-white' 
                : 'bg-transparent text-purple-300 hover:bg-purple-800'
            }`}
          >
            {section.charAt(0).toUpperCase() + section.slice(1)}
          </button>
        ))}
      </div>

      {/* Content Sections */}
      {activeSection === 'about' && (
        <div className="bg-black/50 p-8 rounded-2xl">
          <h2 className="text-3xl mb-4 text-purple-400">About Me</h2>
          <p className="text-lg text-gray-300">
            Passionate Full Stack Developer from Morocco, transforming complex ideas 
            into elegant digital solutions. With expertise in Laravel, React, and 
            cutting-edge web technologies, I create innovative and performant web applications.
          </p>
        </div>
      )}

      {activeSection === 'skills' && (
        <div className="grid grid-cols-2 gap-8">
          <div className="bg-black/50 p-8 rounded-2xl">
            <h2 className="text-3xl mb-6 text-purple-400">Technologies</h2>
            {technologies.map((tech, index) => (
              <div key={index} className="mb-4">
                <div className="flex items-center mb-2">
                  {tech.icon}
                  <span className="ml-4 text-xl">{tech.name}</span>
                </div>
                <div className="w-full bg-gray-700 rounded-full h-4">
                  <div 
                    className="bg-purple-600 h-4 rounded-full" 
                    style={{width: `${tech.level}%`}}
                  />
                </div>
              </div>
            ))}
          </div>
          <div className="bg-black/50 p-8 rounded-2xl">
            <h2 className="text-3xl mb-6 text-purple-400">Development Skills</h2>
            <ul className="space-y-2">
              {[
                'Full Stack Development',
                'Responsive Web Design',
                'API Integration',
                'Performance Optimization',
                'Cloud Deployment'
              ].map((skill, index) => (
                <li 
                  key={index} 
                  className="flex items-center text-lg text-gray-300 hover:text-purple-400 transition-colors"
                >
                  <Cpu size={24} className="mr-3 text-purple-500" />
                  {skill}
                </li>
              ))}
            </ul>
          </div>
        </div>
      )}

      {activeSection === 'projects' && (
        <div className="bg-black/50 p-8 rounded-2xl">
          <h2 className="text-3xl mb-6 text-purple-400">Featured Projects</h2>
          <div className="grid grid-cols-3 gap-6">
            {[
              { name: 'Portfolio Website', tech: 'React, Tailwind' },
              { name: 'E-Commerce Platform', tech: 'Laravel, Vue.js' },
              { name: 'API Dashboard', tech: 'Node.js, Express' }
            ].map((project, index) => (
              <div 
                key={index} 
                className="bg-purple-900/30 p-6 rounded-xl hover:scale-105 transition-transform"
              >
                <FileText size={48} className="text-purple-500 mb-4" />
                <h3 className="text-xl font-bold mb-2">{project.name}</h3>
                <p className="text-gray-400">{project.tech}</p>
              </div>
            ))}
          </div>
        </div>
      )}

      {activeSection === 'contact' && (
        <div className="bg-black/50 p-8 rounded-2xl text-center">
          <h2 className="text-3xl mb-6 text-purple-400">Let's Connect</h2>
          <p className="text-xl mb-6 text-gray-300">
            Open to collaboration, freelance opportunities, and exciting projects.
          </p>
          <a 
            href="mailto:charkaouielmahjoub50@gmail.com" 
            className="bg-purple-600 hover:bg-purple-700 text-white px-8 py-3 rounded-full text-xl transition-colors"
          >
            Contact Me
          </a>
        </div>
      )}

      {/* Footer */}
      <div className="mt-8 text-center text-gray-500">
        © 2024 Cherkaoui Mahjoub. All Rights Reserved.
      </div>
    </div>
  );
};

export default DeveloperProfile;
