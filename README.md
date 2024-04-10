#include <stdio.h> 
#include <stdlib.h> 
#include <string.h>

#define MAX_CONTATOS 100

typedef struct { 
    char nome[50]; 
    char telefone[15]; 
    char email[50]; 
    char descricao[100]; 
} Contato;

// Função para salvar contatos em um arquivo
void salvarContatos(Contato contatos[], int numContatos, const char *nomeArquivo) { 
    FILE *arquivo = fopen(nomeArquivo, "w");  // Abre o arquivo para escrita
    if (arquivo == NULL) {  // Verifica se o arquivo foi aberto corretamente
        printf("Erro ao abrir o arquivo.\n"); 
        exit(1);  // Encerra o programa em caso de erro
    }

    // Escreve os contatos no arquivo
    for (int i = 0; i < numContatos; i++) { 
        fprintf(arquivo,"Nome: %s\nTelefone: %s\nEmail: %s\nDescrição: %s\n--------------\n", contatos[i].nome, contatos[i].telefone, contatos[i].email,contatos[i].descricao); 
    }

    fclose(arquivo);  // Fecha o arquivo
}

// Função para carregar contatos de um arquivo
void carregarContatos(Contato contatos[], int *numContatos, const char *nomeArquivo) { 
    FILE *arquivo = fopen(nomeArquivo, "r");  // Abre o arquivo para leitura
    if (arquivo == NULL) {  // Verifica se o arquivo foi aberto corretamente
        printf("Erro ao abrir o arquivo.\n"); 
        exit(1);  // Encerra o programa em caso de erro
    }

    *numContatos = 0;  // Zera o contador de contatos

    // Lê os contatos do arquivo
    while (fscanf(arquivo, "%[^;];%[^;];%[^;];%[^\n]\n", contatos[*numContatos].nome, contatos[*numContatos].telefone, contatos[*numContatos].email, contatos[*numContatos].descricao) != EOF) { 
        (*numContatos)++; 
    }

    fclose(arquivo);  // Fecha o arquivo
}

// Função principal
int main() { 
    Contato contatos[MAX_CONTATOS]; 
    char nomeArquivo[50]; 
    int opcao, numContatos = 0;

    // Loop principal do programa
    while (1) { 
        printf("\nSelecione uma opção:\n"); 
        printf("1 - Adicionar contato\n"); 
        printf("2 - Listar contatos\n"); 
        printf("3 - Salvar contatos em um arquivo\n"); 
        printf("4 - Carregar contatos de um arquivo\n"); 
        printf("5 - Sair\n"); 
        scanf("%d", &opcao);  // Lê a opção escolhida pelo usuário

        switch (opcao) { 
            case 1:
                // Adicionar contato
                if (numContatos >= MAX_CONTATOS) { 
                    printf("Limite máximo de contatos atingido.\n"); 
                    break; 
                }

                printf("\nDigite o nome: "); 
                scanf(" %[^\n]s", contatos[numContatos].nome);

                printf("Digite o telefone: "); 
                scanf(" %[^\n]s", contatos[numContatos].telefone);

                printf("Digite o email: "); 
                scanf(" %[^\n]s", contatos[numContatos].email);

                printf("Digite a descrição: "); 
                scanf(" %[^\n]s", contatos[numContatos].descricao);

                numContatos++; 
                break;

#include <stdio.h> 
#include <stdlib.h> 
#include <string.h>

#define max_contatos 100

typedef struct { 
    char nome[50]; 
    char telefone[15]; 
    char email[50]; 
    char descricao[100]; 
} contato;

// função para salvar contatos em um arquivo
void salvarcontatos(contato contatos[], int numcontatos, const char *nomearquivo) { 
    file *arquivo = fopen(nomearquivo, "w");  // abre o arquivo para escrita
    if (arquivo == null) {  // verifica se o arquivo foi aberto corretamente
        printf("erro ao abrir o arquivo.\n"); 
        exit(1);  // encerra o programa em caso de erro
    }

    // escreve os contatos no arquivo
    for (int i = 0; i < numcontatos; i++) { 
        fprintf(arquivo,"nome: %s\ntelefone: %s\nemail: %s\ndescrição: %s\n--------------\n", contatos[i].nome, contatos[i].telefone, contatos[i].email,contatos[i].descricao); 
    }

    fclose(arquivo);  // fecha o arquivo
}

// função para carregar contatos de um arquivo
void carregarcontatos(contato contatos[], int *numcontatos, const char *nomearquivo) { 
    file *arquivo = fopen(nomearquivo, "r");  // abre o arquivo para leitura
    if (arquivo == null) {  // verifica se o arquivo foi aberto corretamente
        printf("erro ao abrir o arquivo.\n"); 
        exit(1);  // encerra o programa em caso de erro
    }

    *numcontatos = 0;  // zera o contador de contatos

    // lê os contatos do arquivo
    while (fscanf(arquivo, "%[^;];%[^;];%[^;];%[^\n]\n", contatos[*numcontatos].nome, contatos[*numcontatos].telefone, contatos[*numcontatos].email, contatos[*numcontatos].descricao) != eof) { 
        (*numcontatos)++; 
    }

    fclose(arquivo);  // fecha o arquivo
}

// função principal
int main() { 
    contato contatos[max_contatos]; 
    char nomearquivo[50]; 
    int opcao, numcontatos = 0;

    // loop principal do programa
    while (1) { 
        printf("\nselecione uma opção:\n"); 
        printf("1 - adicionar contato\n"); 
        printf("2 - listar contatos\n"); 
        printf("3 - salvar contatos em um arquivo\n"); 
        printf("4 - carregar contatos de um arquivo\n"); 
        printf("5 - sair\n"); 
        scanf("%d", &opcao);  // lê a opção escolhida pelo usuário

        switch (opcao) { 
            case 1:
                // adicionar contato
                if (numcontatos >= max_contatos) { 
                    printf("limite máximo de contatos atingido.\n"); 
                    break; 
                }

                printf("\ndigite o nome: "); 
                scanf(" %[^\n]s", contatos[numcontatos].nome);

                printf("digite o telefone: "); 
                scanf(" %[^\n]s", contatos[numcontatos].telefone);

                printf("digite o email: "); 
                scanf(" %[^\n]s", contatos[numcontatos].email);

                printf("digite a descrição: "); 
                scanf(" %[^\n]s", contatos[numcontatos].descricao);

                numcontatos++; 
                break;

            case 2:
                // listar contatos
                for (int i = 0; i < numcontatos; i++) { 
                    printf("\nnome: %s\n", contatos[i].nome); 
                    printf("telefone: %s\n", contatos[i].telefone); 
                    printf("email: %s\n", contatos[i].email); 
                    printf("descrição: %s\n", contatos[i].descricao); 
                    printf("-----------------------\n"); 
                } 
                break;

            case 3:
                // salvar contatos em um arquivo
                printf("\ndigite o nome do arquivo para salvar os contatos: "); 
                scanf("%s", nomearquivo); 
                salvarcontatos(contatos, numcontatos, nomearquivo); 
                printf("contatos salvos com sucesso!\n"); 

                // reseta o contador de contatos
                numcontatos = 0;
                break;

            case 4:
                // carregar contatos de um arquivo
                printf("\ndigite o nome do arquivo para carregar os contatos: "); 
                scanf("%s", nomearquivo); 
                carregarcontatos(contatos, &numcontatos, nomearquivo); 
                printf("contatos carregados com sucesso!\n"); 
                break;

            case 5:
                // sair do programa
                printf("saindo do programa.\n"); 
                exit(0); 
                break;

            default:
                // opção inválida
                printf("opção inválida. tente novamente.\n"); 
                break;
        } 
    }

    return 0; 
}
