ALTER PROCEDURE USP_Migracion_Departamento
AS
	DECLARE @intFlag int
	SET @intFlag =0

    WHILE (@intFlag <=4)
	BEGIN
		
		INSERT INTO dbo.DepartamentoGugo
		SELECT  distinct Compania,
				Nivel_4,
				'',
				0,
				GETDATE(),
				1,
				Nivel
		FROM dbo.Arbol_Organizacional
		WHERE Nivel=@intFlag
		SET @intFlag = @intFlag + 1;

	END
	

	--UPDATE d
	--SET d.Nombre = o.Nivel_4
	--FROM dbo.DepartamentoGugo d 
	--INNER JOIN dbo.Arbol_Organizacional o
	--ON D.Nombre='Gerencia General Pacifico Salud'
GO
