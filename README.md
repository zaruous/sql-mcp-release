# sql-mcp-release

[sql-gen-mcp](https://github.com/zaruous/sql-gen-mcp)의 **배포 산출물(fat JAR) 전용 레포**입니다.
소스 코드는 이 레포에 없습니다 — 코드는 [zaruous/sql-gen-mcp](https://github.com/zaruous/sql-gen-mcp)에 있습니다.

## 다운로드

[Releases](https://github.com/zaruous/sql-mcp-release/releases)에서 받거나, 직접 내려받습니다.

```bash
curl -L -O https://github.com/zaruous/sql-mcp-release/releases/download/v1.0.0/sql-gen-mcp-1.0.0.jar
```

## 실행

JDK 21 이상이 필요합니다. 의존성이 모두 포함된 fat JAR이라 별도 설치 없이 바로 실행됩니다.

```bash
# HTTP 모드 (기본 포트 7070) — Swagger UI: http://localhost:7070/swagger
java -jar sql-gen-mcp-1.0.0.jar

# 포트 지정
java -jar sql-gen-mcp-1.0.0.jar 8080

# STDIO 모드 (Claude Desktop 연동)
java -jar sql-gen-mcp-1.0.0.jar --stdio

# STDIO 모드 + DB 접속 정보
java -jar sql-gen-mcp-1.0.0.jar --stdio \
  --db.driver=org.postgresql.Driver \
  --db.url=jdbc:postgresql://localhost:5432/mydb \
  --db.user=user \
  --db.pw=password
```

지원 DBMS: PostgreSQL, Oracle, MSSQL.
설정 항목과 MCP 도구 목록 등 자세한 내용은 [소스 레포의 README](https://github.com/zaruous/sql-gen-mcp#readme)를 참고하세요.

## llm-manager 연동

[llm_manager](https://github.com/zaruous/llm_manager)의 `SQL Gen MCP Server` 서비스팩이 이 릴리즈를 직접 내려받도록 설정되어 있습니다. 서비스 추가 후 **설치** 버튼을 누르면 JAR을 자동으로 받아옵니다.

## 릴리즈 발행

수동으로 올리지 않습니다. 소스 레포에서 `vX.Y.Z` 태그를 push하면
[`release.yml`](https://github.com/zaruous/sql-gen-mcp/blob/master/.github/workflows/release.yml) 워크플로가 fat JAR을 빌드해 이 레포의 같은 이름 릴리즈에 첨부합니다.

```bash
# sql-gen-mcp 레포에서
git tag v1.0.1 && git push origin v1.0.1
```

JAR 파일명은 `sql-gen-mcp-<version>.jar` 형식이며, 버전은 태그에서 `v`를 뗀 값입니다.
