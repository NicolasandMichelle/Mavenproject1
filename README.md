# Mavenproject1
appdelivery
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package com.mycompany.mavenproject1;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

/**
 *
 * @author ORGSA
 */
public class Mavenproject1 {

    /**
     *
     * @param args
     */
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }


/**
 *
 * @author ORGSA
 */

    // Datos de conexión
    private static final String URL = "jdbc:sqlserver://localhost:1433;databaseName=MiBaseDeDatos;encrypt=true;trustServerCertificate=true;";
    private static final String USUARIO = "sa";  // Reemplaza con tu usuario
    private static final String PASSWORD = "tu_contraseña"; // Reemplaza con tu contraseña

    
    public static void conectarYConsultar(){ 
        try (Connection conexion = DriverManager.getConnection(URL, USUARIO, PASSWORD)) {
            System.out.println("✅ Conexión exitosa a SQL Server");

            // Crear y ejecutar una consulta SQL
            String sql = "SELECT * FROM Clientes";  // Asegúrate de que la tabla existe
            try (Statement stmt = conexion.createStatement();
                 ResultSet rs = stmt.executeQuery(sql)) {

                while (rs.next()) {
                    System.out.println("ID: " + rs.getInt("id") + ", Nombre: " + rs.getString("nombre"));
                }
            }

        } catch (SQLException e) {
            System.err.println("❌ Error de conexión: " + e.getMessage());
        }
    }
}
