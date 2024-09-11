<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Estética Janeth Zazueta</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }
        header {
            background: #333;
            color: #fff;
            padding: 10px;
            text-align: center;
        }
        nav {
            display: flex;
            justify-content: center;
            background: #444;
        }
        nav a {
            color: #fff;
            padding: 14px 20px;
            text-decoration: none;
            display: block;
            cursor: pointer;
        }
        nav a:hover {
            background: #555;
        }
        .container {
            padding: 20px;
        }
        .section {
            display: none; /* Oculta las secciones por defecto */
        }
        .section.active {
            display: block; /* Muestra la sección activa */
        }
        .form-group {
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
        }
        .form-group input, .form-group textarea {
            width: 100%;
            padding: 8px;
            box-sizing: border-box;
        }
        .form-group button {
            padding: 10px 15px;
            background: #28a745;
            color: #fff;
            border: none;
            cursor: pointer;
        }
        .form-group button:hover {
            background: #218838;
        }
        .list-group {
            list-style-type: none;
            padding: 0;
        }
        .list-group li {
            padding: 10px;
            border: 1px solid #ddd;
            margin-bottom: 5px;
            cursor: pointer;
            position: relative;
        }
        .list-group li:hover {
            background: #f0f0f0;
        }
        .client-info {
            border: 1px solid #ddd;
            padding: 20px;
            margin-bottom: 20px;
        }
        .edit-delete-buttons {
            margin-top: 10px;
            position: absolute;
            right: 10px;
            top: 10px;
        }
        .InputBuscador {
            width: 200px;
            padding: 10px;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Estética Janeth Zazueta</h1>
    </header>
    <nav>
        <a href="#" onclick="showSection('inicio')">Inicio</a>
        <a href="#" onclick="showSection('registro')">Registro</a>
        <a href="#" onclick="showSection('listado-clientes')">Listado de Clientes</a>
        <a href="#" onclick="showSection('citas-hoy')">Citas de Hoy</a>
        <a href="#" onclick="showSection('agendadas')">Agendadas</a>
        <a href="#" onclick="showSection('punto-de-venta')">Punto de Venta</a>
    </nav>
    <div class="container">
        <!-- Página de Inicio -->
        <div id="inicio" class="section active">
            <h2>Inicio</h2>
            <p>Precio del dólar al día de hoy: <span id="precio-dolar">0.00</span></p>
            <h3>Check In de Empleados</h3>
            <ul id="check-in-empleados" class="list-group">
                <!-- Los datos de check-in se llenarán dinámicamente -->
            </ul>
        </div>

        <!-- Página de Registro -->
        <div id="registro" class="section">
            <h2>Registro de Cliente</h2>
            <form id="registro-form">
                <div class="form-group">
                    <label for="nombre">Nombre:</label>
                    <input type="text" id="nombre" name="nombre" required>
                </div>
                <div class="form-group">
                    <label for="telefono">Número de Celular:</label>
                    <input type="text" id="telefono" name="telefono" required>
                </div>
                <div class="form-group">
                    <button type="submit">Registrar</button>
                </div>
            </form>
        </div>

        <!-- Página de Listado de Clientes -->
        <div id="listado-clientes" class="section">
            <h2>Listado de Clientes</h2>
            <!-- Buscador -->
            <input id="buscador" type="text" placeholder="🔎 Buscar por nombre o teléfono" class="InputBuscador" oninput="buscarCliente()">
            <ul id="listado-clientes-list" class="list-group">
                <!-- Los clientes se llenarán dinámicamente -->
            </ul>
        </div>

        <!-- Página de Perfil del Cliente -->
        <div id="perfil-cliente" class="section">
            <h2>Perfil del Cliente</h2>
            <div class="client-info" id="info-cliente">
                <!-- Información del cliente se mostrará aquí -->
            </div>
            <!-- Botón para crear una nueva cita -->
            <button onclick="mostrarFormularioCita()">Crear una cita nueva</button>
            <!-- Formulario para crear una nueva cita -->
            <div id="crear-cita-form-container" style="display: none;">
                <h3>Crear Nueva Cita</h3>
                <form id="crear-cita-form">
                    <div class="form-group">
                        <label for="fecha-cita">Fecha:</label>
                        <input type="date" id="fecha-cita" required>
                    </div>
                    <div class="form-group">
                        <label for="hora-cita">Hora:</label>
                        <input type="time" id="hora-cita" required>
                    </div>
                    <div class="form-group">
                        <label for="detalles-cita">Detalles:</label>
                        <textarea id="detalles-cita" rows="4" required></textarea>
                    </div>
                    <div class="form-group">
                        <button type="submit">Crear Cita</button>
                    </div>
                </form>
            </div>
            <!-- Formulario de edición del cliente -->
            <div id="editar-cliente-form">
                <h3>Editar Información del Cliente</h3>
                <form id="form-editar-cliente">
                    <div class="form-group">
                        <label for="editar-nombre">Nombre:</label>
                        <input type="text" id="editar-nombre" required>
                    </div>
                    <div class="form-group">
                        <label for="editar-telefono">Número de Celular:</label>
                        <input type="text" id="editar-telefono" required>
                    </div>
                    <div class="form-group">
                        <label for="telefono-adicional">Teléfono Adicional:</label>
                        <input type="text" id="telefono-adicional">
                    </div>
                    <div class="form-group">
                        <button type="submit">Guardar Cambios</button>
                    </div>
                </form>
            </div>
            <!-- Listado de citas anteriores -->
            <div id="citas-anteriores">
                <h3>Citas Anteriores</h3>
                <ul class="list-group" id="citas-anteriores-list">
                    <!-- Las citas anteriores se llenarán dinámicamente -->
                </ul>
            </div>
        </div>

        <!-- Página de Citas de Hoy -->
        <div id="citas-hoy" class="section">
            <h2>Citas de Hoy</h2>
            <ul id="citas-hoy-list" class="list-group">
                <!-- Las citas de hoy se llenarán dinámicamente -->
            </ul>
        </div>

        <!-- Página de Citas Agendadas -->
        <div id="agendadas" class="section">
            <h2>Citas Agendadas</h2>
            <ul id="citas-agendadas-list" class="list-group">
                <!-- Las citas se llenarán dinámicamente -->
            </ul>
        </div>

        <!-- Página de Punto de Venta -->
       <div id="punto-de-venta" class="section">
            <h2>Punto de Venta</h2>
            <div class="pos-container">
                <!-- Formulario para añadir producto o servicio -->
                <h3>Añadir Producto o Servicio</h3>
                <form id="add-product-form">
                    <div class="form-group">
                        <label for="producto-nombre">Nombre del Producto/Servicio:</label>
                        <input type="text" id="producto-nombre" required>
                    </div>
                    <div class="form-group">
                        <label for="producto-precio">Precio:</label>
                        <input type="number" id="producto-precio" min="0" step="0.01" required>
                    </div>
                    <div class="form-group">
                        <button type="submit">Añadir</button>
                    </div>
                </form>
                
                <!-- Listado de productos o servicios añadidos -->
                <h3>Productos/Servicios Añadidos</h3>
                <ul id="productos-list" class="list-group">
                    <!-- Productos añadidos se mostrarán aquí -->
                </ul>

                <!-- Total y pago del cliente -->
                <div class="total-display">
                    <p>Total: $<span id="total">0.00</span></p>
                    <div class="form-group">
                        <label for="pago-cliente">Pago del Cliente:</label>
                        <input type="number" id="pago-cliente" min="0" step="0.01">
                    </div>
                    <button onclick="calcularCambio()">Calcular Cambio</button>
                    <p>Cambio: $<span id="cambio">0.00</span></p>
                </div>
            <!-- Información y funcionalidades del punto de venta -->
        </div>
    </div>

    <script>
        let selectedClient = null;

        function showSection(id) {
            var sections = document.querySelectorAll('.section');
            sections.forEach(function(section) {
                section.classList.remove('active');
            });
            document.getElementById(id).classList.add('active');
        }

        function saveClient(nombre, telefono) {
            let clients = JSON.parse(localStorage.getItem('clients')) || [];
            clients.push({ nombre, telefono, telefonoAdicional: '', citas: [] });
            localStorage.setItem('clients', JSON.stringify(clients));
        }

        function loadClients() {
            let clients = JSON.parse(localStorage.getItem('clients')) || [];
            const listadoClientesList = document.getElementById('listado-clientes-list');
            listadoClientesList.innerHTML = '';

            clients.forEach((client, index) => {
                const li = document.createElement('li');
                li.textContent = `Nombre: ${client.nombre}, Teléfono: ${client.telefono}`;
                li.onclick = function() {
                    showClientProfile(index);
                };

                // Botón de eliminar
                const deleteButton = document.createElement('button');
                deleteButton.textContent = 'Eliminar';
                deleteButton.style.marginLeft = '10px';
                deleteButton.onclick = function(event) {
                    event.stopPropagation();
                    deleteClient(index);
                };
                li.appendChild(deleteButton);

                listadoClientesList.appendChild(li);
            });
        }

        function showClientProfile(index) {
            selectedClient = index;
            let clients = JSON.parse(localStorage.getItem('clients'));
            const client = clients[index];
            const infoClienteDiv = document.getElementById('info-cliente');
            infoClienteDiv.innerHTML = `
                <p><strong>Nombre:</strong> ${client.nombre}</p>
                <p><strong>Teléfono:</strong> ${client.telefono}</p>
                <p><strong>Teléfono Adicional:</strong> ${client.telefonoAdicional || 'No especificado'}</p>
            `;
            document.getElementById('editar-nombre').value = client.nombre;
            document.getElementById('editar-telefono').value = client.telefono;
            document.getElementById('telefono-adicional').value = client.telefonoAdicional;
            loadCitasAnteriores();
            showSection('perfil-cliente');
        }

        function loadCitasAnteriores() {
            const citasAnterioresList = document.getElementById('citas-anteriores-list');
            citasAnterioresList.innerHTML = '';
            let clients = JSON.parse(localStorage.getItem('clients'));
            const client = clients[selectedClient];
            client.citas.forEach(cita => {
                const li = document.createElement('li');
                li.textContent = `Fecha: ${cita.fecha}, Hora: ${cita.hora}, Detalles: ${cita.detalles}`;
                citasAnterioresList.appendChild(li);
            });
        }

        function mostrarFormularioCita() {
            document.getElementById('crear-cita-form-container').style.display = 'block';
        }

        document.getElementById('crear-cita-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const fecha = document.getElementById('fecha-cita').value;
            const hora = document.getElementById('hora-cita').value;
            const detalles = document.getElementById('detalles-cita').value;

            let clients = JSON.parse(localStorage.getItem('clients'));
            clients[selectedClient].citas.push({ fecha, hora, detalles });
            localStorage.setItem('clients', JSON.stringify(clients));

            alert('Cita creada con éxito!');
            this.reset();
            loadCitasAnteriores();
            actualizarCitasAgendadas();  // Actualiza la sección de "Citas Agendadas"
            document.getElementById('crear-cita-form-container').style.display = 'none';
        });

        document.getElementById('registro-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const nombre = document.getElementById('nombre').value;
            const telefono = document.getElementById('telefono').value;

            saveClient(nombre, telefono);
            alert('Cliente registrado con éxito!');
            this.reset();
            loadClients();
        });

        document.getElementById('form-editar-cliente').addEventListener('submit', function(e) {
            e.preventDefault();
            let clients = JSON.parse(localStorage.getItem('clients'));
            clients[selectedClient].nombre = document.getElementById('editar-nombre').value;
            clients[selectedClient].telefono = document.getElementById('editar-telefono').value;
            clients[selectedClient].telefonoAdicional = document.getElementById('telefono-adicional').value;

            localStorage.setItem('clients', JSON.stringify(clients));
            alert('Información del cliente actualizada con éxito!');
            loadClients(); // Actualizar lista de clientes
            showClientProfile(selectedClient); // Actualizar perfil del cliente
        });

        function deleteClient(index) {
            if (confirm("¿Seguro que quieres eliminar este cliente?")) {
                let clients = JSON.parse(localStorage.getItem('clients'));
                clients.splice(index, 1);  // Eliminar cliente del array
                localStorage.setItem('clients', JSON.stringify(clients));  // Actualizar localStorage
                loadClients();  // Recargar la lista de clientes
                showSection('listado-clientes');  // Volver a la lista de clientes
            }
        }

        function actualizarCitasAgendadas() {
            const citasAgendadasList = document.getElementById('citas-agendadas-list');
            citasAgendadasList.innerHTML = '';
            let clients = JSON.parse(localStorage.getItem('clients'));
            clients.forEach(client => {
                client.citas.forEach(cita => {
                    const li = document.createElement('li');
                    li.textContent = `Cliente: ${client.nombre} - Fecha: ${cita.fecha}, Hora: ${cita.hora}, Detalles: ${cita.detalles}`;
                    citasAgendadasList.appendChild(li);
                });
            });
        }

        function buscarCliente() {
            const searchString = document.getElementById('buscador').value.toLowerCase();
            let clients = JSON.parse(localStorage.getItem('clients')) || [];
            const listadoClientesList = document.getElementById('listado-clientes-list');
            listadoClientesList.innerHTML = '';

            clients.forEach((client, index) => {
                if (client.nombre.toLowerCase().includes(searchString) || client.telefono.includes(searchString)) {
                    const li = document.createElement('li');
                    li.textContent = `Nombre: ${client.nombre}, Teléfono: ${client.telefono}`;
                    li.onclick = function() {
                        showClientProfile(index);
                    };

                    // Botón de eliminar
                    const deleteButton = document.createElement('button');
                    deleteButton.textContent = 'Eliminar';
                    deleteButton.style.marginLeft = '10px';
                    deleteButton.onclick = function(event) {
                        event.stopPropagation();
                        deleteClient(index);
                    };
                    li.appendChild(deleteButton);

                    listadoClientesList.appendChild(li);
                }
            });
        }

        // Cargar clientes al inicio
        window.onload = function() {
            loadClients();
            actualizarCitasAgendadas();  // Inicializa la sección de "Citas Agendadas"
        };
    </script>
</body>
</html>
