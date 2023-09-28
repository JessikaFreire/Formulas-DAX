# Hashtag Treinamentos 👩‍💻

## Fórmulas DAX


### Curso Básico de Fórmulas DAX

▶ [Arquivos](/Curso-Basico-de-Formulas-DAX)

💻 [Playlist no YouTube](https://www.youtube.com/playlist?list=PLxjKFMYkZ9OdBK4fKFBNYHRwj8o3fe_Yk) 

▶ Aula 1 | Introdução às Fórmulas DAX e Colunas Calculadas

    Colunas Calculadas
    ⚡Km = ROUND(BaseLogistica[Milhas] * 1.6, 2)
    ⚡Gasto Viagem = BaseLogistica[Combustível] + BaseLogistica[Manutenção] + BaseLogistica[Custos Fixos]
    ⚡Tempo Entrega = BaseLogistica[Data Entrega] - BaseLogistica[Data Pedido]
    ⚡Status Entrega = IF(
      BaseLogistica[Tempo Entrega] <= BaseLogistica[Prazo Entrega], 
      "No Prazo", 
      "Com Atraso"
      )

▶ Aula 2 | Criando Medidas no Power BI

    Medidas
    ⚡Estados Atendidos = DISTINCTCOUNT(BaseLogistica[UF])

    ⚡Qtd Viagens = COUNTROWS(BaseLogistica)

    ⚡Total KM = SUM(BaseLogistica[Km])
    
▶ Aula 3 | Funções Iteradora
    
    Medidas
    ⚡Gasto Médio Viagem = AVERAGEX(BaseLogistica, BaseLogistica[Combustível] + BaseLogistica[Manutenção] + BaseLogistica[Custos Fixos])

    ⚡Total Receita Bruta = SUMX(BaseLogistica, BaseLogistica[Valor do Frete Líquido] / 0.8)

    ⚡Receita Média por Viagem = AVERAGE(BaseLogistica[Valor do Frete Líquido])

    ⚡Máximo Receita Bruta = MAXX(BaseLogistica, BaseLogistica[Valor do Frete Líquido] / 0.8)

    ⚡Mínimo Receita Bruta = MINX(BaseLogistica, BaseLogistica[Valor do Frete Líquido] / 0.8)

    ⚡Total Gasto = SUMX(BaseLogistica, BaseLogistica[Combustível] + BaseLogistica[Manutenção] + BaseLogistica[Custos Fixos])

    ⚡Total KM Função = SUMX(BaseLogistica, ROUND(BaseLogistica[Milhas] * 1.6, 2))


▶ Aula 4 | Função CALCULATE
    
    Medidas
    ⚡% no Prazo = [Viagens no Prazo] / [Qtd Viagens]

    ⚡Receita RJ e SP no Prazo = CALCULATE(
      SUM(BaseLogistica[Valor do Frete Líquido]),
      BaseLogistica[UF] in {"RJ","SP"},
      BaseLogistica[Status Entrega] = "No Prazo"
      )

    ⚡Viagens no Prazo = CALCULATE([Qtd Viagens], BaseLogistica[Status Entrega] = "No Prazo")

    ⚡Viagens no Prazo Volkswagen = CALCULATE(
      [Qtd Viagens],
      BaseLogistica[Status Entrega] = "No Prazo",
      BaseLogistica[Marca] = "Volkswagen"
      )

    ⚡Viagens Volkswagen = CALCULATE(
      COUNTROWS(BaseLogistica),
      BaseLogistica[Marca] = "Volkswagen"
      )


---

### Minicurso de Fórmulas DAX

▶ [As 7 fórmulas Power BI que você tem que aprender](/Minicurso-de-Formulas-Dax/As-7-Formulas/)

💻 [Vídeo no YouTube](https://youtu.be/TjyAudH8h38)

- SUM
- AVERAGE
- MAX/MIN
- DIVIDE
- COUNT/COUNTA/COUNTROWS
- DISTINCTCOUNT
-

    Colunas Calculadas
    ⚡Faturamento na Venda = BaseVendas[Tamanho Pedido] * BaseVendas[Preco Unitario]

    ⚡Custo na Venda = BaseVendas[Tamanho Pedido] * BaseVendas[Custo Unitario]

    Medidas
    ⚡Faturamento Total = SUM(BaseVendas[Faturamento na Venda])

    ⚡Custo Total = SUM(BaseVendas[Custo na Venda])

    ⚡Faturamento Total = SUM(BaseVendas[Faturamento na Venda])

    ⚡Media de Faturamento = AVERAGE(BaseVendas[Faturamento na Venda])

    ⚡Maximo Faturado = MAX(BaseVendas[Faturamento na Venda])

    ⚡Minimo Faturado = MIN(BaseVendas[Faturamento na Venda])

    ⚡Total de Produtos Devolvidos = SUM(BaseDevolucoes[Quantidade Devolvida])

    ⚡Total de Produtos Vendidos = SUM(BaseVendas[Tamanho Pedido])

    ⚡Numero de Vendas = COUNTROWS(BaseVendas)

▶ [PROCV no Power BI](/Minicurso-de-Formulas-Dax/PROCV-no-Power-BI/)

💻 [Vídeo no YouTube](https://youtu.be/oFN7u6y2eiU)
    
    Colunas Calculadas
    ⚡Preco do Produto = LOOKUPVALUE(Produtos[Preço Unitário], Produtos[SKU],'Vendas 2016'[SKU])

    ⚡Custo do Produto = RELATED(Produtos[Custo Unitário])  

    ⚡Faturamento da Venda = 'Vendas 2016'[Tamanho Pedido] * 'Vendas 2016'[Preco do Produto]

▶ [Como Usar a Função FILTER](/Minicurso-de-Formulas-Dax/Funcao-FILTER/)

💻 [Vídeo no YouTube](https://youtu.be/XqFPb33bH-M)
    
    Colunas Calculadas
    ⚡Media Salarial = AVERAGE(CadastroFuncionarios[Salario])

    ⚡Media Salarial Absoluta = 
      CALCULATE(
      [Media Salarial],
      ALL(CadastroFuncionarios))

    ⚡Qtd Funcionarios Acima da Media = 
      CALCULATE(
      COUNT(CadastroFuncionarios[Funcionário]),
      FILTER(CadastroFuncionarios,CadastroFuncionarios[Salario]>=[Media Salarial Absoluta]))