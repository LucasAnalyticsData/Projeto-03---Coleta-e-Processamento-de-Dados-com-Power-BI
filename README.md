Realizei a junção dos colaboradores e respectivos nomes dos gerentes.
Para isso achei mais facil utilizar a consulta SQL, alterando então a forma da importação inicial, a fim de associar quanto antes o Gerente ao funcionario.
Utilizei a seguinte consulta SQL:

SELECT
e.\*,
Case WHEN e.Super_ssn is null then 'Sem Gerente' else e2.Fname end as GerenteFName,
Case WHEN e.Super_ssn is null then null else e2.Lname end as GerenteLName
FROM dbo.employee e
LEFT JOIN dbo.employee e2 on e2.Ssn = e.Super_ssn
