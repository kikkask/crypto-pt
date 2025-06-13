# Crypto-PT

[![PyPI version](https://badge.fury.io/py/crypto-pt.svg)](https://badge.fury.io/py/crypto-pt)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Uma biblioteca Python didática para explorar a criptografia RSA em português.

---

## Sobre o Projeto

O `crypto-pt` nasceu como um projeto de Atividades Práticas Supervisionadas (APS) com o objetivo de desmistificar o funcionamento do algoritmo RSA. É uma ferramenta desenvolvida com foco didático, ideal para estudantes, entusiastas de criptografia e desenvolvedores que desejam entender os conceitos fundamentais da criptografia de chave pública de forma prática e em português.

O código foi mantido intencionalmente simples e claro para facilitar o estudo e a compreensão do fluxo de geração de chaves, criptografia e descriptografia.

## Principais Funcionalidades

* 🔑 **Geração de Chaves RSA:** Crie pares de chaves (pública e privada) com tamanho de bits personalizável.
* 🔒 **Criptografia de Strings:** Criptografe qualquer mensagem de texto de forma simples.
* 🔓 **Descriptografia de Mensagens:** Desvende mensagens criptografadas com a chave privada correspondente.

## Instalação

Para instalar o `crypto-pt`, basta usar o `pip`:

```bash
pip install crypto-pt
```

## Guia de Uso Rápido
O processo para usar a biblioteca é dividido em quatro passos simples:

Definir Parâmetros: Escolha a mensagem a ser criptografada e o tamanho em bits para as chaves.

Gerar Chaves: Crie o par de chaves pública e privada.

Criptografar: Use a chave pública para cifrar a mensagem.

Descriptografar: Use a chave privada para decifrar a mensagem e recuperar o texto original.

Veja o exemplo em ação:

```Python
import crypto_pt

# 1. Defina a mensagem e o tamanho dos bits para as chaves
mensagem_original = "Minha mensagem secreta em português!"
# Para testes rápidos, 512 bits é suficiente. 
# Para maior segurança, use 1024 ou 2048.
bits_chave = 512  

print(f"Mensagem Original: '{mensagem_original}'")
print("-" * 30)

try:
    # 2. Gere as chaves pública e privada
    print("Gerando chaves...")
    chave_publica, chave_privada = crypto_pt.gerar_chaves_grandes(bits=bits_chave)
    print(f"Chave Pública (e, n): {chave_publica}")
    print(f"Chave Privada (d, n): {chave_privada}\n")

    # 3. Criptografe a mensagem com a chave pública
    print("Criptografando mensagem...")
    mensagem_criptografada = crypto_pt.criptografar(mensagem_original, chave_publica)
    print(f"Mensagem Criptografada (lista de inteiros): {mensagem_criptografada}\n")

    # 4. Descriptografe a mensagem com a chave privada
    print("Descriptografando mensagem...")
    mensagem_descriptografada = crypto_pt.descriptografar(mensagem_criptografada, chave_privada)
    print(f"Mensagem Descriptografada: '{mensagem_descriptografada}'")
    print("-" * 30)

    # Verificação final
    assert mensagem_original == mensagem_descriptografada
    print("✅ Sucesso! A mensagem original foi recuperada.")

except ValueError as e:
    print(f"❌ Erro de Valor: {e}")
except Exception as e:
    print(f"❌ Ocorreu um erro inesperado: {e}")
```

## Aviso Importante de Segurança:
⚠️ Atenção: Esta implementação do RSA é destinada exclusivamente a fins educacionais. Ela serve como uma ferramenta de aprendizado e pode não ser segura para uso em ambientes de produção. A biblioteca não implementa esquemas de preenchimento (padding schemes) cruciais para a segurança, como o OAEP.

Para aplicações de segurança críticas, utilize bibliotecas de criptografia robustas, auditadas e mantidas pela comunidade, como a Cryptography.

## Licença
Este projeto é distribuído sob a Licença MIT. Veja o arquivo LICENSE para mais detalhes.
