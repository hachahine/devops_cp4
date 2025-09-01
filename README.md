# Projeto Docker Compose – CP4

## Arquitetura atual
<img width="747" height="240" alt="image" src="https://github.com/user-attachments/assets/d2ed1d13-4461-4683-b2d4-68830717735d" />

> A aplicação conecta diretamente ao banco Oracle XE rodando localmente, sem containerização.

## Arquitetura futura
<img width="901" height="313" alt="image" src="https://github.com/user-attachments/assets/33b8067f-9f14-471b-8ed1-525c9d40dee0" />

> Aplicação e banco rodam em containers separados, conectados por uma rede Docker interna (`cp4net`). Isso garante isolamento, portabilidade e persistência de dados.

---

## Instruções de Uso

1. Clone o repositório:
```bash
git clone https://github.com/hachahine/devops_cp4.git
cd devops_cp4
```

2. Rode os containers:
```bash
docker compose up --build -d
```

3. Verifique os containers:
```bash
docker ps
```

4. Acesse a aplicação:
- URL: `http://localhost:8081/api/customers`  

5. Para parar os containers:
```bash
docker compose down
```
---

## Troubleshooting Básico

- **Conflito de nomes de container:**  
```bash
Error: Conflict. The container name "/oracle-xe" is already in use
```
> Solução: remova o container antigo ou renomeie no `docker-compose.yaml`.
```bash
docker rm -f oracle-xe
```

- **Aplicação não conecta ao banco:**  
> Verifique se o serviço do banco está saudável e se a rede está correta.  
```bash
docker compose logs -f db
docker compose exec app ping db
```

- **Problemas com porta ocupada:**  
> Altere a porta mapeada no `docker-compose.yaml`.


