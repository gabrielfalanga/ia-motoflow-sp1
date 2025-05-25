# 🏍️ Machine Learning Motoflow – Classificação de Motos

## 🚀 Descrição do Projeto

Este projeto utiliza **Transfer Learning com MobileNetV2** para classificar imagens de motos em 3 categorias da empresa Mottu:

- `mottu-e`
- `mottu-pop`
- `mottu-sport`

O modelo é treinado com um conjunto reduzido de imagens e exportado para o formato `.tflite`, pronto para uso em aplicativos mobile.

## 🛠️ Tecnologias Utilizadas no Modelo de Classificação de Imagens

### 🧠 1. TensorFlow & Keras
- **Framework principal de Deep Learning.**
- Permite criar, treinar, salvar e exportar modelos.
- Keras é a API de alto nível do TensorFlow.

**Usado para:**
- Construção do modelo (`Sequential`, `Functional API`)
- Camadas: `Dense`, `Dropout`, `GlobalAveragePooling2D`
- Ativações: `relu`, `softmax`
- Callbacks: `EarlyStopping`, `ReduceLROnPlateau`
- Exportação para `.keras` e `.tflite`

### 🏗️ 2. MobileNetV2 (Transfer Learning)
- Arquitetura de CNN leve e eficiente, **pré-treinada no ImageNet**.
- Reutilizada como base (`include_top=False`) para acelerar e melhorar o aprendizado.

**Usado para:**
- Base do classificador de imagens (sem treinar do zero)
- Excelente para aplicações mobile e embedded

### 🖼️ 3. ImageDataGenerator (Keras)
- Ferramenta para **carregamento e pré-processamento de imagens** diretamente de pastas.

**Usado para:**
- Carregar imagens automaticamente em batches
- Realizar **data augmentation** (flip, zoom, shear, etc.)
- Separar treino e validação com `validation_split`

### 💾 4. TensorFlow Lite
- Versão compacta do modelo para dispositivos móveis.

**Usado para:**
- Converter o modelo `.keras` para `.tflite` com `TFLiteConverter`
- Tornar o modelo compatível com apps Android/iOS

### ⚙️ Outras práticas aplicadas

| Recurso                        | Propósito                                           |
|-------------------------------|-----------------------------------------------------|
| `Dropout`                     | Evitar overfitting                                 |
| `EarlyStopping`               | Parar o treinamento quando a `val_loss` não melhora |
| `ReduceLROnPlateau`           | Ajustar a taxa de aprendizado automaticamente       |
| `rescale=1./255`              | Normalização dos pixels para facilitar o aprendizado |

---

## 📁 Estrutura de Dados

As imagens estão organizadas em diretórios separados por classe. A divisão dos dados segue:

```
data/
├── mottu-e/
├── mottu-pop/
└── mottu-sport/
```

## ⚙️ Instruções de Uso

1. **Clone o repositório** (caso aplicável):

```bash
git clone https://github.com/seu-usuario/motoflow-classificacao.git
cd motoflow-classificacao
```

2. **Acesse o notebook:**
   - Abra o arquivo `Challenge_IA_2025.ipynb` no [Google Colab](https://colab.research.google.com/) ou no seu ambiente Jupyter local.

3. **Execute o notebook por completo:**
   - O notebook fará:
     - Carregamento e pré-processamento das imagens
     - Criação e treinamento do modelo com MobileNetV2
     - Avaliação do desempenho
     - Exportação para `.tflite`

4. **Exportação final:**
   - O modelo treinado será salvo como:
     ```
     modelo_motoflow.tflite
     ```

## 📊 Resultados Parciais

- **Acurácia:** ~93% no fim do treinamento
- **Loss de validação:** Estável e em queda progressiva, indicando boa generalização
- **Testes com imagens desconhecidas:** O modelo acertou as 3 classes oferecidas para o predict

