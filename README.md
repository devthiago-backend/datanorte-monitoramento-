
Algoritmo "DataNorte_Monitoramento"
Var
   idServidor, idPiorServidor: caractere
   qtdAmostras, qtdServidores, i: inteiro
   tempo, soma, media, maiorMedia: real
   resposta: caractere
   primeiro: logico

Inicio
   maiorMedia <- -1
   qtdServidores <- 0
   primeiro <- verdadeiro
   idPiorServidor <- ""

   Escreva("Deseja informar um servidor? S/N: ")
   Leia(resposta)

   Enquanto (resposta = "S") ou (resposta = "s") faca
      qtdServidores <- qtdServidores + 1

      Escreva("Informe o identificador do servidor ", qtdServidores, ": ")
      Leia(idServidor)

      Escreva("Quantas amostras foram coletadas para ", idServidor, "? ")
      Leia(qtdAmostras)

      soma <- 0
      Para i de 1 ate qtdAmostras faca
         Escreva("Tempo da amostra ", i, " em ms: ")
         Leia(tempo)
         soma <- soma + tempo
      FimPara

      Se qtdAmostras > 0 entao
         media <- soma / qtdAmostras
      Senao
         media <- 0
      FimSe

      Escreval("")
      Escreval("Servidor: ", idServidor, " | Amostras: ", qtdAmostras, " | Tempo Medio: ", media:0:2, " ms")
      Escreval("-------------------------------------------")

      // Verifica pior desempenho
      Se primeiro = verdadeiro entao
         maiorMedia <- media
         idPiorServidor <- idServidor
         primeiro <- falso
      Senao
         Se media > maiorMedia entao
            maiorMedia <- media
            idPiorServidor <- idServidor
         FimSe
      FimSe

      Escreva("Deseja informar outro servidor? S/N: ")
      Leia(resposta)
   FimEnquanto

   Se qtdServidores > 0 entao
      Escreval("")
      Escreval("RESULTADO FINAL:")
      Escreval("Servidor com pior desempenho: ", idPiorServidor)
      Escreval("Maior tempo medio: ", maiorMedia:0:2, " ms")
   Senao
      Escreval("Nenhum servidor informado.")
   FimSe

Fimalgoritmo