using System;

using System.Collections.Generic;





namespace DIO.Bank

{

  class Program

  {    

​    

​    static List<Conta> listConta = new List<Conta>();

​    static void Main(string[] args)

​    {



​    Console.WriteLine("Informe a senha!");

​    int senha = int.Parse(Console.ReadLine());    

​    Usuario usuario = new Usuario(senha);

​    usuario.validaSenha();



​      string opcaoUsuario = ObterOpcaoUsuario();



​      while (opcaoUsuario.ToUpper() != "X")

​      {

​        switch (opcaoUsuario)

​        {

​          case "1":

​            ListarContas();

​            break;

​          case "2":

​            InserirConta();

​            break;

​          case "3":

​            Tranferir();

​            break;

​          case "4":

​            Sacar();

​            break;

​          case "5":

​            Depositar();

​            break;

​          case "C":

​            Console.Clear();

​            break;

​          

​          default:

​            throw new ArgumentOutOfRangeException();

​        }



​        opcaoUsuario = ObterOpcaoUsuario();

​      }



​      Console.WriteLine("Obrigado por utilizar nossos serviços.");

​      Console.ReadLine();

​    }



​    private static void Tranferir()

​    {

​      Console.Write("Digite o numero da conta de origem: ");

​      int indiceOrigem = int.Parse(Console.ReadLine());



​      Console.Write("Digite o numero da conta de destino: ");

​      int indiceDestino = int.Parse(Console.ReadLine());



​      Console.Write("Digite o valor a ser transferido: ");

​      double valorTranssferencia = double.Parse(Console.ReadLine());



​      listConta[indiceOrigem].Transferir(valorTranssferencia, listConta[indiceDestino]);

​    }



​    private static void Depositar()

​    {

​      Console.Write("Digite o numero da conta: ");

​      int indiceConta = int.Parse(Console.ReadLine());



​      Console.Write("Digite o valor a ser depositado: ");

​      double valorDeposito = double.Parse(Console.ReadLine());



​      listConta[indiceConta].Depositar(valorDeposito);

​    }



​    private static void Sacar()

​    {

​      Console.Write("Digite o numero da conta: ");

​      int indiceConta = int.Parse(Console.ReadLine());



​      Console.Write("Digite o valor a ser sacado: ");

​      double valorSaque = double .Parse(Console.ReadLine());



​      listConta[indiceConta].Sacar(valorSaque);

​    }



​    private static void ListarContas()

​    {

​      Console.WriteLine("Listar contas");



​      if(listConta.Count == 0)

​      {

​        Console.WriteLine("Nenhuma conta cadastrada.");

​        return;

​      }



​      for(int i = 0; i < listConta.Count; i++)

​      {

​        Conta conta = listConta[i];

​        Console.Write("#{0} - ",i);

​        Console.WriteLine(conta);

​      }

​    }



​    private static void InserirConta()

​    {

​      Console.WriteLine("Inserir nova conta");



​      Console.Write("Digite 1 para Conta Fisica ou 2 para Juridica: ");

​      int entradaTipoConta = int.Parse(Console.ReadLine());



​      Console.Write("Digite o nome do cliente: ");

​      string entradaNome = Console.ReadLine();  



​      Console.Write("Digite o saldo inicial: ");

​      double entradaSaldo = double.Parse(Console.ReadLine());



​      Console.Write("Digite o crédito: ");

​      double entradaCredito = double.Parse(Console.ReadLine());



​      Conta novaConta = new Conta(tipoConta: (TipoConta)entradaTipoConta,

​                    saldo: entradaSaldo,

​                    credito: entradaCredito,

​                    nome: entradaNome);

​      listConta.Add(novaConta);

​    }



​    private static string ObterOpcaoUsuario()

​    {

​      Console.WriteLine();

​      Console.WriteLine("DIO Bank a seu dispor!!");

​      Console.WriteLine("Informe a opção desejada:");



​      Console.WriteLine("1- Listar contas");

​      Console.WriteLine("2- Inserir nova conta");

​      Console.WriteLine("3- Transferir");

​      Console.WriteLine("4- Sacar");

​      Console.WriteLine("5- Depositar");

​      Console.WriteLine("C- Limpar Tela");

​      Console.WriteLine("X- Sair");

​      Console.WriteLine();



​      string opcaoUsuario = Console.ReadLine().ToUpper();

​      Console.WriteLine();

​      return opcaoUsuario;  

​    }

  }

}