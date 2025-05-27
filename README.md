CODE DO SQL (Correto)



CREATE DATABASE clinica veterinária
USE clinica veterinária



CREATE TABLE Veterinario (
    CRV CHAR(6) PRIMARY KEY,
    Nome VARCHAR(100) NOT NULL,
    Endereco VARCHAR(200) NOT NULL,
    Celular VARCHAR(9),
    CPF CHAR(11) NOT NULL
);





CREATE TABLE Cliente (
    CPF CHAR(11) PRIMARY KEY,
    Nome VARCHAR(30) NOT NULL,
    Endereco VARCHAR(200) NOT NULL,
    Telefone VARCHAR(15) NOT NULL,
    Celular VARCHAR(10) NOT NULL
);




CREATE TABLE Animal (
    ID_Animal INT PRIMARY KEY,
    Nome VARCHAR(50),
    Tipo VARCHAR(50) NOT NULL,
    Raca VARCHAR(50),
    Idade INT,
    Alergico BOOLEAN NOT NULL,
    CPF_Cliente CHAR(11) NOT NULL,
    Peso DECIMAL(6,2) NOT NULL,
    Altura DECIMAL(4,2) NOT NULL,
    FOREIGN KEY (CPF_Cliente) REFERENCES Cliente(CPF)
);




CREATE TABLE Alimentacao (
    ID_Animal INT PRIMARY KEY,
    Herbivoro BOOLEAN NOT NULL,
    Carnivoro BOOLEAN NOT NULL,
    Onivoro BOOLEAN NOT NULL,
    FOREIGN KEY (ID_Animal) REFERENCES Animal(ID_Animal)
);




CREATE TABLE Consulta (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    DataHora DATETIME NOT NULL,
    Valor DECIMAL(8,2) NOT NULL,
    Diagnostico VARCHAR(100) NOT NULL,
    ID_Animal INT NOT NULL,
    CRV_Veterinario CHAR(11) NOT NULL,
    FOREIGN KEY (ID_Animal) REFERENCES Animal(ID_Animal),
    FOREIGN KEY (CRV_Veterinario) REFERENCES Veterinario(CRV)
);


INSERT INTO Cliente (CPF, Nome, Telefone, Endereco) VALUES
('11111111111', 'Ana Souza', '11999999991', 'Rua A, 123'),
('22222222222', 'Bruno Lima', '11999999992', 'Rua B, 456'),
('33333333333', 'Carla Mendes', '11999999993', 'Rua C, 789'),
('44444444444', 'Diego Santos', '11999999994', 'Rua D, 321'),
('55555555555', 'Elaine Silva', '11999999995', 'Rua E, 654'),
('66666666666', 'Fabio Ramos', '11999999996', 'Rua F, 987'),
('77777777777', 'Gabriela Rocha', '11999999997', 'Rua G, 147'),
('88888888888', 'Henrique Costa', '11999999998', 'Rua H, 258'),
('99999999999', 'Isabela Teixeira', '11999999999', 'Rua I, 369'),
('10101010101', 'João Pereira', '11999999910', 'Rua J, 159');

INSERT INTO Animal (ID_Animal, Nome, Tipo, Raca, Idade, Alergico, CPF_Cliente) VALUES
(1, 'Rex', 'Cachorro', 'Labrador', 5, 0, '11111111111'),
(2, 'Mia', 'Gato', 'Siamês', 3, 1, '22222222222'),
(3, 'Bob', 'Cachorro', 'Poodle', 7, 0, '33333333333'),
(4, 'Luna', 'Gato', 'Persa', 2, 0, '44444444444'),
(5, 'Thor', 'Cachorro', 'Pitbull', 4, 1, '55555555555'),
(6, 'Mel', 'Cachorro', 'Beagle', 6, 0, '66666666666'),
(7, 'Nina', 'Gato', 'Maine Coon', 5, 0, '77777777777'),
(8, 'Zeus', 'Cachorro', 'Pastor Alemão', 3, 1, '88888888888'),
(9, 'Bidu', 'Cachorro', 'Bulldog', 8, 0, '99999999999'),
(10, 'Pingo', 'Gato', 'Angorá', 1, 0, '10101010101');


INSERT INTO alimentacao (ID_Animal, Herbivoro, Carnivoro, Onivoro, Peso, Altura) VALUES
(1, 0, 1, 0, 25.50, 0.60),
(2, 0, 1, 0, 4.20, 0.25),
(3, 1, 0, 0, 1.80, 0.20),
(4, 0, 1, 0, 32.00, 0.65),
(5, 0, 1, 0, 3.80, 0.23),
(6, 1, 0, 0, 0.15, 0.05),
(7, 0, 1, 0, 0.05, 0.03),
(8, 1, 0, 0, 0.30, 0.15),
(9, 0, 0, 1, 6.50, 0.35),
(10, 0, 1, 0, 4.50, 0.24);

INSERT INTO veterinario (CRV, Nome, Endereco, Celular, CPF) VALUES
('123456', 'Dr. Roberto Almeida', 'Rua dos Médicos, 100', '912345678', '98765432109'),
('234567', 'Dra. Sandra Nunes', 'Av. Veterinária, 200', '923456789', '87654321098'),
('345678', 'Dr. Marcelo Costa', 'Rua dos Animais, 300', '934567890', '76543210987'),
('456789', 'Dra. Patricia Souza', 'Alameda Pet, 400', '945678901', '65432109876'),
('567890', 'Dr. Ricardo Santos', 'Av. Clínica, 500', '956789012', '54321098765'),
('678901', 'Dra. Camila Oliveira', 'Rua da Saúde, 600', '967890123', '43210987654'),
('789012', 'Dr. Eduardo Pereira', 'Alameda dos Bichos, 700', '978901234', '32109876543'),
('890123', 'Dra. Luciana Fernandes', 'Av. dos Pets, 800', '989012345', '21098765432'),
('901234', 'Dr. Gustavo Martins', 'Rua Animal, 900', '990123456', '10987654321'),
('012345', 'Dra. Beatriz Rocha', 'Alameda Vet, 1000', '901234567', '09876543210');

INSERT INTO consulta (ID, DataHora, Valor, Diagnostico, ID_Animal, CRV_Veterinario) VALUES
(1, '2023-01-10 09:00:00', 150.00, 'Check-up anual', 1, '123456'),
(2, '2023-01-12 10:30:00', 200.00, 'Vacinação', 2, '234567'),
(3, '2023-01-15 14:00:00', 180.00, 'Problema digestivo', 3, '345678'),
(4, '2023-01-18 11:00:00', 250.00, 'Ferimento na pata', 4, '456789'),
(5, '2023-01-20 15:30:00', 120.00, 'Check-up anual', 5, '567890'),
(6, '2023-01-22 08:45:00', 90.00, 'Consulta de rotina', 6, '678901'),
(7, '2023-01-25 16:00:00', 300.00, 'Cirurgia de remoção de tumor', 7, '789012'),
(8, '2023-01-28 13:15:00', 130.00, 'Problema respiratório', 8, '890123'),
(9, '2023-02-01 10:00:00', 170.00, 'Alergia alimentar', 9, '901234'),
(10, '2023-02-05 09:30:00', 160.00, 'Check-up anual', 10, '012345');




