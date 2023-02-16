//B8
//index.jsp
<a href="view.jsp?page=1">View Employees Table</a>

//view.jsp
<%@page language="java" contentType="text/html" pageEncoding="UTF-8" %>
<%@page import="java.sql.*,javax.servlet.*,java.io.*" %>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Pagination in Jsp</title>
    </head>
    <body>
    <center>
        <%
            String spageid=request.getParameter("page");
            int pageid=Integer.parseInt(spageid);
            int total=5;
            if(pageid==1){}
            else{
                pageid=pageid-1;
                pageid=pageid*total+1;
            }
            out.println("<h2>Page NO:"+pageid+"<h2>");
            out.println("<table border='1' cellspacing='6' width='60%'");
            out.println("<tr><th>ID</th><th>NAME</th>SALARY<th></tr>");
            Class.forName("com.mysql.jdbc.Driver");
            Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/pagination?characterEncoding=utf8","root","1234");
            Statement stmt=conn.createStatement();
            String qry=("select * from emp limit"+(pageid -1)+","+total);
            ResultSet rs=stmt.executeQuery(qry);
            while(rs.next()){
                out.println("<tr><td>"+rs.getInt(1)+"</td><td>"+rs.getString(2)+"</td><td>"+rs.getFloat(3)+"</td></tr>");
            }
            conn.close();
            out.println("</table>");
        %>
        <br><br>
        <a href="view.jsp?page=1">1</a>
        <a href="view.jsp?page=2">2</a>
        <a href="view.jsp?page=3">3</a>
    </center>
    </body>
</html>



//B7
//update.java

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.sql.*;
import java.io.*;


public class update extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException 
    {
        response.setContentType("text/html;charset=UTF-8");
        try (PrintWriter out = response.getWriter()) 
        {
            try
            {
                String name1=request.getParameter("name1");
                if(name1.length()==0){
                    response.sendRedirect("update.jsp");
                }
                else
                {
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/updateDB?characterEncoding=utf8","root","1234");
                    Statement stmt = conn.createStatement();
                    String qry="insert into names values('"+name1+"')";
                    if(stmt.executeUpdate(qry)==1)
                    {
                        System.out.println("Data insertion successful");
                      
                    }
                    response.sendRedirect("update.jsp");
                }
            }
              
                    
            catch(Exception e)
            {
                System.out.println(e);
            }
        }
    }
                 
    
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException 
    {
        response.setContentType("text/html;charset=utf-8");
        try (PrintWriter out = response.getWriter()) 
        {
          try{
            String[] list1=request.getParameterValues("list1");
            if(list1==null)
            {
                response.sendRedirect("update.jsp");
            }
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/updateDB?characterEncoding=utf8","root","1234");
                    Statement stmt = conn.createStatement();
                    String qry;
            for(int i=0;i<list1.length;i++)
            {
                  qry="delete from names where name='"+list1[i]+"'";
                    if(stmt.executeUpdate(qry)==1)
                    {
                        System.out.println(list1[i]+"--Data deleted successfully");
                    }
            } 
            response.sendRedirect("update.jsp");
            }
        
        catch(Exception e)
        {         
            System.out.println(e);
        }
     }
    }
 }
        

//update.jsp

<%-- 
    Document   : update
    Created on : Feb 12, 2023, 12:13:19 PM
    Author     : Pradee
--%>

<%@page contentType="text/html" pageEncoding="UTF-8"%>
<%@page import="java.sql.*"%>
<%@page import="javax.servlet.*" %>
<%@page import="java.io.*" %>


<!DOCTYPE html>
<html>
 <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
    <title>Update Database</title>
</head>
<body>
    <h2 align="center"> Add or Remove Record from Database </h2>
    <form action="update" method="get">
        <b> Enter Name: <input type="text" name="name1"><br>
                <input type="submit" value="Add">

    </form>
      
    <form action="update" method="post">
        <h3> Select an Item and Click Remove. <br></h3>
        <select style="width: 200px" name="list1" multiple="multiple">
        <%
            Class.forName ("com.mysql.jdbc.Driver");
                Connection conn=DriverManager.getConnection ("jdbc:mysql://localhost:3306/updateDB?characterEncoding-utf8", "root", "1234");
                Statement stmt = conn.createStatement();
                String qry="select * from names";
                ResultSet rs=stmt.executeQuery (qry);
                if (rs!=null)    
                {                
                    while (rs.next()){
        %>
        <option><%=rs.getString(1)%></option>
        <%
                  }
            }
        %>
        </select>
        <input type="submit" value="remove">
    </form>
</body>
</html>


//B6

//login.jsp

<%@page language="java" contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>login Page</title>
</head>
<body align="center">
        <h2> Welcome to login page </h2>
        <hr style="background-color: #0080FF; height:5px" align="center"/>
        <br><br>
        <%
            try{
                String username= (String)session.getAttribute ("username");
                if(username=="invalid")
                {                    
        %>
        <h3 style="color:red"><b>Enter Valid Username & Password!</b></h3>      
        <%
                }
                else if (username!=null)
                {
                    response.sendRedirect("homepage.jsp");
                }   
         }
        catch(Exception e)
        {
            System.out.println(e);
        }
        %>        
        <form method="post" action="authorize">
            <table align="center" border="1">
            <tr>
                   <td> <h3 style="color: darkmagenta"> Enter Username: </td>
                   <td> <input type="text" name="UNAME" align="right" style="width:160px"> </td>
            </tr
            <tr>
                <td> <h3 style="color: darkmagenta"> Enter Password: </td>
                <td> <input type="password" name="PWD" align="right" style="width:160px"> </td>
            </tr>   
            <tr>
                   <td align="center"> <input type="submit" value="LOGIN" style="background-color: #0088FF; color:#FFFFFF; font-weight:bolder"> 
                   <td align="center"> <input type="reset" value="RESET" style="background-color: #0088FF; color:#FFFFFF; font-weight:bolder">
                       
            </tr>
       </table>
      </form>
    </body>
</html>

//homepage.jsp

<%@page contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
        <title>JSP Page</title>

</head>      
<body>
    <%
        String username= (String)session.getAttribute("username");
        if (username==null || username=="invalid")
        {
            response.sendRedirect("login.jsp");       
        }
        else
        {
        %>
        <h4>Hello <%=username%>!</h4>
        <%
        }
        %> 
</body>
</html>

//authorize.java
import javax.servlet.ServletException; //import javax.servlet.ServletException; import jakarta.servlet.http.*; //import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest; //import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse; //import javax.servlet.http.HttpServletResponse; import java.sql.*;
import java.io.*;
import java.sql.*;
import javax.servlet.http.*;

public class authorize extends HttpServlet {
    protected void processRequest (HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        
        response.setContentType("text/html; charset=UTF-8");

        try (PrintWriter out = response.getWriter()) {
            String UNAME = request.getParameter("UNAME");
            String PWD = request.getParameter("PWD");
           
// Establishing Database Connection 
            Class.forName("com.mysql.jdbc.Driver");
            Connection conn=DriverManager.getConnection ("jdbc:mysql://localhost:3306/b6?characterEncoding-utf8","root", "1234");
            Statement stmt = conn.createStatement();
            ResultSet rs = stmt.executeQuery("Select * from login where UNAME='"+UNAME+"' and PSWD='"+PWD+"' ");
            
// Redirect to next page based on username and password
            System.out.println(rs);
            if(!rs.next()) {
                HttpSession session=request.getSession();
                session.setAttribute("username", "invalid"); 
                response.sendRedirect("login.jsp");
            }
            else{   
                    HttpSession session=request.getSession(); 
                        session.setAttribute("username", UNAME);
                    response.sendRedirect("homepage.jsp");
            }
        }
        catch (Exception e) {
                System.out.println(e);
        }            
    }   
            // <editor-fold defaultstate="collapsed" desc="HttpServlet methods. Click on the + sign on the left to edit the code.">
    /**
     * Handles the HTTP <code>GET</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Handles the HTTP <code>POST</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Returns a short description of the servlet.
     *
     * @return a String containing servlet description
     */
    @Override
    public String getServletInfo() {
        return "Short description";
    }// </editor-fold>

}

//B5
//dbsearch.jsp

<%@page language="java" contentType="text/html" pageEncoding="UTF-8"%>
<%@page import="java.sql.*" %>
<%@page import="javax.servlet.*" %>
<%@page import="java.io.*" %>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>DB Search</title>
    </head>
    <body>
        <h2>Retrieve the Student information from Database</h2>
        <form method="get">
            Enter Register Number:ś
            <input type="text" name="regno"><br>
            <input type="Submit" value="GetInfo">
            <%
                String regno=request.getParameter("regno");
                if(regno!=null)
                {
                    String qry= "select * from stu_info where regno='"+regno+"' ";
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/b5?charecterEncoding=utf8","root","1234");
                    Statement stmt= conn.createStatement();
                    ResultSet rs=stmt.executeQuery(qry);
                    System.out.println("Outside resultset!");
                    if(rs.next()){
                        System.out.println("inside resultset!");
                    
            %>
                <table border="1">
                    <tr>
                        <th>Student Name</th>
                        <th>Gender</th>
                        <th>DOB</th>
                        <th>SSLC Percentage</th>
                        <th>PUC Percentage</th>
                        <th>Degree Percentage</th>
                    </tr>
                    <tr>
                        <td><%=rs.getString(2)%></td>
                        <td><%=rs.getString(3)%></td>
                        <td><%=rs.getString(4)%></td>
                        <td><%=rs.getString(5)%></td>
                        <td><%=rs.getString(6)%></td>
                        <td><%=rs.getString(7)%></td>
                    </tr>
                    <%
                    }
                    else
                        out.println("<br>Unable to get information. Register number not fpund!");
                    }
                    %>
                </table>
        </form>
    </body>
</html>


//B4
//insert.java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.sql.*;
import java.io.*;

public class insert extends HttpServlet {

    protected void processRequest(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        try (PrintWriter out = response.getWriter()) {
            String regno= request.getParameter("regno");
            String name= request.getParameter("name");
            String stuclass= request.getParameter("stuclass");
            String age= request.getParameter("age");
            String gender= request.getParameter("gender");
           try
            {
                Class.forName("com.mysql.jdbc.Driver");
                    Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/b4?characterEncoding=utf8","root","1234");
                    Statement stmt = conn.createStatement();
         stmt.executeUpdate("insert into stu_info values('"+regno+"','"+name+"','"+stuclass+"','"+age+"','"+gender+"')");
                ResultSet rs=stmt.executeQuery("select * from stu_info");
      
            out.println("<html><body bgcolor=gray><center><h2>STUDENT INFO</h2></center>");
            out.println("<table align=center border=1 bordercolor=green size =3>");
            out.println("<tr bgcolor=purple>");
            out.println("<th><font color=white>StudentID</font></th>");
            out.println("<th><font color=white>StudentName</font></th>");
            out.println("<th><font color=white>class</font></th>");
            out.println("<th><font color=white>Age</font></th>");
            out.println("<th><font color=white>Gender</font></th>");
            out.println("</tr>");
            while(rs.next())
            {
                out.println("<tr bgcolor=ivory>");
                out.println("<td>"+rs.getString(1) + "</td>");
                out.println("<td>"+rs.getString(2) + "</td>");
                out.println("<td>"+rs.getString(3) + "</td>");
                out.println("<td>"+rs.getString(4) + "</td>");
                out.println("<td>"+rs.getString(5) + "</td>");
                out.println("</tr>");
            }
            out.println("</table><br>");
            out.println("</body>");
            out.println("</html>");
            }
        catch (Exception e)
        {
            System.out.println("ghje");
        }
    }
}

    // <editor-fold defaultstate="collapsed" desc="HttpServlet methods. Click on the + sign on the left to edit the code.">
    /**
     * Handles the HTTP <code>GET</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Handles the HTTP <code>POST</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Returns a short description of the servlet.
     *
     * @return a String containing servlet description
     */
    @Override
    public String getServletInfo() {
        return "Short description";
    }// </editor-fold>

}


//Student.jsp
<%@page language="java" contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>JSP Page</title>
    </head>
    <body>
        <form action="insert">
    <center>
        <h1>Student Information</h1><br>
        <table border="1">
            <tr>
                <td>REG_NO:</td>
                <td><input type="Text" name="regno"></td>
            </tr>
            <tr>
                <td>NAME:</td>
                <td><input type="Text" name="name"></td>
            </tr>
            <tr>
                <td>CLASS:</td>
                <td><input type="Text" name="stuclass"></td>
            </tr>
            <tr>
                <td>AGE:</td>
                <td><input type="Text" name="age"></td>
            </tr>
            <tr>
                <td>GENDER:</td>
                <td><input type="Text" name="gender"></td>
            </tr>
            <tr><td></td><td><input type="Submit" value="submit"></tr>
        </table>
    </center>
        </form>
    </body>
</html>


//B3
//telephone.jsp

<%@page contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Telephone Directoryu</title>
    </head>
    <body>
        <form action="Search" method="get">
            <h1>Click your choice</h1>
            <br>
            <input type="radio" name="name" value="telephone_no" checked>Telephone Number<br>
            <input type="radio" name="name" value="name">Name
            <h1>Enter Your choice</h1>
            <input type="text" name="val">
            <input type="submit" value="submit">
        </form>
    </body>
</html>

//Search.java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class Search extends HttpServlet {

    protected void processRequest(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        try (PrintWriter out = response.getWriter()) {
            String name=request.getParameter("name");
                String val= request.getParameter("val");
            try
            {
                Class.forName("com.mysql.jdbc.Driver");
                        Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/telephone?characterEncoding=utf8","root","1234");
                        Statement stmt = conn.createStatement();
                        String qry1;
                        if(name.equals("name"))
                            qry1="select * from TD where NAME='"+val+"'";
                        else
                            qry1="select * from TD where number='"+val+"'";
                        ResultSet rs = stmt.executeQuery(qry1);
                        out.println("<br> Data Retrived from tp.TD is:<br><br>&nbsp&nbsp"+"NAME"+"&nbsp&nbsp|&nbsp&nbsp"+"NUMBER"+"&nbsp&nbsp|&nbsp&nbsp"+"ADDRESS<br>");
                        while(rs.next())
                        {
                            out.println("|"+rs.getString(1)+"&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp|&nbsp&nbsp"+rs.getString(2)+"&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp|"+rs.getString(3)+"<br>");
                        }
            } catch(Exception e){
                e.printStackTrace();
                out.println("IN catch block");
                        
            }
            
        }
    }

    // <editor-fold defaultstate="collapsed" desc="HttpServlet methods. Click on the + sign on the left to edit the code.">
    /**
     * Handles the HTTP <code>GET</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Handles the HTTP <code>POST</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Returns a short description of the servlet.
     *
     * @return a String containing servlet description
     */
    @Override
    public String getServletInfo() {
        return "Short description";
    }// </editor-fold>

}



//B2
//cookiestest.java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.Cookie;

import java.util.*;

public class CookieTest extends HttpServlet {

    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        //response.setContentType("text/html;charset=UTF-8");
        try (PrintWriter out = response.getWriter()) {
            Cookie c1= new Cookie("username","DSCE");
            Cookie c2= new Cookie("password","MCA-VTU");
            
            response.addCookie(c1);
            response.addCookie(c2);
            
            response.setContentType("text/html");
            out.println("<!DOCTYPE html>");
            out.println("<html>");
            out.println("<head>");
            out.println("<title>Set cookie</title>");            
            out.println("</head>");
            out.println("<body>");
            out.println("<br><h2>Plese click the button to see the cookies sent to you.</h2><br>");
            out.println("<form method=\"post\"><input type=\"submit\" value=\"submit\"></form>");
            out.println("</body>");
            out.println("</html>");
        }
    }
    @Override
    public void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        try(PrintWriter out = response.getWriter()){
            response.setContentType("text/html");
            out.println("<html>");
            out.println("<head>");
            out.println("<title>Show cookie</title>"); 
            out.println("</head><body><br><h2>Here All the headers.</h2><br><h3>");
            Enumeration enum1=request.getHeaderNames();
            while(enum1.hasMoreElements())
            {
                String header=(String)enum1.nextElement();
                out.println("<b>"+header+"</b>");
                out.print(request.getHeader(header)+"<br>");
            }
            out.println("<h3><h2><b><br>And here are all the cookies.<br></b></h2></h3>");
            Cookie[] Cookies=request.getCookies();
            int length=Cookies.length;
            for(int i=0;i<length;i++)
            {
                Cookie cookie=Cookies[i];
                out.println("<br>cookie Name:"+cookie.getName());
                out.println("<br>cookie Value:"+cookie.getValue());
            }
            out.println("</h3></body></html>");
            
        }
    }
}

    // <editor-fold defaultstate="collapsed" desc="HttpServlet methods. Click on the + sign on the left to edit the code.">
    /**
     * Handles the HTTP <code>GET</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Handles the HTTP <code>POST</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Returns a short description of the servlet.
     *
     * @return a String containing servlet description
     */
    @Override
    public String getServletInfo() {
        return "Short description";
    }// </editor-fold>

}


//B1
//insert.jsp
<%-- 
    Document   : index
    Created on : Jan 23, 2023, 6:46:28 PM
    Author     : Pradee
--%>

<%@page contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Session</title>
    </head>
    <body>
        <form action="save.jsp" method="post">
            <h2>Enter the Name for the Session Variable</h2>
            <h3>Name:<input type="Text" name="username"><br></h3>
            <input type="Submit" value="submit">
        </form>
    </body>
</html>

//save.jsp
<%-- 
    Document   : save
    Created on : Jan 23, 2023, 6:50:19 PM
    Author     : Pradee
--%>

<%@page contentType="text/html" pageEncoding="UTF-8"%>
<%
    String username=request.getParameter("username");
    if(username==null)
        username="";
    session.setAttribute("username",username);
    %>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Save Session</title>
    </head>
    <body>
        <h1>Session Created!</h1>
        <h3><p><a href="show.jsp">Click here to view the Session value</a></p></h3>
    </body>
</html>


//show.jsp


<%-- 
    Document   : show
    Created on : Jan 23, 2023, 6:52:12 PM
    Author     : Pradee
--%>

<%@page contentType="text/html" pageEncoding="UTF-8"%>
<%
 String username=(String)session.getAttribute("username");
  if(username==null)
     username="";
 %>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Show Session</title>
    </head>
    <body>
        <h1>Display Session</h1>
        <h3><p>Welcome: <%=username %></p></h3>
    </body>
</html>
 
