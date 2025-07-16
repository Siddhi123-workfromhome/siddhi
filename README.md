import React, { useState } from "react";

const jobsData = [
  {
    id: 1,
    title: "Frontend Developer",
    company: "TechSoft",
    location: "Remote",
    description: "React/JS developer needed for remote team.",
  },
  {
    id: 2,
    title: "Content Writer",
    company: "WriteIt",
    location: "Remote",
    description: "Remote writing jobs for blogs and websites.",
  },
  // Add more jobs...
];

function App() {
  const [search, setSearch] = useState("");
  const filteredJobs = jobsData.filter(job =>
    job.title.toLowerCase().includes(search.toLowerCase()) ||
    job.company.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div style={{ padding: 20 }}>
      <h1>Work From Home Jobs</h1>
      <input
        type="text"
        placeholder="Search jobs"
        value={search}
        onChange={e => setSearch(e.target.value)}
        style={{ padding: 8, marginBottom: 20 }}
      />
      <ul>
        {filteredJobs.map(job => (
          <li key={job.id} style={{ marginBottom: 20, border: "1px solid #ccc", padding: 10 }}>
            <h2>{job.title}</h2>
            <p><strong>Company:</strong> {job.company}</p>
            <p><strong>Location:</strong> {job.location}</p>
            <p>{job.description}</p>
            <button>Apply Now</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
