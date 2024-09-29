# Docker - Problemas Comuns e Soluções
Este repositório tem como objetivo documentar problemas comuns enfrentados ao usar Docker e suas respectivas soluções. Aqui, você encontrará exemplos práticos, dicas, e explicações para ajudar a solucionar as dificuldades mais frequentes ao lidar com contêineres Docker.

## 1. Error: Cannot connect to the Docker daemon

### Solução:

Certifique-se de que o daemon do Docker está em execução usando:

```sh
sudo systemctl start docker
```

Ou use `docker-machine start` (para usuários do Docker Machine).

## 2. Error: Permission denied while trying to connect to the Docker daemon socket

### Solução:

Adicione seu usuário ao grupo Docker:

```sh
sudo usermod -aG docker $USER
```

Faça logout e login novamente para que as alterações tenham efeito.

## 3. Error: Container is unhealthy

### Solução:

- Verifique o comando de verificação de saúde (`HEALTHCHECK`) no seu Dockerfile.
- Revise os logs do contêiner para identificar o problema.

## 4. Error: Docker: Error response from daemon: conflict

### Solução:

Remova o contêiner existente usando:

```sh
docker rm <container_id>
```

Depois, tente executar o contêiner novamente.

## 5. Error: No space left on device

### Solução:

Limpe imagens, contêineres e volumes não utilizados:

```sh
docker system prune
```

## 6. Error: Network timed out while trying to connect to Docker Hub

### Solução:

- Verifique sua conexão com a internet e as configurações de proxy.
- Tente a operação novamente após resolver os problemas de rede.

## 7. Error: Cannot locate package in Dockerfile

### Solução:

Atualize a lista de pacotes antes de instalar software:

```dockerfile
RUN apt-get update
```

## 8. Error: EACCES: permission denied

### Solução:

- Verifique se há permissões necessárias para o volume montado.
- Use `sudo` se necessário.

## 9. Error: No such file or directory

### Solução:

Verifique o caminho do arquivo e certifique-se de que ele exista no contexto de build do Docker.

## 10. Error: Address already in use

### Solução:

- Verifique se a porta não está sendo usada por outra aplicação.
- Pare o serviço que está em conflito ou use uma porta diferente.

---
