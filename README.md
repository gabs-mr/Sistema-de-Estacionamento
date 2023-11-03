# Sistema-de-Estacionamento
Neste Projeto de LAB você será desafiado a construir um sistema para um estacionamento, que será usado para gerenciar os veículos estacionados e realizar suas operações, como por exemplo adicionar um veículo, remover um veículo (e exibir o valor cobrado durante o período) e listar os veículos.

using System;
using System.Collections.Generic;

class Estacionamento
{
    static void Main()
    {
        List<Veiculo> veiculosEstacionados = new List<Veiculo>();

        while (true)
        {
            Console.WriteLine("Escolha uma opção:");
            Console.WriteLine("1. Adicionar veículo");
            Console.WriteLine("2. Remover veículo");
            Console.WriteLine("3. Listar veículos");
            Console.WriteLine("4. Sair");

            string opcao = Console.ReadLine();

            switch (opcao)
            {
                case "1":
                    AdicionarVeiculo(veiculosEstacionados);
                    break;
                case "2":
                    RemoverVeiculo(veiculosEstacionados);
                    break;
                case "3":
                    ListarVeiculos(veiculosEstacionados);
                    break;
                case "4":
                    return;
                default:
                    Console.WriteLine("Opção inválida. Por favor, escolha uma opção válida.");
                    break;
            }
        }
    }

    static void AdicionarVeiculo(List<Veiculo> veiculos)
    {
        Console.WriteLine("Informe a placa do veículo:");
        string placa = Console.ReadLine();

        Veiculo veiculo = new Veiculo(placa);
        veiculos.Add(veiculo);
        Console.WriteLine("Veículo adicionado com sucesso.");
    }

    static void RemoverVeiculo(List<Veiculo> veiculos)
    {
        Console.WriteLine("Informe a placa do veículo a ser removido:");
        string placa = Console.ReadLine();

        Veiculo veiculo = veiculos.Find(v => v.Placa == placa);
        if (veiculo != null)
        {
            veiculos.Remove(veiculo);
            Console.WriteLine($"Veículo com placa {placa} foi removido.");
            // Aqui você pode calcular e exibir o valor cobrado durante o período, se necessário.
        }
        else
        {
            Console.WriteLine("Veículo não encontrado.");
        }
    }

    static void ListarVeiculos(List<Veiculo> veiculos)
    {
        Console.WriteLine("Veículos estacionados:");
        foreach (Veiculo veiculo in veiculos)
        {
            Console.WriteLine($"Placa: {veiculo.Placa}");
        }
    }
}

class Veiculo
{
    public string Placa { get; set; }

    public Veiculo(string placa)
    {
        Placa = placa;
    }
}
