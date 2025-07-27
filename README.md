# 🚗 Sistema de Recomendação de Veículos com KMeans

Este projeto é um sistema de recomendação que sugere veículos com base nas preferências do usuário utilizando **clusterização com KMeans**. O sistema analisa dados como preço, potência, consumo e tipo de veículo para entregar recomendações próximas do perfil desejado.

---

## 🧠 Tecnologias Utilizadas

- Python
- pandas
- scikit-learn
- numpy
- matplotlib / seaborn

---

## 📊 Funcionalidades

- Clusterização de veículos com KMeans
- Recomendação com base em:
  - Preço máximo
  - Potência mínima
  - Consumo na cidade
  - Ano mínimo
  - Preferência por SUV, sedã, câmbio automático e combustível flex
- Filtro alternativo automático caso não haja resultados no cluster
- Sugestão de veículos similares ao perfil do usuário

---

## 📝 Estrutura do Dataset

| Coluna               | Tipo       | Descrição                             |
|----------------------|------------|----------------------------------------|
| nome_veiculo         | string     | Nome e modelo do veículo               |
| preco                | numérico   | Preço FIPE                             |
| potencia_cv          | numérico   | Potência em cavalos                    |
| consumo_cidade       | numérico   | Consumo urbano (km/l)                  |
| tipo_suv             | binário    | 1 se SUV, 0 caso contrário             |
| tipo_sedan           | binário    | 1 se sedã, 0 caso contrário            |
| cambio_automatica    | binário    | 1 se automático                        |
| combustivel_flex     | binário    | 1 se for flex                          |
| ano                  | inteiro   | Ano de fabricação                      |
| Cluster              | inteiro    | Cluster atribuído pelo modelo KMeans  |

---

## ⚙️ Como Funciona

1. O usuário responde perguntas sobre suas preferências.
2. O sistema transforma essas preferências em um vetor numérico.
3. O vetor é escalonado e classificado em um dos clusters formados pelo modelo KMeans.
4. Os veículos dentro do cluster são filtrados com base nos critérios.
5. Se não houver veículos compatíveis, um **filtro flexivel** é aplicado (mais flexível).
6. Os veículos recomendados são retornados em uma lista.

---

## 🧪 Exemplo de Uso

```python
entrada_usuario = {
    'preco_maximo': 80000,
    'potencia_minima': 110,
    'consumo_minimo': 10,
    'ano_minimo': 2021,
    'prefere_suv': True,
    'prefere_sedan': False,
    'prefere_automatico': True,
    'prefere_flex': True
}

recomendados = recomendar_veiculos(entrada_usuario)
print(recomendados.head())
