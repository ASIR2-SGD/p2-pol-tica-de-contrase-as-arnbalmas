# Política de contraseñas

## Contexto
Por defecto, la mayoría de sistemas operativos, vienene con una política de contraseña muy laxa, una contraseña segura presenta una barrera más al atacante, que en su intento de acceder al sistema, indudablemete dejará más rastro y en algunos casos a provocar el abandondo de ataque.

## Objetivos
* Entender el sistema de contraseñas del sistema operativo linux
  - El linux almacena sus contraseñas en los archivos passwd ,shadow ,group en ella estan encriptadas y solo peude acceder el root a ellas
   


* Entender el PAM (Plugable authentication Module)
- PAM(pwquality) es un plugin que sirve para poder poner tus propias restricciónes de contraseñas para que contenga mas seguridad, sin tener en cuenda la determinada por linux

* Instalar y configurar la libreria _pwquality_
```bash
 apt install libpam-pwquality
 vim /etc/security/pwquality.conf [si le especifica como quieres que sea la contraseña(caracteres, numeros simbolos...)]
```


* Comprobar y verificar que se ha llevado la práctica de forma correcta

|          | Score |l.min | Requisitos | Ejemplos  |
|----------|-------|------|------------|-----------|
|          |       |      |            |           |
|No valida | <40   |  -   | minlen = 6 |  vinicio  |
|          |       |      |            |           |
| Débil    | 40-50 | -6   | minlen = 6 | compra2  |
|          | 40-50 | -6   |dcredit = -1|           |
|          |       |      |            |           |
| Media    | 50-80 | -8   | minlen = 8 | Comproa2 |
|          | 50-80 | -8   |dcredit = -1|           |
|          | 50-80 | -8   |ucredit = -1|           |
|          |       |      |            |           |
| extrema  | <80   | -10  | minlen = 10|Comproba2_|
|          | <80   | -10  |dcredit = -1|           |
|          | <80   | -10  |ucredit = -1|           |
|          | <80   | -10  |ocredit = -1|           |


* Documentar la práctica.
  1. Comprobamos en el fichero /etc/pam.d/common-auth que el modulo esta activo
   
  2. Accedemos a /etc/security/pwquality.conf y en el fichero configuramos a nuestro gusto como queremos que sea la contraseña, para ello escomentamos cada una y configuramos
   
  3. Si el numero que se añade debe ser en negativo ya que el negativo indica que debe contener como minimo ese valor
   
  4. Si el valor es positivo indica que si contiene el valor en positivo se sumara el valor añadido al archivo en ese valor
   
  5. Para comprobar que esta bien configurado guardamos la configuración y ejecutamos pwscore > añadimos nuestra contraseña y comprobamos al valor de seguridad que nos muestra


