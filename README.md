import React, { useState } from "react";

function RegistrationForm({ onClose }) {
  const [form, setForm] = useState({
    name: "",
    email: "",
    password: "",
  });

  function handleChange(e) {
    setForm({ ...form, [e.target.name]: e.target.value });
  }

  function handleSubmit(e) {
    e.preventDefault();
    console.log("Form Submitted:", form);
    // Here you could send the data to a backend
    onClose();
  }

  return (
    <div style={{ border: "1px solid #ccc", padding: "16px", width: "300px", background: "#f9f9f9" }}>
      <h2>Register</h2>
      <form onSubmit={handleSubmit}>
        <div>
          <label>
            Name:
            <input type="text" name="name" value={form.name} onChange={handleChange} required />
          </label>
        </div>
        <div>
          <label>
            Email:
            <input type="email" name="email" value={form.email} onChange={handleChange} required />
          </label>
        </div>
        <div>
          <label>
            Password:
            <input type="password" name="password" value={form.password} onChange={handleChange} required />
          </label>
        </div>
        <button type="submit">Submit</button>
        <button type="button" onClick={onClose} style={{ marginLeft: "8px" }}>Cancel</button>
      </form>
    </div>
  );
}

export default function App() {
  const [showForm, setShowForm] = useState(false);

  return (
    <div style={{ padding: "40px", fontFamily: "sans-serif" }}>
      <h1>Welcome!</h1>
      {!showForm && (
        <button onClick={() => setShowForm(true)}>Registration</button>
      )}
      {showForm && (
        <RegistrationForm onClose={() => setShowForm(false)} />
      )}
    </div>
  );
}

