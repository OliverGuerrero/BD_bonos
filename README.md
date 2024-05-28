USE [DB_Bonos]
GO
/****** Object:  Table [dbo].[Bonos]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Bonos](
	[ID_Bono] [int] IDENTITY(1,1) NOT NULL,
	[ID_Colaborador] [int] NOT NULL,
	[Monto] [decimal](10, 2) NOT NULL,
	[TipoVentaProducto] [varchar](2) NOT NULL,
	[TipoVentaServicio] [varchar](2) NOT NULL,
	[PorcentajeRentabilidad] [decimal](5, 2) NOT NULL,
	[BonoCalculado] [bit] NOT NULL,
	[FechaCalculo] [date] NOT NULL,
	[MontoBono] [decimal](10, 2) NOT NULL,
	[Estado] [varchar](20) NOT NULL,
	[Justificacion] [varchar](max) NULL,
PRIMARY KEY CLUSTERED 
(
	[ID_Bono] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Colaboradores]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Colaboradores](
	[ID_Colaborador] [int] IDENTITY(1,1) NOT NULL,
	[Nombre] [varchar](100) NOT NULL,
	[Correo] [varchar](50) NOT NULL,
	[Departamento] [varchar](50) NULL,
	[ID_Cliente] [int] NULL,
	[CodColaborador] [varchar](20) NULL,
	[Fecha_Ingreso] [date] NULL,
PRIMARY KEY CLUSTERED 
(
	[ID_Colaborador] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Compañias]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Compañias](
	[ID_Compañias] [int] IDENTITY(1,1) NOT NULL,
	[Nombre] [varchar](40) NULL,
	[Pais] [varchar](60) NULL,
	[ID_Colaborador] [int] NOT NULL
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Factura]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Factura](
	[id_Factura] [int] IDENTITY(1,1) NOT NULL,
	[Descripcion] [varchar](50) NULL,
	[Numero_factura] [varchar](20) NULL,
	[ID_CLiente] [int] NOT NULL,
	[Fecha_creacion] [date] NULL,
	[Servicios_Comprados] [varchar](20) NULL,
 CONSTRAINT [PK_Factura] PRIMARY KEY CLUSTERED 
(
	[id_Factura] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Notificaciones]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Notificaciones](
	[ID_Notificacion] [int] IDENTITY(1,1) NOT NULL,
	[ID_Colaborador] [int] NOT NULL,
	[TipoNotificacion] [varchar](50) NOT NULL,
	[ContenidoNotificacion] [varchar](max) NOT NULL,
	[FechaHoraNotificacion] [datetime] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[ID_Notificacion] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Pagos]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Pagos](
	[ID_Pago] [int] IDENTITY(1,1) NOT NULL,
	[ID_Bono] [int] NOT NULL,
	[Monto] [decimal](10, 2) NOT NULL,
	[FechaPago] [date] NOT NULL,
	[MetodoPago] [varchar](20) NOT NULL,
	[NumeroReferencia] [varchar](50) NULL,
PRIMARY KEY CLUSTERED 
(
	[ID_Pago] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Transmital]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Transmital](
	[Id_Transmital] [int] IDENTITY(1,1) NOT NULL,
	[Trasmital_Code] [varchar](20) NULL,
	[Transmital_Date] [date] NULL,
	[Due_date] [date] NULL,
	[Numero_de_Archivo] [int] NULL,
	[ID_Cliente] [int] NOT NULL,
	[Correo] [varchar](20) NULL,
	[Descripcion] [varchar](70) NULL,
	[ID_Venta] [int] NOT NULL,
 CONSTRAINT [PK_Transmital] PRIMARY KEY CLUSTERED 
(
	[Id_Transmital] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Vendedores]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Vendedores](
	[ID_Cliente] [int] IDENTITY(1,1) NOT NULL,
	[Nombre] [varchar](100) NOT NULL,
	[Estado] [varchar](100) NOT NULL,
	[Correo] [varchar](50) NOT NULL,
	[Telefono] [varchar](15) NOT NULL,
	[CodUsuario] [varchar](30) NULL,
PRIMARY KEY CLUSTERED 
(
	[ID_Cliente] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Ventas]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Ventas](
	[ID_Venta] [int] IDENTITY(1,1) NOT NULL,
	[ID_Colaborador] [int] NOT NULL,
	[Fecha] [date] NOT NULL,
	[Monto] [decimal](10, 2) NOT NULL,
	[LineaProducto] [varchar](100) NULL,
	[CostoLineaProducto] [decimal](10, 2) NULL,
	[LineaServicio] [varchar](100) NULL,
	[PrecioServicio] [decimal](10, 2) NULL,
	[LineaContrato] [varchar](100) NULL,
PRIMARY KEY CLUSTERED 
(
	[ID_Venta] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
ALTER TABLE [dbo].[Bonos] ADD  DEFAULT ('Pendiente') FOR [Estado]
GO
ALTER TABLE [dbo].[Bonos]  WITH CHECK ADD  CONSTRAINT [FK_Bonos_Colaboradores] FOREIGN KEY([ID_Colaborador])
REFERENCES [dbo].[Colaboradores] ([ID_Colaborador])
GO
ALTER TABLE [dbo].[Bonos] CHECK CONSTRAINT [FK_Bonos_Colaboradores]
GO
ALTER TABLE [dbo].[Colaboradores]  WITH CHECK ADD FOREIGN KEY([ID_Cliente])
REFERENCES [dbo].[Vendedores] ([ID_Cliente])
GO
ALTER TABLE [dbo].[Colaboradores]  WITH CHECK ADD  CONSTRAINT [FK_Colaboradores_Vendedores] FOREIGN KEY([ID_Cliente])
REFERENCES [dbo].[Vendedores] ([ID_Cliente])
ON UPDATE CASCADE
GO
ALTER TABLE [dbo].[Colaboradores] CHECK CONSTRAINT [FK_Colaboradores_Vendedores]
GO
ALTER TABLE [dbo].[Compañias]  WITH CHECK ADD  CONSTRAINT [FK_Compañias_Colaboradores] FOREIGN KEY([ID_Compañias])
REFERENCES [dbo].[Colaboradores] ([ID_Colaborador])
GO
ALTER TABLE [dbo].[Compañias] CHECK CONSTRAINT [FK_Compañias_Colaboradores]
GO
ALTER TABLE [dbo].[Factura]  WITH CHECK ADD  CONSTRAINT [FK_Factura_Vendedores] FOREIGN KEY([ID_CLiente])
REFERENCES [dbo].[Vendedores] ([ID_Cliente])
ON UPDATE CASCADE
GO
ALTER TABLE [dbo].[Factura] CHECK CONSTRAINT [FK_Factura_Vendedores]
GO
ALTER TABLE [dbo].[Notificaciones]  WITH CHECK ADD  CONSTRAINT [FK_Notificaciones_Colaboradores] FOREIGN KEY([ID_Colaborador])
REFERENCES [dbo].[Colaboradores] ([ID_Colaborador])
GO
ALTER TABLE [dbo].[Notificaciones] CHECK CONSTRAINT [FK_Notificaciones_Colaboradores]
GO
ALTER TABLE [dbo].[Pagos]  WITH CHECK ADD FOREIGN KEY([ID_Bono])
REFERENCES [dbo].[Bonos] ([ID_Bono])
GO
ALTER TABLE [dbo].[Transmital]  WITH CHECK ADD  CONSTRAINT [FK_Transmital_Vendedores] FOREIGN KEY([ID_Cliente])
REFERENCES [dbo].[Vendedores] ([ID_Cliente])
ON UPDATE CASCADE
GO
ALTER TABLE [dbo].[Transmital] CHECK CONSTRAINT [FK_Transmital_Vendedores]
GO
ALTER TABLE [dbo].[Transmital]  WITH CHECK ADD  CONSTRAINT [FK_Transmital_Ventas] FOREIGN KEY([ID_Venta])
REFERENCES [dbo].[Ventas] ([ID_Venta])
GO
ALTER TABLE [dbo].[Transmital] CHECK CONSTRAINT [FK_Transmital_Ventas]
GO
ALTER TABLE [dbo].[Ventas]  WITH CHECK ADD FOREIGN KEY([ID_Colaborador])
REFERENCES [dbo].[Colaboradores] ([ID_Colaborador])
GO
/****** Object:  StoredProcedure [dbo].[CalcularBonos]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[CalcularBonos]
AS
BEGIN
    -- Obtener la fecha actual
    DECLARE @FechaActual DATE = GETDATE();

    -- Obtener los totales por línea de venta dentro del período
    SELECT c.ID_Colaborador,
           SUM(CASE WHEN v.LineaProducto IS NOT NULL THEN v.Monto ELSE 0 END) AS TotalProductos,
           SUM(CASE WHEN v.LineaServicio IS NOT NULL THEN v.Monto ELSE 0 END) AS TotalServicios,
           SUM(CASE WHEN v.LineaContrato IS NOT NULL THEN v.Monto ELSE 0 END) AS TotalContratos
    INTO #VentasPeriodo
    FROM Ventas v
    INNER JOIN Colaboradores c ON v.ID_Colaborador = c.ID_Colaborador
    WHERE v.Fecha <= @FechaActual
    GROUP BY c.ID_Colaborador

    -- Calcular y registrar los bonos
    DECLARE @ID_Colaborador INT,
            @TotalProductos DECIMAL(10, 2),
            @TotalServicios DECIMAL(10, 2),
            @TotalContratos DECIMAL(10, 2),
            @MontoBono DECIMAL(10, 2)

    DECLARE cur_ventas CURSOR FOR
        SELECT ID_Colaborador, TotalProductos, TotalServicios, TotalContratos
        FROM #VentasPeriodo

    OPEN cur_ventas
    FETCH NEXT FROM cur_ventas INTO @ID_Colaborador, @TotalProductos, @TotalServicios, @TotalContratos

    WHILE @@FETCH_STATUS = 0
    BEGIN
        -- Calcular bono por productos
        IF @TotalProductos > 0
        BEGIN
            SET @MontoBono = @TotalProductos * 0.05;
            INSERT INTO Bonos (ID_Colaborador, Monto, TipoVentaProducto, TipoVentaServicio, PorcentajeRentabilidad, BonoCalculado, FechaCalculo, MontoBono)
            VALUES (@ID_Colaborador, @TotalProductos, 'Si', 'No', 5, 1, GETDATE(), @MontoBono);
        END

        -- Calcular bono por servicios
        IF @TotalServicios > 0
        BEGIN
            SET @MontoBono = @TotalServicios * 0.03;
            INSERT INTO Bonos (ID_Colaborador, Monto, TipoVentaProducto, TipoVentaServicio, PorcentajeRentabilidad, BonoCalculado, FechaCalculo, MontoBono)
            VALUES (@ID_Colaborador, @TotalServicios, 'No', 'Si', 25, 1, GETDATE(), @MontoBono);
        END

        -- Calcular bono por contratos
        IF @TotalContratos > 0
        BEGIN
            IF @TotalContratos = 'Nuevo'
            BEGIN
                SET @MontoBono = @TotalContratos * 0.03;
            END
            ELSE IF @TotalContratos = 'Renovación'
            BEGIN
                SET @MontoBono = @TotalContratos * 0.01;
            END
            INSERT INTO Bonos (ID_Colaborador, Monto, TipoVentaProducto, TipoVentaServicio, PorcentajeRentabilidad, BonoCalculado, FechaCalculo, MontoBono)
            VALUES (@ID_Colaborador, @TotalContratos, 'No', 'No', 0, 1, GETDATE(), @MontoBono);
        END

        FETCH NEXT FROM cur_ventas INTO @ID_Colaborador, @TotalProductos, @TotalServicios, @TotalContratos
    END

    CLOSE cur_ventas
    DEALLOCATE cur_ventas

    -- Eliminar tabla temporal
    DROP TABLE #VentasPeriodo
END
GO
/****** Object:  StoredProcedure [dbo].[GetAllVendedores]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[GetAllVendedores]
AS
BEGIN
    SELECT * FROM Vendedores;
END;
GO
/****** Object:  StoredProcedure [dbo].[InsertarNuevoVendedor]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[InsertarNuevoVendedor]
    @Nombre VARCHAR(100),
    @CodUsuario VARCHAR(30),
    @Correo VARCHAR(50),
    @Estado VARCHAR(10),
	@Telefono Varchar(20)
AS
BEGIN
    -- Verificar si el estado es válido
    IF @Estado NOT IN ('Activo', 'Inactivo')
    BEGIN
        RAISERROR('El estado del vendedor debe ser ''Activo'' o ''Inactivo''.', 16, 1)
        RETURN
    END

    -- Insertar el nuevo vendedor
    INSERT INTO Vendedores (Nombre, CodUsuario, Correo, Estado,Telefono)
    VALUES (@Nombre, @CodUsuario, @Correo,@Estado, @Telefono)

    -- Obtener el ID del nuevo vendedor insertado
    SELECT SCOPE_IDENTITY() AS NuevoID_Vendedor
END
GO
/****** Object:  StoredProcedure [dbo].[ObtenerBonosColaboradores]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[ObtenerBonosColaboradores]
AS
BEGIN
    SELECT c.Nombre AS NombreColaborador,
           SUM(b.MontoBono) AS MontoBono,
           COUNT(v.ID_Venta) AS TotalVentas
    FROM Colaboradores c
    LEFT JOIN Bonos b ON c.ID_Colaborador = b.ID_Colaborador
    LEFT JOIN Pagos p ON b.ID_Bono = p.ID_Bono
    LEFT JOIN Ventas v ON c.ID_Colaborador = v.ID_Colaborador
    GROUP BY c.Nombre
END
GO
/****** Object:  StoredProcedure [dbo].[ObtenerColaboradores]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[ObtenerColaboradores]
AS
BEGIN
    SELECT ID_Colaborador, Nombre
    FROM Colaboradores
END
GO
/****** Object:  StoredProcedure [dbo].[ObtenerDetalleBonosFacturas]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[ObtenerDetalleBonosFacturas]
AS
BEGIN
    SELECT
        f.Numero_factura AS 'IdFactura',
        CASE
            WHEN b.TipoVentaProducto = 'Si' THEN 'Producto'
            WHEN b.TipoVentaServicio = 'Si' THEN 'Servicio'
            ELSE 'Contrato'
        END AS 'TipoBono',
        b.MontoBono AS 'MontoBono',
        b.ID_Bono AS 'IdBono',
        v.Nombre AS 'Cliente',
        v.Estado AS 'Estado',
        f.Descripcion AS 'Descripcion'
    FROM
        Bonos b
        INNER JOIN Colaboradores co ON b.ID_Colaborador = co.ID_Colaborador
        INNER JOIN Vendedores v ON co.ID_Cliente = v.ID_Cliente
        INNER JOIN Factura f ON v.ID_Cliente = f.ID_CLiente
    ORDER BY
        f.Numero_factura
END
GO
/****** Object:  StoredProcedure [dbo].[RegistrarPago]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[RegistrarPago]
    @ID_Bono INT,
    @Monto DECIMAL(10, 2)
AS
BEGIN
    INSERT INTO Pagos (ID_Bono, Monto, FechaPago)
    VALUES (@ID_Bono, @Monto, GETDATE())
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateVendedor]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[UpdateVendedor]
    @ID_Cliente INT,
    @Nombre VARCHAR(50),
    @CodUsuario VARCHAR(50),
    @Correo VARCHAR(50),
    @Estado VARCHAR(50),
	@Telefono VARCHAR(20)
AS
BEGIN
    UPDATE Vendedores
    SET Nombre = @Nombre,
        CodUsuario = @CodUsuario,
        Correo = @Correo,
        Estado = @Estado,
		Telefono =@Telefono
    WHERE ID_Cliente = @ID_Cliente
END
GO
/****** Object:  StoredProcedure [dbo].[VerBonosCalculados]    Script Date: 28/05/2024 01:46:22 p. m. ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[VerBonosCalculados]
    @Fecha DATE
AS
BEGIN
    -- Seleccionar los registros insertados en la tabla Bonos para la fecha especificada
    SELECT *
    FROM Bonos
    WHERE FechaCalculo = @Fecha;
END
GO
