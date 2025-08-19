# My-Portfolio
new repositary
import { useState, useEffect } from "react";
import { motion } from "framer-motion";
import { ArrowUp, Mail, Phone, Github, Linkedin } from "lucide-react";

// -------------------- Header Component --------------------
function Header() {
  const [scrolled, setScrolled] = useState(false);

  useEffect(() => {
    const handleScroll = () => setScrolled(window.scrollY > 50);
    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  }, []);

  // NOTE: Using "bg-white bg-opacity-40" instead of "bg-white/40" for broader Tailwind compatibility
  const headerBg = scrolled
    ? "bg-white shadow-lg"
    : "bg-white bg-opacity-40 backdrop-blur-md shadow-md";

  return (
    <header
      className={`fixed top-0 left-0 w-full z-50 flex items-center justify-between px-6 py-3 transition-all duration-500 ${headerBg}`}
    >
      {/* Profile image + Name */}
      <div className="flex items-center space-x-3">
        <img
          src="/profile.jpg"
          alt="MammadRafeek Wallibayi"
          className="w-12 h-12 rounded-full border-2 border-gray-300 object-cover"
        />
        <span className="font-bold text-lg text-gray-800">MammadRafeek Wallibayi</span>
      </div>

      {/* Nav Links */}
      <nav className="space-x-6 font-medium">
        <a href="#about" className="hover:text-blue-600 transition-colors">About</a>
        <a href="#skills" className="hover:text-blue-600 transition-colors">Skills</a>
        <a href="#education" className="hover:text-blue-600 transition-colors">Education</a>
        <a href="#projects" className="hover:text-blue-600 transition-colors">Projects</a>
        <a href="#contact" className="hover:text-blue-600 transition-colors">Contact</a>
      </nav>
    </header>
  );
}

// -------------------- Back to Top Button --------------------
function BackToTop() {
  const [visible, setVisible] = useState(false);

  useEffect(() => {
    const toggleVisibility = () => setVisible(window.scrollY > 200);
    window.addEventListener("scroll", toggleVisibility);
    return () => window.removeEventListener("scroll", toggleVisibility);
  }, []);

  return (
    visible && (
      <button
        onClick={() => window.scrollTo({ top: 0, behavior: "smooth" })}
        className="fixed bottom-6 right-6 bg-blue-600 text-white p-3 rounded-full shadow-lg hover:bg-blue-700 transition-transform animate-bounce"
        aria-label="Back to top"
      >
        <ArrowUp className="w-5 h-5" />
      </button>
    )
  );
}

// -------------------- Section Wrapper with Animation --------------------
function Section({ id, children, bg }) {
  return (
    <motion.section
      id={id}
      className={`p-12 min-h-screen flex flex-col justify-center transition-colors duration-700 ease-in-out ${bg}`}
      initial={{ opacity: 0, y: 50 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: false }}
      transition={{ duration: 0.8 }}
    >
      {children}
    </motion.section>
  );
}

// -------------------- Main App --------------------
export default function App() {
  return (
    <div className="font-sans">
      <Header />

      {/* About Section */}
      <Section id="about" bg="bg-gradient-to-r from-pink-100 to-pink-200">
        <div className="flex flex-col md:flex-row items-center gap-8">
          <img
            src="/profile.jpg"
            alt="MammadRafeek Wallibayi"
            className="w-48 h-48 rounded-full shadow-lg border-4 border-white object-cover"
          />
          <div>
            <h2 className="text-3xl font-bold mb-4">About Me</h2>
            <p className="text-lg max-w-2xl">
              An energetic and enthusiastic fresher seeking to work in a progressive environment where I have the opportunity to showcase my skills, interact with diverse individuals and groups at all organization’s level, and contribute to the success of the organization.
            </p>
          </div>
        </div>
      </Section>

      {/* Skills Section */}
      <Section id="skills" bg="bg-gradient-to-r from-blue-100 to-blue-200">
        <h2 className="text-3xl font-bold mb-6">Skills</h2>
        <ul className="list-disc pl-6 space-y-2 text-lg">
          <li>HTML</li>
          <li>CSS</li>
          <li>JavaScript</li>
          <li>Python</li>
          <li>Java</li>
          <li>MySQL</li>
        </ul>
      </Section>

      {/* Education Section */}
      <Section id="education" bg="bg-gradient-to-r from-green-100 to-green-200">
        <h2 className="text-3xl font-bold mb-6">Education</h2>
        <div className="space-y-4 text-lg">
          <div>
            <p className="font-semibold">MCA</p>
            <p>Visvesvaraya Technological University Belagavi, CPGS Kalaburagi</p>
            <p>2023 - 2025</p>
          </div>
          <div>
            <p className="font-semibold">BCA</p>
            <p>Sharnbasva University</p>
            <p>2020 - 2023</p>
          </div>
        </div>
      </Section>

      {/* Projects Section */}
      <Section id="projects" bg="bg-gradient-to-r from-purple-100 to-purple-200">
        <h2 className="text-3xl font-bold mb-6">Projects</h2>
        <ul className="list-disc pl-6 space-y-2 text-lg">
          <li>Text Summarization and Document Understanding</li>
          <li>Speech Emotion Detection System</li>
          <li>Smart Wiper Detection System</li>
          <li>Mini Greenhouse Implementation</li>
        </ul>
      </Section>

      {/* Contact Section */}
      <Section id="contact" bg="bg-gradient-to-r from-yellow-100 to-yellow-200">
        <h2 className="text-3xl font-bold mb-6">Contact</h2>
        <div className="space-y-4 text-lg">
          <p className="flex items-center gap-2">
            <Mail className="w-5 h-5" />
            <a href="mailto:mdrafeek0276@gmail.com" className="text-blue-600 underline">
              mdrafeek0276@gmail.com
            </a>
          </p>
          <p className="flex items-center gap-2">
            <Phone className="w-5 h-5" />
            <a href="tel:+919108440276" className="text-blue-600 underline">
              +91 9108440276
            </a>
          </p>
          <p className="flex items-center gap-2">
            <Github className="w-5 h-5" />
            <a
              href="https://github.com/mammadrafeek786"
              target="_blank"
              rel="noopener noreferrer"
              className="text-blue-600 underline"
            >
              github.com/mammadrafeek786
            </a>
          </p>
          <p className="flex items-center gap-2">
            <Linkedin className="w-5 h-5" />
            <a
              href="https://linkedin.com/in/md-rafik-wallibayi"
              target="_blank"
              rel="noopener noreferrer"
              className="text-blue-600 underline"
            >
              linkedin.com/in/md-rafik-wallibayi
            </a>
          </p>
          <p>
            📄 Resume:{" "}
            <a href="/resume.pdf" download className="text-blue-600 underline">
              Download Resume
            </a>
          </p>
        </div>
      </Section>

      <BackToTop />
    </div>
  );
}
