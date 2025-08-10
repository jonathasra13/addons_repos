# Imagem base oficial do Home Assistant (multi-arquitetura)
ARG BUILD_FROM=ghcr.io/home-assistant/{arch}-base:latest
FROM ${BUILD_FROM}

# Labels de identificação do add-on
LABEL \
    io.hass.name="Flask Add-on" \
    io.hass.description="Executa um servidor Flask dentro do Home Assistant" \
    io.hass.type="addon" \
    io.hass.version="1.0.0"

# Instalar Python3, pip e virtualenv
RUN apk add --no-cache python3 py3-pip

# Criar virtualenv
RUN python3 -m venv /venv

# Ativar virtualenv e instalar dependências
RUN . /venv/bin/activate && pip install --no-cache-dir Flask

# Adicionar virtualenv ao PATH
ENV PATH="/venv/bin:$PATH"

# Criar pasta da aplicação
WORKDIR /app

# Copiar código do add-on
COPY . /app

# Tornar script executável
RUN chmod a+x /app/run.sh

# Comando de inicialização
# CMD [ "/app/run.sh" ]
