# FiapCap1Fase2
o MER está em .DMD pois foi feito no oracle Developer Data Modeler
já o codigo do DER vem abaixo (feito no SQLDesigner):
-- ---
-- Globals
-- ---

-- SET SQL_MODE="NO_AUTO_VALUE_ON_ZERO";
-- SET FOREIGN_KEY_CHECKS=0;

-- ---
-- Table 'Produtor'
-- 
-- ---

DROP TABLE IF EXISTS `Produtor`;
		
CREATE TABLE `Produtor` (
  `id:1` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `Nome:João Pereira` VARCHAR NULL DEFAULT NULL,
  `Local:Fazenda Estrela` VARCHAR NULL DEFAULT NULL,
  `id:1_Produtor` INT NULL DEFAULT NULL,
  PRIMARY KEY (`id:1`)
);

-- ---
-- Table 'Plantação'
-- 
-- ---

DROP TABLE IF EXISTS `Plantação`;
		
CREATE TABLE `Plantação` (
  `id:101` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `cultura:Milho` VARCHAR NULL DEFAULT NULL,
  `data:2022-03-11` DATE NULL DEFAULT NULL,
  `área:20h` DECIMAL NULL DEFAULT NULL,
  `id:101_Plantação` INT NULL DEFAULT NULL,
  PRIMARY KEY (`id:101`)
);

-- ---
-- Table 'SensorU'
-- 
-- ---

DROP TABLE IF EXISTS `SensorU`;
		
CREATE TABLE `SensorU` (
  `id:201` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `Tipo:Umidade` VARCHAR NULL DEFAULT NULL,
  `Local:Setor A` VARCHAR NULL DEFAULT NULL,
  `id:201_SensorU` INT NULL DEFAULT NULL,
  PRIMARY KEY (`id:201`)
);

-- ---
-- Table 'SensorPH'
-- 
-- ---

DROP TABLE IF EXISTS `SensorPH`;
		
CREATE TABLE `SensorPH` (
  `id:202` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `Tipo:ph` VARCHAR NULL DEFAULT NULL,
  `Local:Setor A` VARCHAR NULL DEFAULT NULL,
  `id:202_SensorPH` INT NULL DEFAULT NULL,
  PRIMARY KEY (`id:202`)
);

-- ---
-- Table 'SensorN'
-- 
-- ---

DROP TABLE IF EXISTS `SensorN`;
		
CREATE TABLE `SensorN` (
  `id:203` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `Tipo:nutrientes` VARCHAR NULL DEFAULT NULL,
  `Local:Setor B` VARCHAR NULL DEFAULT NULL,
  `id:203_SensorN` INT NULL DEFAULT NULL,
  PRIMARY KEY (`id:203`)
);

-- ---
-- Table 'Leitura Umidade'
-- 
-- ---

DROP TABLE IF EXISTS `Leitura Umidade`;
		
CREATE TABLE `Leitura Umidade` (
  `id:301` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `DataHora:2022-03-16 08:00` DATETIME NULL DEFAULT NULL,
  `Valor:45%` DECIMAL NULL DEFAULT NULL,
  PRIMARY KEY (`id:301`)
);

-- ---
-- Table 'Leitura PH'
-- 
-- ---

DROP TABLE IF EXISTS `Leitura PH`;
		
CREATE TABLE `Leitura PH` (
  `id:302` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `DataHora: 2022-03-16 08:00` DATETIME NULL DEFAULT NULL,
  `Valor:6.5 ` DECIMAL NULL DEFAULT NULL,
  PRIMARY KEY (`id:302`)
);

-- ---
-- Table 'Leitura Nutrientes'
-- 
-- ---

DROP TABLE IF EXISTS `Leitura Nutrientes`;
		
CREATE TABLE `Leitura Nutrientes` (
  `id:303` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `DataHora: 2022-03-16 08:00` DATETIME NULL DEFAULT NULL,
  `Valor_p: 15 mg/kg` DECIMAL NULL DEFAULT NULL,
  `Valor_k: 20 mg/kg` DECIMAL NULL DEFAULT NULL,
  PRIMARY KEY (`id:303`)
);

-- ---
-- Table 'Ajuste Aplicação'
-- 
-- ---

DROP TABLE IF EXISTS `Ajuste Aplicação`;
		
CREATE TABLE `Ajuste Aplicação` (
  `id:401` INT NULL AUTO_INCREMENT DEFAULT NULL,
  `DataHora 2022-03-16 09:00` DATETIME NULL DEFAULT NULL,
  `Tipo:irrigação` VARCHAR NULL DEFAULT NULL,
  `quantidade: 2000 litros de água` DECIMAL NULL DEFAULT NULL,
  PRIMARY KEY (`id:401`)
);

-- ---
-- Foreign Keys 
-- ---

ALTER TABLE `Produtor` ADD FOREIGN KEY (id:1_Produtor) REFERENCES `Produtor` (`id:1`);
ALTER TABLE `Produtor` ADD FOREIGN KEY (id:1_Produtor) REFERENCES `Plantação` (`id:101`);
ALTER TABLE `Plantação` ADD FOREIGN KEY (id:101) REFERENCES `SensorU` (`id:201`);
ALTER TABLE `Plantação` ADD FOREIGN KEY (id:101) REFERENCES `SensorPH` (`id:202`);
ALTER TABLE `Plantação` ADD FOREIGN KEY (id:101) REFERENCES `SensorN` (`id:203`);
ALTER TABLE `Plantação` ADD FOREIGN KEY (id:101) REFERENCES `Ajuste Aplicação` (`id:401`);
ALTER TABLE `Plantação` ADD FOREIGN KEY (id:101_Plantação) REFERENCES `Plantação` (`id:101`);
ALTER TABLE `SensorU` ADD FOREIGN KEY (id:201) REFERENCES `Leitura Umidade` (`id:301`);
ALTER TABLE `SensorU` ADD FOREIGN KEY (id:201_SensorU) REFERENCES `SensorU` (`id:201`);
ALTER TABLE `SensorPH` ADD FOREIGN KEY (id:202) REFERENCES `Leitura PH` (`id:302`);
ALTER TABLE `SensorPH` ADD FOREIGN KEY (id:202_SensorPH) REFERENCES `SensorPH` (`id:202`);
ALTER TABLE `SensorN` ADD FOREIGN KEY (id:203) REFERENCES `Leitura Nutrientes` (`id:303`);
ALTER TABLE `SensorN` ADD FOREIGN KEY (id:203_SensorN) REFERENCES `SensorN` (`id:203`);

-- ---
-- Table Properties
-- ---

-- ALTER TABLE `Produtor` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `Plantação` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `SensorU` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `SensorPH` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `SensorN` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `Leitura Umidade` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `Leitura PH` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `Leitura Nutrientes` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `Ajuste Aplicação` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

-- ---
-- Test Data
-- ---

-- INSERT INTO `Produtor` (`id:1`,`Nome:João Pereira`,`Local:Fazenda Estrela`,`id:1_Produtor`) VALUES
-- ('','','','');
-- INSERT INTO `Plantação` (`id:101`,`cultura:Milho`,`data:2022-03-11`,`área:20h`,`id:101_Plantação`) VALUES
-- ('','','','','');
-- INSERT INTO `SensorU` (`id:201`,`Tipo:Umidade`,`Local:Setor A`,`id:201_SensorU`) VALUES
-- ('','','','');
-- INSERT INTO `SensorPH` (`id:202`,`Tipo:ph`,`Local:Setor A`,`id:202_SensorPH`) VALUES
-- ('','','','');
-- INSERT INTO `SensorN` (`id:203`,`Tipo:nutrientes`,`Local:Setor B`,`id:203_SensorN`) VALUES
-- ('','','','');
-- INSERT INTO `Leitura Umidade` (`id:301`,`DataHora:2022-03-16 08:00`,`Valor:45%`) VALUES
-- ('','','');
-- INSERT INTO `Leitura PH` (`id:302`,`DataHora: 2022-03-16 08:00`,`Valor:6.5 `) VALUES
-- ('','','');
-- INSERT INTO `Leitura Nutrientes` (`id:303`,`DataHora: 2022-03-16 08:00`,`Valor_p: 15 mg/kg`,`Valor_k: 20 mg/kg`) VALUES
-- ('','','','');
-- INSERT INTO `Ajuste Aplicação` (`id:401`,`DataHora 2022-03-16 09:00`,`Tipo:irrigação`,`quantidade: 2000 litros de água`) VALUES
-- ('','','','');
