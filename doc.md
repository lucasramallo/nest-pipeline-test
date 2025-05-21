## Medidas para acelerar execução

#### Cache

```yml
    - name: Cache NVD Database
    uses: actions/cache@v4
    with:
        path: dependency-check/data
        key: nvd-database-${{ runner.os }}-${{ hashFiles('dependency-check/data/**') }}
        restore-keys: |
        nvd-database-${{ runner.os }}-
```

Cache do Banco NVD: Utiliza a ação actions/cache para armazenar o banco de vulnerabilidades, reduzindo o tempo de atualização em execuções futuras.

#### API Key

```shell
    [WARN] An NVD API Key was not provided - it is highly recommended to use an NVD API key as the update can take a VERY long time without an API Key
```

O aviso que você mencionou indica que o OWASP Dependency-Check está sendo executado sem uma chave de API do NVD (National Vulnerability Database), o que pode tornar a atualização do banco de vulnerabilidades muito lenta devido às restrições de taxa de requisições da API pública do NVD. Para resolver isso, você pode configurar uma chave de API do NVD no pipeline do GitHub Actions para acelerar o processo de atualização.

## Dependency-check-action

Para evitar o download manual do Dependency-Check e a atualização do NVD é usar uma ação pré-existente do GitHub Marketplace, como a ação dependency-check/dependency-check-action

#### Com dependencia multer 1.4.4-lts.1 que foi reportada em 19 de maio de 2025

```shell
pnpm install multer@2.0.0
```

![alt text](image.png)

Identificado!

#### Com dependencia Tough-Cookie 4.1.3 a vulnerabilidade CVE-2025-49237 foi reportada em 13 de maio de 2025
