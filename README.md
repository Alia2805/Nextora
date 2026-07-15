import React, { useState } from 'react';

export default function App() {
  // --- STATE MANAGEMENT ---
  const [isAuthenticated, setIsAuthenticated] = useState(false);
  const [authMode, setAuthMode] = useState('signup'); // signup or login
  const [authForm, setAuthForm] = useState({ name: '', email: '', password: '', grade: '10th' });
  const [activeTab, setActiveTab] = useState('finder'); // finder, higher, courses, scholarships, chatbot
  
  // Search Filters
  const [percentage, setPercentage] = useState(75);
  const [selectedStream, setSelectedStream] = useState('Science');
  const [chatInput, setChatInput] = useState('');
  const [chatMessages, setChatMessages] = useState([
    { sender: 'bot', text: 'Hello! I am Nextora AI. Ask, discover, and achieve your dreams. How can I help you map your career path today?' }
  ]);

  // --- DUMMY DATA BASE ---
  const collegesData = [
    { name: 'Apex Polytechnic Institute', stream: 'Polytechnic', minPercent: 45, fees: '₹45,000/yr', docs: '10th Marksheet, LC', placement: '80% Placement' },
    { name: 'St. Xavier Higher Secondary', stream: 'Science', minPercent: 85, fees: '₹30,000/yr', docs: '10th Marksheet, Transfer Cert', placement: 'Excellent Record' },
    { name: 'St. Xavier Higher Secondary', stream: 'Commerce', minPercent: 75, fees: '₹25,000/yr', docs: '10th Marksheet, Transfer Cert', placement: 'Top Tier Tieups' },
    { name: 'Sir J.J. School of Arts', stream: 'Arts', minPercent: 60, fees: '₹20,000/yr', docs: '10th Marksheet, Portfolio', placement: 'Creative Agency Tieups' },
    { name: 'Global Tech Diploma College', stream: 'Diploma', minPercent: 35, fees: '₹55,000/yr', docs: '10th Marksheet, Income Cert', placement: 'Direct 2nd Yr Engg Entry' },
    { name: 'National Science Academy', stream: 'Science', minPercent: 92, fees: '₹40,000/yr', docs: '10th Marksheet, Migration Cert', placement: 'IIT-JEE coaching attached' },
  ];

  const internationalColleges = [
    { name: 'Technical University of Munich (Germany)', degree: 'Masters / PhD', stream: 'Engineering', fees: '€0 (Tuition Free)', reqs: 'IELTS 6.5, GRE, Blocked Account', placement: 'Top European Tech Firms' },
    { name: 'Stanford University (USA)', degree: 'Masters / PhD', stream: 'Science & Management', fees: '$55,000/yr', reqs: 'TOEFL 100, GRE/GMAT, 3 LORs, SOP', placement: 'Silicon Valley Hub' },
    { name: 'Heidelberg University (Germany)', degree: 'Masters / PhD', stream: 'Medical & Life Sci', fees: '€0 (Tuition Free)', reqs: 'IELTS 7.0, German A2 preferred', placement: 'Global Research Labs' }
  ];

  const coursesData = [
    { title: 'Full-Stack Web Development', provider: 'Meta via Coursera', type: 'Paid (Financial Aid Avail)', marketDemand: 'Critical / High', link: '#' },
    { title: 'Introduction to Python Data Science', provider: 'Kaggle / Google', type: 'Free', marketDemand: 'Very High', link: '#' },
    { title: 'UX/UI Product Design Systems', provider: 'Figma Academy', type: 'Free', marketDemand: 'Trending', link: '#' }
  ];

  const scholarshipsData = [
    { name: 'National Merit Scholarship Program', type: 'Government', criteria: 'Score > 85% in 10th/12th', reward: 'Full Tuition Fee Waiver' },
    { name: 'Reliance Foundation Scholarships', type: 'Private', criteria: 'Merit-cum-Means (Family Income < 2.5L)', reward: 'Up to ₹2,00,000 for degree studies' }
  ];

  // --- HANDLERS ---
  const handleAuthSubmit = (e) => {
    e.preventDefault();
    if (authForm.email && authForm.password) {
      setIsAuthenticated(true);
    } else {
      alert('Please fill out all fields.');
    }
  };

  const handleSendMessage = (e) => {
    e.preventDefault();
    if (!chatInput.trim()) return;

    const userMsg = { sender: 'user', text: chatInput };
    let botReplyText = "That's an excellent question! Based on trends, I suggest pursuing a career path aligned with your skills. Try evaluating your core technical skills or standard certifications on our platform.";

    if (chatInput.toLowerCase().includes('10th') || chatInput.toLowerCase().includes('percent')) {
      botReplyText = "For 10th grade options, check out our College Finder section. You can use your exact percentage to match with Science, Commerce, Arts, or Diploma lines instantly!";
    } else if (chatInput.toLowerCase().includes('germany') || chatInput.toLowerCase().includes('usa')) {
      botReplyText = "Studying abroad requires preparation. Germany offers zero tuition fees for public universities, while the US provides unparalleled industry placements. You will need strong IELTS/TOEFL scores.";
    }

    const botMsg = { sender: 'bot', text: botReplyText };
    setChatMessages([...chatMessages, userMsg, botMsg]);
    setChatInput('');
  };

  // --- AUTH RENDERING ---
  if (!isAuthenticated) {
    return (
      <div style={styles.authContainer}>
        <div style={styles.authCard}>
          <h1 style={styles.brandTitle}>NEXTORA</h1>
          <p style={styles.brandSubtitle}>Your Pathway to Academic & Career Success</p>
          
          <div style={styles.authToggle}>
            <button 
              style={{ ...styles.toggleBtn, borderBottom: authMode === 'signup' ? '3px solid #4F46E5' : 'none' }}
              onClick={() => setAuthMode('signup')}
            >
              Sign Up
            </button>
            <button 
              style={{ ...styles.toggleBtn, borderBottom: authMode === 'login' ? '3px solid #4F46E5' : 'none' }}
              onClick={() => setAuthMode('login')}
            >
              Login
            </button>
          </div>

          <form onSubmit={handleAuthSubmit} style={styles.form}>
            {authMode === 'signup' && (
              <input 
                type="text" 
                placeholder="Full Name" 
                style={styles.input} 
                value={authForm.name}
                onChange={e => setAuthForm({...authForm, name: e.target.value})}
              />
            )}
            <input 
              type="email" 
              placeholder="Email Address" 
              style={styles.input} 
              value={authForm.email} 
              onChange={e => setAuthForm({...authForm, email: e.target.value})}
              required
            />
            <input 
              type="password" 
              placeholder="Password" 
              style={styles.input} 
              value={authForm.password}
              onChange={e => setAuthForm({...authForm, password: e.target.value})}
              required
            />
            {authMode === 'signup' && (
              <select 
                style={styles.input} 
                value={authForm.grade}
                onChange={e => setAuthForm({...authForm, grade: e.target.value})}
              >
                <option value="10th">Currently in 10th</option>
                <option value="12th">Currently in 12th</option>
                <option value="Graduate">Undergraduate Graduate</option>
              </select>
            )}
            <button type="submit" style={styles.submitBtn}>
              {authMode === 'signup' ? 'Create Account' : 'Sign In'}
            </button>
          </form>
        </div>
      </div>
    );
  }

  // --- MAIN APP APPLICATION RENDER ---
  return (
    <div style={styles.appStructure}>
      {/* Navigation Header */}
      <nav style={styles.navbar}>
        <div style={styles.logoGroup}>
          <span style={styles.navBrand}>Nextora</span>
        </div>
        <div style={styles.navLinks}>
          <button style={activeTab === 'finder' ? styles.activeNavLink : styles.navLink} onClick={() => setActiveTab('finder')}>College Finder (10th/12th)</button>
          <button style={activeTab === 'higher' ? styles.activeNavLink : styles.navLink} onClick={() => setActiveTab('higher')}>Global Higher Ed</button>
          <button style={activeTab === 'courses' ? styles.activeNavLink : styles.navLink} onClick={() => setActiveTab('courses')}>Market Courses</button>
          <button style={activeTab === 'scholarships' ? styles.activeNavLink : styles.navLink} onClick={() => setActiveTab('scholarships')}>Scholarships</button>
          <button style={activeTab === 'chatbot' ? styles.chatNavHighlight : styles.chatNavBtn} onClick={() => setActiveTab('chatbot')}>💬 Talk with Nextora</button>
          <button style={styles.logoutBtn} onClick={() => setIsAuthenticated(false)}>Logout</button>
        </div>
      </nav>

      {/* Primary Page Canvas */}
      <main style={styles.contentCanvas}>

        {/* SECTION 1: 10th Percentage & Criteria Based College Suggestion */}
        {activeTab === 'finder' && (
          <div>
            <h2 style={styles.sectionHeader}>Percent-based College Criteria Suggester</h2>
            <p style={styles.sectionDesc}>Slide your 10th Grade score down to view eligible colleges, admission paths, fees, and required document structures.</p>
            
            <div style={styles.filterBar}>
              <div style={{ flex: 1, marginRight: '20px' }}>
                <label style={styles.label}>Your 10th Percentage Cut-off: <strong>{percentage}%</strong></label>
                <input 
                  type="range" min="35" max="100" 
                  value={percentage} 
                  onChange={(e) => setPercentage(Number(e.target.value))}
                  style={styles.slider}
                />
              </div>

              <div>
                <label style={styles.label}>Select Stream Track:</label>
                <select style={styles.dropdown} value={selectedStream} onChange={(e) => setSelectedStream(e.target.value)}>
                  <option value="Science">Science</option>
                  <option value="Commerce">Commerce</option>
                  <option value="Arts">Arts</option>
                  <option value="Diploma">Technical Diploma</option>
                  <option value="Polytechnic">Polytechnic</option>
                </select>
              </div>
            </div>

            <div style={styles.grid}>
              {collegesData
                .filter(c => c.stream === selectedStream && percentage >= c.minPercent)
                .map((college, idx) => (
                  <div key={idx} style={styles.card}>
                    <h3 style={styles.cardTitle}>{college.name}</h3>
                    <span style={styles.badge}>{college.stream}</span>
                    <p><strong>Min Required Cut-off:</strong> {college.minPercent}%</p>
                    <p><strong>Estimated Annual Fees:</strong> {college.fees}</p>
                    <p><strong>Required Entry Documents:</strong> {college.docs}</p>
                    <p style={{ color: '#059669', fontWeight: 'bold' }}>⚡ Placement Status: {college.placement}</p>
                  </div>
              ))}
              {collegesData.filter(c => c.stream === selectedStream && percentage >= c.minPercent).length === 0 && (
                <p style={{ color: '#6B7280' }}>No local colleges found for your exact criteria level. Try adjusting your input criteria score sliders.</p>
              )}
            </div>
          </div>
        )}

        {/* SECTION 2: Advanced Higher Studies & Overseas Universities */}
        {activeTab === 'higher' && (
          <div>
            <h2 style={styles.sectionHeader}>Advanced Postgraduate, Degree & Global Doctoral Explorer</h2>
            <p style={styles.sectionDesc}>Explore elite Bachelor's, Master's, and PhD opportunities inside India as well as premier overseas destinations like Germany and the USA.</p>

            <div style={styles.grid}>
              {internationalColleges.map((col, idx) => (
                <div key={idx} style={{ ...styles.card, borderLeft: '5px solid #0284C7' }}>
                  <h3 style={styles.cardTitle}>{col.name}</h3>
                  <div style={{ display: 'flex', gap: '5px', marginBottom: '10px' }}>
                    <span style={{ ...styles.badge, backgroundColor: '#E0F2FE', color: '#0369A1' }}>{col.degree}</span>
                    <span style={styles.badge}>{col.stream}</span>
                  </div>
                  <p><strong>Fee Structure:</strong> {col.fees}</p>
                  <p><strong>Mandatory Entry Requirements:</strong> {col.reqs}</p>
                  <p style={{ color: '#059669', fontWeight: 'bold' }}>🎯 Global Placement Metrics: {col.placement}</p>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* SECTION 3: High-Demand Online Certification Modules */}
        {activeTab === 'courses' && (
          <div>
            <h2 style={styles.sectionHeader}>Industry-Ready Micro-Credentials & Online Courses</h2>
            <p style={styles.sectionDesc}>Bridge the industry employability gap with free and paid technical skill pipelines directly aligned to global hiring mandates.</p>

            <div style={styles.grid}>
              {coursesData.map((course, idx) => (
                <div key={idx} style={styles.card}>
                  <h3 style={styles.cardTitle}>{course.title}</h3>
                  <p style={{ color: '#4F46E5', fontWeight: '500' }}>Platform Provider: {course.provider}</p>
                  <p><strong>Financial Model:</strong> {course.type}</p>
                  <p><strong>Market Adaptability Rating:</strong> <span style={{ color: '#DC2626', fontWeight: 'bold' }}>{course.marketDemand}</span></p>
                  <button style={styles.actionBtn}>Enroll / Explore Program</button>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* SECTION 4: Comprehensive Financial Aid & Scholarships Portal */}
        {activeTab === 'scholarships' && (
          <div>
            <h2 style={styles.sectionHeader}>Centralized Student Financial Aid & Scholarship Desk</h2>
            <p style={styles.sectionDesc}>Access state funding, private organizational awards, and merit setups to securely back your global or local studies.</p>

            <div style={styles.grid}>
              {scholarshipsData.map((sch, idx) => (
                <div key={idx} style={{ ...styles.card, borderLeft: '5px solid #059669' }}>
                  <h3 style={styles.cardTitle}>{sch.name}</h3>
                  <span style={{ ...styles.badge, backgroundColor: '#D1FAE5', color: '#065F46' }}>{sch.type} Scheme</span>
                  <p style={{ marginTop: '10px' }}><strong>Eligibility Framework:</strong> {sch.criteria}</p>
                  <p><strong>Financial Reward Valuation:</strong> <span style={{ color: '#059669', fontWeight: 'bold' }}>{sch.reward}</span></p>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* SECTION 5: AI Career Bot Workspace ("Talk with Nextora") */}
        {activeTab === 'chatbot' && (
          <div style={styles.chatWorkspace}>
            <div style={styles.chatHeader}>
              <h2 style={{ margin: 0 }}>Talk with Nextora</h2>
              <div style={styles.chatSubTag}>
                <span>ASK</span> • <span>DISCOVER</span> • <span>ACHIEVE</span>
              </div>
            </div>

            <div style={styles.chatHistoryWindow}>
              {chatMessages.map((msg, index) => (
                <div 
                  key={index} 
                  style={{ 
                    ...styles.chatBubbleLayout, 
                    justifyContent: msg.sender === 'user' ? 'flex-end' : 'flex-start' 
                  }}
                >
                  <div style={{ 
                    ...styles.chatBubble, 
                    backgroundColor: msg.sender === 'user' ? '#4F46E5' : '#F3F4F6',
                    color: msg.sender === 'user' ? '#FFFFFF' : '#1F2937'
                  }}>
                    {msg.text}
                  </div>
                </div>
              ))}
            </div>

            <form onSubmit={handleSendMessage} style={styles.chatInputRow}>
              <input 
                type="text" 
                placeholder="Ask about streams, packages, visa requirements, or options based on marks..."
                style={styles.chatTextInput}
                value={chatInput}
                onChange={(e) => setChatInput(e.target.value)}
              />
              <button type="submit" style={styles.chatSendBtn}>Consult AI</button>
            </form>
          </div>
        )}

      </main>
    </div>
  );
}

// --- CSS-IN-JS ARCHITECTURE STYLES ---
const styles = {
  authContainer: { display: 'flex', justifyContent: 'center', alignItems: 'center', height: '100vh', backgroundColor: '#F3F4F6', fontFamily: 'system-ui, sans-serif' },
  authCard: { backgroundColor: '#FFFFFF', padding: '40px', borderRadius: '12px', boxShadow: '0 4px 6px rgba(0,0,0,0.1)', width: '100%', maxWidth: '420px', textAlign: 'center' },
  brandTitle: { fontSize: '32px', color: '#4F46E5', margin: '0 0 5px 0', letterSpacing: '2px', fontWeight: '800' },
  brandSubtitle: { color: '#6B7280', fontSize: '14px', marginBottom: '25px' },
  authToggle: { display: 'flex', justifyContent: 'space-around', marginBottom: '20px' },
  toggleBtn: { border: 'none', background: 'none', padding: '10px 20px', fontSize: '16px', fontWeight: '600', cursor: 'pointer', color: '#4B5563' },
  form: { display: 'flex', flexDirection: 'column', gap: '15px' },
  input: { padding: '12px', borderRadius: '6px', border: '1px solid #D1D5DB', fontSize: '15px', outline: 'none' },
  submitBtn: { padding: '12px', borderRadius: '6px', border: 'none', backgroundColor: '#4F46E5', color: '#FFFFFF', fontSize: '16px', fontWeight: '600', cursor: 'pointer', marginTop: '10px' },
  
  appStructure: { minHeight: '100vh', backgroundColor: '#F9FAFB', fontFamily: 'system-ui, sans-serif', color: '#1F2937' },
  navbar: { display: 'flex', justifyContent: 'space-between', alignItems: 'center', padding: '15px 40px', backgroundColor: '#FFFFFF', borderBottom: '1px solid #E5E7EB', position: 'sticky', top: 0, zIndex: 10 },
  navBrand: { fontSize: '24px', fontWeight: '800', color: '#4F46E5' },
  navLinks: { display: 'flex', gap: '15px', alignItems: 'center' },
  navLink: { background: 'none', border: 'none', padding: '8px 12px', borderRadius: '6px', cursor: 'pointer', fontWeight: '500', color: '#4B5563', fontSize: '14px' },
  activeNavLink: { background: '#EEF2FF', border: 'none', padding: '8px 12px', borderRadius: '6px', cursor: 'pointer', fontWeight: '600', color: '#4F46E5', fontSize: '14px' },
  chatNavBtn: { background: '#F3F4F6', border: 'none', padding: '8px 15px', borderRadius: '20px', cursor: 'pointer', fontWeight: '600', color: '#374151', fontSize: '14px' },
  chatNavHighlight: { background: '#4F46E5', border: 'none', padding: '8px 15px', borderRadius: '20px', cursor: 'pointer', fontWeight: '600', color: '#FFFFFF', fontSize: '14px' },
  logoutBtn: { background: 'none', border: '1px solid #DC2626', padding: '6px 12px', borderRadius: '6px', color: '#DC2626', cursor: 'pointer', fontSize: '13px' },
  
  contentCanvas: { padding: '40px', maxWidth: '1200px', margin: '0 auto' },
  sectionHeader: { fontSize: '28px', fontWeight: '700', marginBottom: '8px', color: '#111827' },
  sectionDesc: { color: '#6B7280', marginBottom: '30px', fontSize: '16px' },
  filterBar: { display: 'flex', backgroundColor: '#FFFFFF', padding: '20px', borderRadius: '8px', boxShadow: '0 1px 3px rgba(0,0,0,0.05)', marginBottom: '30px', alignItems: 'center' },
  label: { display: 'block', marginBottom: '8px', fontWeight: '500', fontSize: '14px', color: '#374151' },
  slider: { width: '100%', accentColor: '#4F46E5' },
  dropdown: { padding: '10px 20px', borderRadius: '6px', border: '1px solid #D1D5DB', backgroundColor: '#FFFFFF', minWidth: '180px' },
  
  grid: { display: 'grid', gridTemplateColumns: 'repeat(auto-fill, minmax(320px, 1fr))', gap: '25px' },
  card: { backgroundColor: '#FFFFFF', padding: '24px', borderRadius: '8px', boxShadow: '0 1px 3px rgba(0,0,0,0.05)', border: '1px solid #E5E7EB', display: 'flex', flexDirection: 'column', gap: '10px' },
  cardTitle: { fontSize: '18px', fontWeight: '700', margin: 0, color: '#111827' },
  badge: { display: 'inline-block', alignSelf: 'flex-start', padding: '4px 8px', borderRadius: '4px', backgroundColor: '#EEF2FF', color: '#4F46E5', fontSize: '12px', fontWeight: '600' },
  actionBtn: { marginTop: 'auto', padding: '10px', backgroundColor: '#4F46E5', color: '#FFFFFF', border: 'none', borderRadius: '6px', fontWeight: '600', cursor: 'pointer', textAlign: 'center' },
  
  chatWorkspace: { backgroundColor: '#FFFFFF', borderRadius: '12px', boxShadow: '0 4px 6px rgba(0,0,0,0.05)', border: '1px solid #E5E7EB', display: 'flex', flexDirection: 'column', height: '70vh' },
  chatHeader: { padding: '20px', borderBottom: '1px solid #E5E7EB', backgroundColor: '#FAF5FF', borderTopLeftRadius: '12px', borderTopRightRadius: '12px' },
  chatSubTag: { display: 'flex', gap: '10px', color: '#7C3AED', fontSize: '12px', fontWeight: '700', marginTop: '5px', letterSpacing: '1px' },
  chatHistoryWindow: { flex: 1, padding: '20px', overflowY: 'auto', display: 'flex', flexDirection: 'column', gap: '15px' },
  chatBubbleLayout: { display: 'flex', width: '100%' },
  chatBubble: { maxWidth: '70%', padding: '12px 16px', borderRadius: '12px', fontSize: '15px', lineHeight: '1.5' },
  chatInputRow: { display: 'flex', padding: '20px', borderTop: '1px solid #E5E7EB', gap: '10px' },
  chatTextInput: { flex: 1, padding: '14px', borderRadius: '8px', border: '1px solid #D1D5DB', outline: 'none', fontSize: '15px' },
  chatSendBtn: { padding: '0 24px', backgroundColor: '#7C3AED', color: '#FFFFFF', border: 'none', borderRadius: '8px', fontWeight: '600', cursor: 'pointer' }
};
