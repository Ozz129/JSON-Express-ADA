# JSON-Express-ADA

// importamos express
const express = require('express');

//utilizamos express
const app = express();

//utilizamos json de express como un middleware
app.use(express.json({
  limit: 10,
  reviver: '',
  strict: true
}));

app.post('/usuarios', (req, res) => {
  const nuevoUsuario = req.body;
  console.log(nuevoUsuario);
  for (const usuario of nuevoUsuario) {
    almacenarUsuario(usuario)
  }
  res.send('Usuario creado correctamente');
});

app.post('/datos', (req, res) => {
    let body = '';
    req.on('data', chunk => {
      body += chunk.toString();
    });
    req.on('end', () => {
      console.log(typeof body);
      res.send('Datos recibidos correctamente');
    });
  });
  
app.listen(3000, () => {
  console.log('La aplicación está escuchando en el puerto 3000');
});
