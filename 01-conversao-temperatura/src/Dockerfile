# É uma boa prática sempre especificar a versão da imagem base no Dockerfile, caso contrário, a imagem pode ter sido atualizada e quebrar o build.
FROM node:22-alpine
WORKDIR /app

# Copiar apenas os arquivos de dependências e instalar                                                                                                                                                                      
COPY package*.json .                                                                                                                                                                                                        
RUN npm install                                                                                                                                                                                                             
                                                                                                                                                                                                                            
# Copiar o restante dos arquivos do projeto                                                                                                                                                                                 
COPY . . 

# Define a porta padrão como 8080 
ENV PORT=8080  

EXPOSE 8080

CMD ["node", "server.js"]