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

void salvarContatos(Contato contatos[], int numContatos,
                    const char *nomeArquivo) {
  FILE *arquivo = fopen(nomeArquivo, "w");
  if (arquivo == NULL) {
    printf("Erro ao abrir o arquivo.\n");
    exit(1);
  }

  for (int i = 0; i < numContatos; i++) {
    fprintf(arquivo,"Nome: %s\nTelefone: %s\nEmail: %s\nDescrição: %s\n--------------\n", contatos[i].nome, contatos[i].telefone, contatos[i].email,contatos[i].descricao);
  }

  fclose(arquivo);
}

void carregarContatos(Contato contatos[], int *numContatos,
                      const char *nomeArquivo) {
  FILE *arquivo = fopen(nomeArquivo, "r");
  if (arquivo == NULL) {
    printf("Erro ao abrir o arquivo.\n");
    exit(1);
  }

  while (fscanf(arquivo, "%[^;];%[^;];%[^;];%[^\n]\n",
                contatos[*numContatos].nome, contatos[*numContatos].telefone,
                contatos[*numContatos].email,
                contatos[*numContatos].descricao) != EOF) {
    (*numContatos)++;
  }

  fclose(arquivo);
}

int main() {
  Contato contatos[MAX_CONTATOS];
  char nomeArquivo[50];
  int opcao, numContatos = 0;

  while (1) {
    printf("\nSelecione uma opção:\n");
    printf("1 - Adicionar contato\n");
    printf("2 - Listar contatos\n");
    printf("3 - Salvar contatos em um arquivo\n");
    printf("4 - Carregar contatos de um arquivo\n");
    printf("5 - Sair\n");
    scanf("%d", &opcao);

    switch (opcao) {
    case 1:
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

    case 2:
      for (int i = 0; i < numContatos; i++) {
        printf("\nNome: %s\n", contatos[i].nome);
        printf("Telefone: %s\n", contatos[i].telefone);
        printf("Email: %s\n", contatos[i].email);
        printf("Descrição: %s\n", contatos[i].descricao);
        printf("-----------------------\n");
      }
      break;

    case 3:
      printf("\nDigite o nome do arquivo para salvar os contatos: ");
      scanf("%s", nomeArquivo);
      salvarContatos(contatos, numContatos, nomeArquivo);
      printf("Contatos salvos com sucesso!\n");
      break;

    case 4:
      printf("\nDigite o nome do arquivo para carregar os contatos: ");
      scanf("%s", nomeArquivo);
      carregarContatos(contatos, &numContatos, nomeArquivo);
      printf("Contatos carregados com sucesso!\n");
      break;

    case 5:
      printf("Saindo do programa.\n");
      exit(0);
      break;

    default:
      printf("Opção inválida. Tente novamente.\n");
      break;
    }
  }

  return 0;
}
