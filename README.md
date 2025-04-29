#include <iostream>
using namespace std;

float calcularMedia(float n1, float n2, float n3) {
    return (n1 + n2 + n3) / 3.0;
}

int main() {
    const int MAX_ALUNOS = 5;
    string nomes[MAX_ALUNOS];
    float notas1[MAX_ALUNOS], notas2[MAX_ALUNOS], notas3[MAX_ALUNOS];
    float medias[MAX_ALUNOS];
    int qtdAlunos;
    int i;

    cout << "Quantos alunos deseja cadastrar? (ate 5): ";
    cin >> qtdAlunos;

    if (qtdAlunos > MAX_ALUNOS || qtdAlunos < 1) {
        cout << "Quantidade invalida!" << endl;
        return 1;
    }

    for (i = 0; i < qtdAlunos; i++) {
        cout << "\nDigite o nome do aluno " << i + 1 << ": ";
        cin.ignore(); 
        getline(cin, nomes[i]);

        cout << "Digite a primeira nota: ";
        cin >> notas1[i];

        cout << "Digite a segunda nota: ";
        cin >> notas2[i];

        cout << "Digite a terceira nota: ";
        cin >> notas3[i];

        medias[i] = calcularMedia(notas1[i], notas2[i], notas3[i]);
    }

    cout << "\nResultados:\n";
    for (i = 0; i < qtdAlunos; i++) {
        cout << "\nAluno: " << nomes[i] << endl;
        cout << "Notas: " << notas1[i] << ", " << notas2[i] << ", " << notas3[i] << endl;
        cout << "Media: " << medias[i] << endl;

        if (medias[i] >= 7.0) {
            cout << "Situacao: Aprovado\n";
        } else {
            cout << "Situacao: Reprovado\n";
        }
    }

    int indiceMaior = 0;
    for (i = 1; i < qtdAlunos; i++) {
        if (medias[i] > medias[indiceMaior]) {
            indiceMaior = i;
        }
    }

    cout << "\nAluno com a maior media: " << nomes[indiceMaior] << " com media " << medias[indiceMaior] << endl;

    return 0;
}
