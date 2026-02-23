# 🚀 Full Stack & Blockchain Developer  
# 🧠 Problem Solver  
# 🎨 Product-Minded Builder

---

**Animated Typing Effect Live Demo:**  
Check out my animated intro: [mywebsite.com/animated-profile](https://mywebsite.com/animated-profile)

---

## Animation Source Code

```tsx
// AnimatedTyping.tsx
import React, { useEffect, useState } from "react";

const phrases = [
  "🚀 Full Stack & Blockchain Developer",
  "🧠 Problem Solver",
  "🎨 Product-Minded Builder"
];

const letterDelay = 70;
const phraseDelay = 900;

export default function AnimatedTyping() {
  const [phraseIndex, setPhraseIndex] = useState(0);
  const [displayedLetters, setDisplayedLetters] = useState("");
  const [letterIndex, setLetterIndex] = useState(0);

  useEffect(() => {
    if (letterIndex < phrases[phraseIndex].length) {
      const timeout = setTimeout(() => {
        setDisplayedLetters(prev => prev + phrases[phraseIndex][letterIndex]);
        setLetterIndex(letterIndex + 1);
      }, letterDelay);
      return () => clearTimeout(timeout);
    } else {
      const timeout = setTimeout(() => {
        setPhraseIndex((phraseIndex + 1) % phrases.length);
        setDisplayedLetters("");
        setLetterIndex(0);
      }, phraseDelay);
      return () => clearTimeout(timeout);
    }
  }, [letterIndex, phraseIndex]);

  return (
    <div style={{ fontFamily: "monospace", fontSize: "1.5rem" }}>
      {displayedLetters}
      <span className="blinking-cursor">|</span>
      <style>{`  
        .blinking-cursor {
          animation: blink .8s linear infinite;
        }
        @keyframes blink {
          0%, 100% { opacity: 1; }
          50% { opacity: 0; }
        }
      `}</style>
    </div>
  );
}