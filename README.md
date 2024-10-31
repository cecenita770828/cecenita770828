<!DOCTYPE html>
<html>
<head>
    <base target="_top">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- CSS -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.7.2/font/bootstrap-icons.css">
    <?!= include('Styles'); ?>
</head>
<body>
    <!-- Loading Spinner -->
    <div class="loading">
        <div class="spinner"></div>
    </div>

    <!-- Mobile Toggle -->
    <button class="mobile-toggle d-md-none" onclick="toggleSidebar()">
        <i class="bi bi-list"></i>
    </button>

    <div class="app-wrapper">
        <!-- Sidebar -->
        <nav class="sidebar" id="sidebar">
            <div class="sidebar-header">
                <h1 class="sidebar-title">SGI</h1>
                <p class="sidebar-subtitle">Sistema de Gestión</p>
            </div>
            
            <ul class="nav-vertical">
                <li>
                    <a href="#" class="nav-link active" data-module="planeacion">
                        <i class="bi bi-calendar3"></i>
                        <span>Planeación</span>
                    </a>
                </li>
                <li>
                    <a href="#" class="nav-link" data-module="almacen">
                        <i class="bi bi-box-seam"></i>
                        <span>Almacén</span>
                    </a>
                </li>
                <li>
                    <a href="#" class="nav-link" data-module="rrhh-asistencia">
                        <i class="bi bi-people"></i>
                        <span>RRHH Asistencia</span>
                    </a>
                </li>
                <li>
                    <a href="#" class="nav-link" data-module="rrhh-actividades">
                        <i class="bi bi-list-check"></i>
                        <span>RRHH Actividades</span>
                    </a>
                </li>
                <li>
                    <a href="#" class="nav-link" data-module="comercio">
                        <i class="bi bi-globe"></i>
                        <span>Comercio Exterior</span>
                    </a>
                </li>
                <li>
                    <a href="#" class="nav-link" data-module="compras">
                        <i class="bi bi-cart"></i>
                        <span>Compras</span>
                    </a>
                </li>
                <li>
                    <a href="#" class="nav-link" data-module="kanban">
                        <i class="bi bi-kanban"></i>
                        <span>Tablero Kanban</span>
                    </a>
                </li>
            </ul>

            <div class="sidebar-footer">
                <div class="user-info">
                    <img src="https://via.placeholder.com/32" alt="User" class="user-avatar">
                    <div class="user-details">
                        <span class="user-name">Admin User</span>
                        <span class="user-role">Administrador</span>
                    </div>
                </div>
            </div>
        </nav>

        <!-- Main Content -->
        <main class="main-content">
            <!-- Content Header -->
            <header class="content-header">
                <h2 class="module-title">Planeación</h2>
                <div class="header-actions">
                    <button class="btn btn-primary d-none" id="btnAdd">
                        <i class="bi bi-plus"></i> Nuevo
                    </button>
                    <button class="btn btn-outline-secondary d-none" id="btnFilter">
                        <i class="bi bi-funnel"></i> Filtrar
                    </button>
                </div>
            </header>

            <!-- Module Content -->
            <div class="module-content">
                <!-- Los módulos se cargarán aquí dinámicamente -->
            </div>
        </main>
    </div>

    <!-- Templates for each module -->
    <template id="template-planeacion">
        <div class="table-wrapper">
            <table class="table">
                <thead>
                    <tr>
                        <th>Máquina</th>
                        <th>Producto</th>
                        <th>Cantidad</th>
                        <th>Operador</th>
                        <th>Turno</th>
                        <th>Estado</th>
                        <th>Acciones</th>
                    </tr>
                </thead>
                <tbody></tbody>
            </table>
        </div>
    </template>
    <!-- Templates for other modules -->
    <template id="template-almacen">
        <div class="table-wrapper">
            <table class="table">
                <thead>
                    <tr>
                        <th>Código</th>
                        <th>Nombre</th>
                        <th>Stock</th>
                        <th>Mínimo</th>
                        <th>Ubicación</th>
                        <th>Estado</th>
                        <th>Acciones</th>
                    </tr>
                </thead>
                <tbody></tbody>
            </table>
        </div>
    </template>

    <template id="template-rrhh-asistencia">
        <div class="metrics-grid">
            <div class="metric-card">
                <div class="metric-icon bg-primary">
                    <i class="bi bi-people"></i>
                </div>
                <div class="metric-info">
                    <span class="metric-value" id="asistieron">-</span>
                    <span class="metric-label">Personal Presente</span>
                </div>
            </div>
            <div class="metric-card">
                <div class="metric-icon bg-success">
                    <i class="bi bi-person-check"></i>
                </div>
                <div class="metric-info">
                    <span class="metric-value" id="requeridos">-</span>
                    <span class="metric-label">Personal Requerido</span>
                </div>
            </div>
            <div class="metric-card">
                <div class="metric-icon bg-warning">
                    <i class="bi bi-person-plus"></i>
                </div>
                <div class="metric-info">
                    <span class="metric-value" id="contratacion">-</span>
                    <span class="metric-label">Contratación Pendiente</span>
                </div>
            </div>
            <div class="metric-card">
                <div class="metric-icon bg-info">
                    <i class="bi bi-graph-up"></i>
                </div>
                <div class="metric-info">
                    <span class="metric-value" id="porcentaje">-</span>
                    <span class="metric-label">% Asistencia</span>
                </div>
            </div>
        </div>
    </template>

    <template id="template-rrhh-actividades">
        <div class="table-wrapper">
            <table class="table">
                <thead>
                    <tr>
                        <th>Actividad</th>
                        <th>Responsable</th>
                        <th>Área</th>
                        <th>Participantes</th>
                        <th>Estado</th>
                        <th>Fecha</th>
                        <th>Acciones</th>
                    </tr>
                </thead>
                <tbody></tbody>
            </table>
        </div>
    </template>

    <template id="template-comercio">
        <div class="table-wrapper">
            <table class="table">
                <thead>
                    <tr>
                        <th>Referencia</th>
                        <th>Proveedor</th>
                        <th>Monto</th>
                        <th>Fecha Estimada</th>
                        <th>Estado</th>
                        <th>Acciones</th>
                    </tr>
                </thead>
                <tbody></tbody>
            </table>
        </div>
    </template>

    <template id="template-compras">
        <div class="table-wrapper">
            <table class="table">
                <thead>
                    <tr>
                        <th>Orden #</th>
                        <th>Proveedor</th>
                        <th>Descripción</th>
                        <th>Monto</th>
                        <th>Fecha Requerida</th>
                        <th>Estado</th>
                        <th>Acciones</th>
                    </tr>
                </thead>
                <tbody></tbody>
            </table>
        </div>
    </template>

    <template id="template-kanban">
        <div class="kanban-container">
            <div class="kanban-toolbar">
                <select class="form-select" id="kanban-filter">
                    <option value="">Todas las áreas</option>
                    <option value="Calidad">Calidad</option>
                    <option value="Producción">Producción</option>
                    <option value="Almacén">Almacén</option>
                    <option value="Mantenimiento">Mantenimiento</option>
                </select>
            </div>
            
            <div class="kanban-board">
                <!-- Backlog Column -->
                <div class="kanban-column">
                    <div class="kanban-column-header">
                        <h3>Pendientes</h3>
                        <span class="task-count">0</span>
                    </div>
                    <div class="kanban-list" data-status="backlog"></div>
                </div>

                <!-- Todo Column -->
                <div class="kanban-column">
                    <div class="kanban-column-header">
                        <h3>Por Hacer</h3>
                        <span class="task-count">0</span>
                    </div>
                    <div class="kanban-list" data-status="todo"></div>
                </div>

                <!-- In Progress Column -->
                <div class="kanban-column">
                    <div class="kanban-column-header">
                        <h3>En Proceso</h3>
                        <span class="task-count">0</span>
                    </div>
                    <div class="kanban-list" data-status="inProgress"></div>
                </div>

                <!-- Done Column -->
                <div class="kanban-column">
                    <div class="kanban-column-header">
                        <h3>Completado</h3>
                        <span class="task-count">0</span>
                    </div>
                    <div class="kanban-list" data-status="done"></div>
                </div>
            </div>
        </div>
    </template>
    <!-- Modal Templates -->
    <div class="modal fade" id="formModal" tabindex="-1" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title"></h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <!-- El formulario se cargará dinámicamente aquí -->
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                    <button type="button" class="btn btn-primary" id="btnSave">Guardar</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Confirmation Modal -->
    <div class="modal fade" id="confirmModal" tabindex="-1" aria-hidden="true">
        <div class="modal-dialog modal-sm">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">Confirmar</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    ¿Está seguro de realizar esta acción?
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                    <button type="button" class="btn btn-danger" id="btnConfirm">Confirmar</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Toast Notification -->
    <div class="toast-container position-fixed bottom-0 end-0 p-3">
        <div class="toast" role="alert" aria-live="assertive" aria-atomic="true" data-bs-delay="3000">
            <div class="toast-header">
                <i class="bi bi-info-circle me-2"></i>
                <strong class="me-auto">Notificación</strong>
                <button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close"></button>
            </div>
            <div class="toast-body"></div>
        </div>
    </div>

    <!-- Scripts -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
<?!= include('JavaScript'); ?>
   
</body>
</html>

