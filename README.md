<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>React Router Dashboard</title>
  <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-router-dom@6/umd/react-router-dom.development.js" crossorigin></script>
  <style>
    body { 
      font-family: sans-serif; 
      padding: 20px; 
    }
    nav a { 
      margin-right: 10px; 
      text-decoration: none;
      color: #333;
      padding: 5px 10px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    nav a:hover {
      background-color: #f0f0f0;
    }
  </style>
</head>
<body>
  <div id="root"></div>
  <script type="text/javascript">
    const { BrowserRouter, Routes, Route, Link, Outlet } = ReactRouterDOM;

    function Dashboard() {
      return (
        <div>
          <h2>Dashboard</h2>
          <nav>
            <Link to="/dashboard/profile">Profile</Link>
            <Link to="/dashboard/settings">Settings</Link>
          </nav>
          <hr />
          <Outlet />
        </div>
      );
    }

    function Profile() {
      return <h3>This is your Profile page.</h3>;
    }

    function Settings() {
      return <h3>This is your Settings page.</h3>;
    }

    function Home() {
      return (
        <div>
          <h2>Home</h2>
          <Link to="/dashboard">Go to Dashboard</Link>
        </div>
      );
    }

    const App = () => (
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/dashboard" element={<Dashboard />}>
            <Route path="profile" element={<Profile />} />
            <Route path="settings" element={<Settings />} />
          </Route>
        </Routes>
      </BrowserRouter>
    );

    const root = ReactDOM.createRoot(document.getElementById("root"));
    root.render(<App />);
  </script>
</body>
</html>
