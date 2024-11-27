# Use uma imagem base do Julia
FROM julia:1.11.1-bookworm

# Configurar o diretório de trabalho
WORKDIR /app

# Instalar dependências necessárias
RUN apt-get update && apt-get install -y \
    curl \
    && apt-get clean

# Instalar o Pluto.jl
RUN julia -e 'using Pkg; Pkg.add("Pluto"); Pkg.precompile()'

# Expõe a porta padrão do Pluto.jl (1234)
EXPOSE 1234

# Comando para iniciar o servidor Pluto.jl
CMD ["julia", "-e", "using Pluto; Pluto.run(host=\"0.0.0.0\", port=1234)"]
