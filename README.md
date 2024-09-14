create  database analitica1;
use analitica1;

CREATE TABLE datos_nalitica (
    id INT PRIMARY KEY,
    genero INT,
    edad INT,
    nivel_educativo INT,
    ingreso_bruto_mensual DECIMAL(10,2)
);
/* 
consulta para determinar la cantidad de hombre y mujeres.
*/
select 
   case 
   when genero = 1 then "hombre"
   when genero = 2 then "mujer"
   else 
   "otros"
   end as genero,count(*) as total
   from datos_nalitica
   group by genero;


/* 
consulta para determinar el ingreso promedio por genero;
*/
select 
case 
when genero =1 then "hombre"
when genero = 2 then "mujer"
else"otros"
end as genero, avg (ingreso_bruto_mensual) as ingreso_promedio 
from datos_nalitica
group by genero;

/* 
consulta para determinar nivel educativo por genero.
*/

select 
   case 
   when genero = 1 then "hombre"
   when genero = 2 then "mujer"
   else 
   "otros"
   end as genero,count(*) as total
   from datos_nalitica
   group by genero,nivel_educativo ;
   
/* 
consulta para determinar ingreso mensual por genero 
*/
select genero, sum(ingreso_bruto_mensual) as ingreso_total
from datos_nalitica 
group by genero;

/* 
consulta para determinar ingreso mensual por rango de edad 
*/

select 
case 
when edad between 18 and 25 
then "18-25"
when edad between 26 and 35 
then "26-35"
when edad between 36 and 45 
then "36-45"
else "46+"
end as rango_edad, avg(ingreso_bruto_mensual) as ingreso_promedio_edad
from datos_nalitica 
group by rango_edad;

/* 
consulta para determinar promedio de ingreso por nivel educativo  
*/
select nivel_educativo,avg(ingreso_bruto_mensual) as ingreso_promedio_nivledu
from datos_nalitica 
group by nivel_educativo;
