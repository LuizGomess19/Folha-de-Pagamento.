//CODIGO PARA CALCULAR FOLHA DE PAGAMENTO

import java.util.Scanner;
public class Main {
    public static void main(String[] args) {

        Scanner console = new Scanner(System.in);

        //VARIAVEIS USADAS PARA CADASTRAR FUNCIONARIO
        String nome, cargo, cpf= "";

        //VARIAVEIS PARA ESCOLHER O MES
        int mes = 0;

        //VARIAVEIS PARA FAZER ADMISSAO FUNCIONARIO
        String dataAdmissao = "";

        //VARIAVEIS PARA CALCULAR HORAS TRABALHADAS
        double salarioBruto = 0.0;
        int horasTraDia = 0;
        byte diasTraSemana = 0;
        int horasTraSem = 0;
        int horasTraMes = 0;
        double salarioHora = 0.0;

        //VARIAVEIS PARA CALCULAR INSALUBRIDADE
        String insalubridade = "";
        double beneficioInsalu = 0.0;
        double salarioInsaluBaixo = 0.0;
        double salarioInsaluMedio = 0.0;
        double salarioInsaluAlto = 0.0;

        //VARIAVEIS PARA CALCULAR PERICULOSIDADE
        String periculosidade,opcao = "";
        double beneficioPericu = 0.0;

        //VARIAVEIS PARA CALCULAR VALE TRANSPORTE
        double tarifa = 0.0;
        double valeT = 0.0;
        double valeDesconto = 0.0;
        double valorPagar = 0.0;

        //VARIAVEIS PARA CALCULAR VALE ALIMENTACAO

        double valeAlimDiario = 24.0;
        double diasTraMes = 0.0;
        double valorReceber = 0.0;

        //VARIAVEIS PARA CALCULAR INSS

        double aliquotaInss = 0.0;
        double tetoMaximo = 0.0;
        double inss = 0.0;

        //VARIAVEIS PARA CALCULAR FGTS

        double fgts = 0.08;
        double fgtsRetorno = 0.0;

        //VARIAVEIS PARA CALCULAR IRRF

        double deducaoDepIRRF = 0;
        double salarioBaseIRRF = 0.0;
        double outrasDeduc = 0.0;
        double pensaoAlim = 0.0;
        double totalDeduc = 0.0;
        double baseCaculoIRRF = 0.0;
        double irrf = 0.0;
        double aliquotaIrrf = 0.0;
        int dependenteIRRF = 0;

        //VARIAVEIS PARA CALCULAR SALARIO LIQUIDO
        double salarioLiquido = 0.0;
        double salarioLiquidoBase = 0.0;

        //VARIAVEIS PARA VIZUALIZAR RELATORIO
        String relatorio = "";

        //INICIO DO PROGRAMA!

        System.out.println("\nBEM VINDO AO APP, VAMOS COMEÇAR!");

        System.out.println("Digite o nome completo do funcionario: ");
        nome = console.nextLine();

        System.out.println("Digite a data de admissão do funcionario no formato de (dd/mm/aaaa): ");
        dataAdmissao = console.nextLine();

        System.out.println("Digite o cargo do mesmo na empresa: ");
        cargo = console.nextLine();

        System.out.println("Digite o CPF: ");
        cpf = console.nextLine();

        System.out.println("\nEscolha o mes em numero inteiro para poder proseguir: \nExemplo: janeiro = 1, fevereiro = 2");
        mes = console.nextInt();
        switch (mes) {
            case 1:
                System.out.println("Mes escolhido foi: Janeiro");
                break;
            case 2:
                System.out.println("Mes escolhido foi: Fevereiro");
                break;
            case 3:
                System.out.println("Mes escolhido foi: Março");
                break;
            case 4:
                System.out.println("Mes escolhido foi: Abril");
                break;
            case 5:
                System.out.println("Mes escolhido foi: Maio");
                break;
            case 6:
                System.out.println("Mes escolhido foi: Junho");
                break;
            case 7:
                System.out.println("Mes escolhido foi: Julho");
                break;
            case 8:
                System.out.println("Mes escolhido foi: Agosto");
                break;
            case 9:
                System.out.println("Mes escolhido foi: Setembro");
                break;
            case 10:
                System.out.println("Mes escolhido foi: Outubro");
                break;
            case 11:
                System.out.println("Mes escolhido foi: Novembro");
                break;
            case 12:
                System.out.println("Mes escolhido foi: Dezembro");
                break;
        }
        System.out.println("\n\nDigite o salario bruto: ");
        salarioBruto = console.nextDouble();

        System.out.println("Digite quantas horas ele trabalha no dia: ");
        horasTraDia = console.nextInt();

        System.out.println("Quantos dias trabalha na semana o funcionario: ");
        diasTraSemana = console.nextByte();

        horasTraSem = horasTraDia * diasTraSemana; //CALCULA QUANTAS HORAS TRABALHA NA SEMANA
        horasTraMes = horasTraSem * 5; //CALCULA QUANTAS HORAS TRABALHA NO MES
        salarioHora = salarioBruto / horasTraMes; //CALCULA VALOR PARA RECEBER POR HORA


        //CALCULO DE PERICULOSIDADE
        System.out.println("\n\nINICIO PERICULOSIDADE!");

        beneficioPericu = salarioBruto + (salarioBruto*0.30);
        System.out.println("O funcionario trabalha com periculosidade?\nDigite 'S' para sim 'N' para nao.");
        periculosidade = console.next();

        if (periculosidade.equalsIgnoreCase("S")) {
            System.out.println("O funcionario devera receber um beneficio de 30% somado com o salario bruto"); //beneficioPericu
        } else if (periculosidade.equalsIgnoreCase("N")) {
            System.out.println("O funcionario nao recebera beneficio!");
        } else {
            System.out.println("Opção invalida!");
        }
        System.out.println("FIM PERICULOSIDADE!");


        //CALCULO INSALUBRIDADE
        System.out.println("\n\nINICIO INSALUBRIDADE!");

        System.out.println("Digite 'B' para risco baixo\nDigite 'M' para risco medio\nDigite 'A' para risco alto ");
        opcao = console.next();

        salarioInsaluBaixo = salarioBruto+(salarioBruto*0.10);
        salarioInsaluMedio = salarioBruto+(salarioBruto*0.20);
        salarioInsaluAlto = salarioBruto+(salarioBruto*0.40);

        switch (opcao.toUpperCase()) {
            case "B":
                System.out.println("Voce selecionou risco baixo! \nO funcionario deve receber um aumento de 40% sobre seu salario bruto"); //salarioInsaluBaixo
                break;
            case "M":
                System.out.println("Voce selecionou risco medio! \nOfuncionario deve receber 40% sobre seu salario bruto"); //salarioInsaluMedio
                break;
            case "A":
                System.out.println("Voce selecionou risco alto! \nO funcionario deve receber 40% sobre seu salario bruto"); //salarioInsaluAlto
                break;
            default:
                System.out.println("Opção invalida!");
                break;
        }
        System.out.println("FIM INSALUBRIDADE!");

        //INICIO VALE TRANSPORTE
        System.out.println("\n\nINICIO VALE TRANSPORTE!");

        System.out.println("Digite o valor cobrado para a utilização do transporte publico: ");
        tarifa = console.nextDouble();

        System.out.println("Digite o valor do vale transporte: ");
        valeT = console.nextDouble();

        if (valeT <(salarioBruto*0.06)) {
            valeDesconto = valeT;
        } else {
            valeDesconto = salarioBruto * 0.06;
        }

        valorPagar = salarioBruto - valeDesconto;

        System.out.println("FIM VALE TRANSPORTE!");


        //INICIO CALCULO INSS
        if(salarioBruto <= 1302.00) {
            inss = salarioBruto * 0.075;
        } else if (salarioBruto <=2571.29) {
            inss = (salarioBruto - 1302.00) * 0.09 +97.65;
        } else if (salarioBruto <= 3856.94) {
            inss = (salarioBruto - 2571.29) * 0.12 + 211.89;
        } else if (salarioBruto <= 7507.49) {
            inss = (salarioBruto - 3856.94) * 0.14 + 366.16;
        } else {
            inss = 877.24;
        }
        aliquotaInss = inss / salarioBruto;
        //FIM CALCULO INSS

        //CALCULO IIRF
        System.out.println("\n\nINICIO IRRF!");

        salarioBaseIRRF = salarioBruto - inss;

        System.out.println("Digite quantos dependetes o funcionario tem: ");
        dependenteIRRF = console.nextInt();

        deducaoDepIRRF = dependenteIRRF * 189.59;

        System.out.println("Digite o valor da pensão alimenticia, se nao houver digite '0': ");
        pensaoAlim = console.nextDouble();

        System.out.println("Digite o valor das outras deduções, se não houver digite '0': ");
        outrasDeduc = console.nextDouble();

        totalDeduc = salarioBaseIRRF + dependenteIRRF + pensaoAlim + outrasDeduc;

        baseCaculoIRRF = salarioBruto - totalDeduc;

        if(baseCaculoIRRF <= 1903.98) {
            irrf = 0;
        } else if (baseCaculoIRRF <= 2826.65) {
            irrf = (baseCaculoIRRF - 142.80) * 0.075;
        } else if (baseCaculoIRRF <= 3751.05) {
            irrf = (baseCaculoIRRF - 354.80) * 0.15;
        } else if (baseCaculoIRRF <= 4664.68) {
            irrf = (baseCaculoIRRF - 636.13) * 0.225;
        } else {
            irrf = (baseCaculoIRRF - 869.36) * 0275;
        }
        aliquotaIrrf = irrf / salarioBruto;
        System.out.println("FIM IRRF!");

        //RELATORIO


        System.out.println("\n\nINICIO RELATORIO!!!");
        //CONTAS

        //FGTS
        fgtsRetorno = salarioBruto * fgts;
        //VALE ALIMENTACAO
        diasTraMes = (diasTraSemana * 5);
        valorReceber = valeAlimDiario * diasTraMes;

        System.out.println("Digite 'S' para vizualizar o relatorio! \nDigite 'N' caso não queira vizualisar orelatorio!");
        relatorio = console.next();

        if (relatorio.equalsIgnoreCase("S")) {
            System.out.println("Relatorio pronto para vizualização"); //beneficioPericu
        } else if (relatorio.equalsIgnoreCase("N")) {
            System.out.println("Fim consulta!");
            System.exit(0);
        } else {
            System.out.println("Opção invalida!");
        }

        System.out.println("_______________________________");
        System.out.println("Consulta de dados do funcionario "+nome+":");

        System.out.println("\n\n_______________________________");
        System.out.println("CPF: "+cpf);
        System.out.println("Data de admissão: "+dataAdmissao);
        System.out.println("Cargo: "+cargo);
        System.out.println("Salario bruto: "+salarioBruto);


        System.out.println("\n\n_______________________________");
        System.out.println("\nPROVENTOS!");
        System.out.println(nome+" recebe por horas trabalhadas o valor de: "+salarioHora);
        System.out.println(nome+" recebe de vale transporte: "+valorPagar);
        System.out.println(nome+" recebe de vale alimentação: "+valorReceber);


        System.out.println("\n\n_______________________________");
        System.out.println("\nDESCONTOS!");
        System.out.println("O "+nome+" tem FGTS no valor de: "+fgtsRetorno+" para pagar!");
        System.out.println("Valor do vale alimentação a descontar: "+ valeDesconto);


        System.out.println("\n\n_______________________________");
        System.out.println("SALARIO LIQUIDO!");
        salarioLiquido = salarioBruto + beneficioPericu + beneficioInsalu - aliquotaIrrf - fgtsRetorno - aliquotaInss - valorReceber - valeDesconto;
        System.out.println("O valor do salario liquido é de: "+salarioLiquido);




    }
}//FIM DO PROGRAMA!
