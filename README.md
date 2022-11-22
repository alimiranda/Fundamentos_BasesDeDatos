# Fundamentos_BasesDeDatos
Notas del curso de fundamentos de bases de datos, algunos querys e imagenes

Pasos para instalar desde la terminal para MAC ship M1:

1. xcode-select --install

2. /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

3. brew doctor

4. brew update

5. brew install mysql

### start

6. brew services start mysql

### conect 
(mysql -h [host] -D [base de datos] -u [usuario] -p
Esto te pedirá la contraseña, para que no sea guardada en el historial, por ejemplo:

mysql -h servidor.jveweb.net -D nombre_base_de_datos -u juan -p)

7. mysql -uroot

8. show databases;

9. use platziblog;

10. show tables;

11. CREATE SCHEMA `platziblog` ;

12. CREATE TABLE `platziblog`.`etiqueta` (
  `id_etiqueta` INT NOT NULL AUTO_INCREMENT,
  `nombre_etiqueta` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`id_etiqueta`));

  13. CREATE TABLE `platziblog`.`usuarios` (
  `id_usuarios` INT NOT NULL AUTO_INCREMENT,
  `nickname` VARCHAR(40) NOT NULL,
  `email` VARCHAR(40) NOT NULL,
  `login` VARCHAR(30) NOT NULL,
  `password` VARCHAR(32) NOT NULL,
  PRIMARY KEY (`id_usuarios`),
  UNIQUE INDEX `email_UNIQUE` (`email` ASC) VISIBLE);

  14. ALTER TABLE `platziblog`.`post` 
ADD INDEX `post_usuarios_idx` (`usuario_id` ASC) VISIBLE;
;
ALTER TABLE `platziblog`.`post` 
ADD CONSTRAINT `post_usuarios`
  FOREIGN KEY (`usuario_id`)
  REFERENCES `platziblog`.`usuarios` (`id_usuarios`)
  ON DELETE NO ACTION
  ON UPDATE CASCADE;

  INSERT INTO `usuarios` (`id_usuarios`,`login`,`password`,`nickname`,`email`) VALUES (2,'monica','(*&^LKJDHC_(*#YDLKJHODG','Moni','monica@platziblog.com');