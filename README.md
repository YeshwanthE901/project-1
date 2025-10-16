
//App.js

import React from "react";
import ThemeToggle from "./ThemeToggle";

function App() {
  return <ThemeToggle />;
}

export default App;


//ThemeToggle.js

import React, { useState, useEffect } from "react";

export default function ThemeToggle() {
  // Get stored theme from localStorage (if exists)
  const getStoredTheme = () => {
    return localStorage.getItem("theme") || "light";
  };

  // State for current theme
  const [theme, setTheme] = useState(getStoredTheme);

  // Whenever theme changes, update localStorage and body class
  useEffect(() => {
    document.body.className = theme; // Apply theme class to body
    localStorage.setItem("theme", theme); // Save preference
  }, [theme]);

  //Toggle between light and dark
  const toggleTheme = () => {
    setTheme((prevTheme) => (prevTheme === "light" ? "dark" : "light"));
  };

  return (
    <div
      style={{
        height: "100vh",
        display: "flex",
        flexDirection: "column",
        alignItems: "center",
        justifyContent: "center",
        backgroundColor: theme === "light" ? "#fff" : "#222",
        color: theme === "light" ? "#000" : "#fff",
        transition: "all 0.3s ease",
      }}
    >
      <h1>{theme === "light" ? " Light Mode" : " Dark Mode"}</h1>
      <button
        onClick={toggleTheme}
        style={{
          marginTop: "20px",
          padding: "10px 20px",
          borderRadius: "8px",
          border: "none",
          background: theme === "light" ? "#000" : "#fff",
          color: theme === "light" ? "#fff" : "#000",
          cursor: "pointer",
        }}
      >
        Toggle Theme
      </button>
    </div>


    //index.js
    
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);

//index.css

body {
  margin: 0;
  font-family: Arial, sans-serif;
}

  );
}
