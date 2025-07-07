Q1: How will you pass the product’s name and price from the parent component?
Answer:
jsx

<ProductCard name="T-shirt" price={499} />

const ProductCard = ({ name, price }) => (
  <div>
    <h2>{name}</h2>
    <p>₹{price}</p>
  </div>
);

Q2: How will you implement the toggle between "Liked ❤️" and "Like 🤍"?
Answer:
const [liked, setLiked] = useState(false);

const toggleLike = () => setLiked(prev => !prev);

<button onClick={toggleLike}>
  {liked ? 'Liked ❤️' : 'Like 🤍'}
</button>

Q3: How will you manage the input using a controlled component?
Answer: 

const [searchTerm, setSearchTerm] = useState('');

<input
  type="text"
  value={searchTerm}
  onChange={e => setSearchTerm(e.target.value)}
  placeholder="Search..."
/>

Q4:  How will you share the current theme using useContext?
Answer:

// ThemeContext.js
export const ThemeContext = createContext();

export const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light');
  const toggleTheme = () => setTheme(prev => (prev === 'light' ? 'dark' : 'light'));

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};


Q5: How to restrict unauthenticated access to the Checkout page?
Answer:

const PrivateRoute = ({ children }) => {
  const { isAuthenticated } = useContext(AuthContext);
  return isAuthenticated ? children : <Navigate to="/login" />;
};

// Usage in routes
<Route path="/checkout" element={<PrivateRoute><CheckoutPage /></PrivateRoute>} />
