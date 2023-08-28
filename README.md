# Projeto Full-Stack: Página de CRUD com ReactJS, NodeJS e MySQL

## Introdução

Bem-vindo(a) ao repositório **Projeto Full-Stack React Node MySQL**, um espaço onde a colaboração e a tecnologia se fundem para criar uma aplicação full-stack incrível. Se você está entusiasmado(a) com o desenvolvimento completo de uma aplicação web usando as mais recentes tecnologias, você está prestes a mergulhar em uma jornada emocionante!

## Sobre o Projeto

Neste repositório, reunimos nossos esforços para desenvolver uma aplicação full-stack impressionante com ReactJS, NodeJS e MySQL. Trabalhando em equipe com os talentosos colegas Giselly Rocha e João Miraya da Newstech, criamos uma aplicação que não apenas utiliza componentes e APIs, mas também integra um banco de dados para operações de CRUD.

### O Objetivo

Nosso objetivo com este projeto foi colocar em prática os conceitos que adquirimos em relação ao ReactJS e NodeJS. Exploramos as complexidades das rotas, tanto no backend quanto no frontend, e exploramos a integração de um banco de dados MySQL para armazenar e gerenciar os dados.

## Funcionalidades Principais

- Página de CRUD completa com ReactJS.
- Backend robusto com NodeJS para gerenciamento de rotas.
- Conexão e operações de CRUD com o banco de dados MySQL.

## Configurações do Projeto

- Utilizamos o pacote yarn com o Vite- react
  
  ```yarn create vite ```
  
- Usamos um formulario com os dados recebidos do cliente para ser consultado e formatado.

  ```
  const Form = ({ getUsers, onEdit, setOnEdit }) => {
    const ref = useRef();
  
    useEffect(() => {
      if (onEdit) {
        const user = ref.current;
  
        user.nome.value = onEdit.nome;
        user.email.value = onEdit.email;
        user.tel.value = onEdit.tel;
        user.dataNasc.value = onEdit.dataNasc;
      }
    }, [onEdit]);```
  
- Usamos o MySQL para armazenar os dados em um banco
  
  ```import mysql from "mysql"```
  
  ```
  export const db =mysql.createConnection({
    host: "localhost",
    user: "root",
    password: "",
    database: "crudreact"
   })
  ```
## Operação de CRUD

- Importando o banco de dados.
  
  ```import {db}from "../db.js";```
  
  - Criando os dados (Create)
    ```
    export const addUser = (req, res) => {

    const q =

    "INSERT INTO usuarios(`nome` , `email` , `tel` , `dataNasc` ) VALUES(?)";

    const values = [
        req.body.nome,
        req.body.email,
        req.body.tel,
        req.body.dataNasc,
    ];

    db.query(q,[values], (err) => {
        if (err) return res.json(err);

        return res.status(200).json("Usuario criado com sucesso. ");

    });};
    ```

  - Consultando os dados (Read).
    ```
    export const getUsers= (_, res) =>{
    const q = "SELECT * FROM usuarios";

    db.query(q, (err, data) => {
        if (err) return res.json(err);

        return res.status(200).json(data);
    });
    };

  - Atualizando os dados (Update)
    ```
    export const updateUser = (req, res) => {

    const q = 
    "UPDATE usuarios SET `nome` = ?, `email` = ?, `tel` = ?, `dataNasc` = ? WHERE `id` = ?";
    const values = [
        req.body.nome,
        req.body.email,
        req.body.tel,
        req.body.dataNasc,
    ];

    db.query(q, [...values, req.params.id], (err) => {
        if (err) return res.json(err);

        return res.status(200).json("Usuario atualizado com sucesso. ");
    })};

  - Deletando os dados (Delete)
    ```
    export const deleteUser = (req, res) => {
    const q = "DELETE FROM usuarios WHERE `id` = ?";
  
    db.query(q, [req.params.id], (err) => {
      if (err) return res.json(err);
  
      return res.status(200).json("Usuário deletado com sucesso.");
    });};

## Aprendizados

Durante a realização deste projeto, expandimos nossos conhecimentos em várias áreas-chave:

- Integração entre frontend e backend usando APIs.
- Gerenciamento de rotas no NodeJS.
- Manipulação de dados em um banco de dados MySQL.

## Próximos Passos

Este projeto marca um ponto de partida, e estamos ansiosos para continuar a aprimorar nossas habilidades. Pretendemos aprofundar nosso conhecimento em segurança, otimização de desempenho e design de interface.

## Como Usar Este Repositório

Sinta-se à vontade para explorar os arquivos e pastas deste repositório para entender como criamos essa aplicação full-stack. Você pode examinar o código, descobrir como integramos o ReactJS e o NodeJS e até mesmo testar a aplicação por conta própria.

## Video do Projeto

[Assista ao vídeo do projeto](https://youtu.be/Htvfm2-TVWk)

## Contato

Gostaria de se conectar, compartilhar insights ou discutir estratégias de desenvolvimento? Vamos trocar ideias [aqui](https://www.linkedin.com/in/robson-ferreira-508247134/)!

Esperamos que este repositório inspire você a mergulhar fundo no desenvolvimento full-stack e a criar projetos impactantes com tecnologias modernas. Vamos construir um futuro digital incrível juntos!
