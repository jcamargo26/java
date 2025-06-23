# java 


import java.util.Arrays;
import java.util.Scanner;

public class projeto { //declaração das variáveis globais
     static int n; //declaração do número de alunos que o usuário vai cadastrar.
    static String[] nome; //vetor para o nome no cadastro
    static double[] nota1; //vetor para a primeira nota
    static double[] nota2;  //vetor para a segunda nota
    static double[] nota3;  //vetor para a terceira nota
    static double[] media;  //vetor para a media das notas
    static String[] situacoes;  //vetor para a situacao(aprovado e reprovado)

    // Metodo principal que executa o fluxo do programa.
    // Ele chama o cadastro dos alunos e depois gera o relatório final.
    public static void main(String[] args) {
        cadastrarAluno(); //chamando função cadastrar aluno.
        System.out.println("===============================================");
        relatorioFinal(); //chamando o relatório final para a Main.
        System.out.println("===============================================");



    }
    public static void cadastrarAluno() { //procedimento para cadastro de alunos
        Scanner scan = new Scanner(System.in); // objeto scanner para entrada de dados
        System.out.print("Digite o número de alunos que deseja cadastrar: ");
        n = scan.nextInt();
        //inicializa os vetores com o número de alunos (n) informado.
        nome = new String[n];
        nota1 = new double[n];
        nota2 = new double[n];
        nota3 = new double[n];
        media = new double[n];
        situacoes = new String[n];

        for (int i = 0; i < n; i++) { //estrutura de repetição para cadastro de aluno
            System.out.println("\n==========CADASTRO DO ALUNO " +(i+1) + "==========.");
            System.out.println("Digite o nome do aluno: ");
            nome[i] = scan.next();
            System.out.println("Digite o valor da primeira nota: ");
            nota1[i] = scan.nextDouble();
            System.out.println("Digite o valor da segunda nota: ");
            nota2[i] = scan.nextDouble();
            System.out.println("Digite o valor da terceira nota: ");
            nota3[i] = scan.nextDouble();

            scan.nextLine();//limpa o buffer do scanner (corrige problema de quebra de linha)
            media[i] = calcularMedia(nota1[i], nota2[i], nota3[i]); //calcula a média do aluno chamando a função calcularMedia
            situacoes[i] = determinarSituacao(media[i]); //determina a situação do aluno (Aprovado ou Reprovado) chamando a função determinarSituacao
        }


    } public static double calcularMedia(double nota1, double nota2, double nota3){//função para calcular média
        double media = (nota1 + nota2+ nota3)/3; //faz a media simples das 3 notas
        System.out.println("A média do aluno é: "+media);
        return media; //retorna a media calculada
    }
    public static String determinarSituacao(double media){ //função que determina a situação (aprovado/reprovado)
            if (media >= 7){
                return "Aprovado."; //estrutura de decisao para saber o valor da media e definir a situação
            } else {
                return "Reprovado.";

            }

    } public static void relatorioFinal() {
        System.out.println("\nRELATÓRIO FINAL.");
        int i;
        for (i = 0; i < n; i++) { //estrutura de repetição para exibir as informações de cada aluno
            System.out.println("Aluno: " + nome[i]);
            System.out.println("Notas: " + nota1[i] + ", " + nota2[i] + ", " + nota3[i]);
            System.out.println("Média: " + String.format("%.2f", media[i])); //utilizei o string format para ficar com duas casas decimais.
            System.out.println("Situação: " + situacoes[i]);
            System.out.println("------------------------");

        }


    }}
