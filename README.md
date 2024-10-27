using System;
using System.Collections.Generic;
using System.Linq;

namespace InteractiveCards
{
    class Program
    {
        static void Main(string[] args)
        {
            // Создаем список карточек
            List<Card> cards = new List<Card>()
            {
                new Card("Карточка 1", "Описание карточки 1", "Действие 1"),
                new Card("Карточка 2", "Описание карточки 2", "Действие 2"),
                new Card("Карточка 3", "Описание карточки 3", "Действие 3")
            };

            // Выводим карточки на экран
            Console.WriteLine("Доступные карточки:");
            for (int i = 0; i < cards.Count; i++)
            {
                Console.WriteLine($"{i + 1}. {cards[i].Title}");
            }

            // Запрашиваем выбор пользователя
            Console.WriteLine("Выберите карточку (введите номер):");
            int choice = int.Parse(Console.ReadLine()) - 1;

            // Проверяем, что выбор пользователя валиден
            if (choice >= 0 && choice < cards.Count)
            {
                // Выводим информацию о выбранной карточке
                Console.WriteLine($"\nНазвание: {cards[choice].Title}");
                Console.WriteLine($"Описание: {cards[choice].Description}");

                // Предлагаем выполнить действие
                Console.WriteLine($"Вы хотите выполнить действие \"{cards[choice].Action}\"? (y/n)");
                string actionChoice = Console.ReadLine();

                // Выполняем действие, если пользователь подтвердил
                if (actionChoice.ToLower() == "y")
                {
                    Console.WriteLine($"Действие \"{cards[choice].Action}\" выполнено!");
                }
                else
                {
                    Console.WriteLine("Действие отменено.");
                }
            }
            else
            {
                Console.WriteLine("Неверный номер карточки.");
            }

            Console.WriteLine("\nНажмите любую клавишу для выхода...");
            Console.ReadKey();
        }
    }

    // Класс для представления карточки
    class Card
    {
        public string Title { get; set; }
        public string Description { get; set; }
        public string Action { get; set; }

        public Card(string title, string description, string action)
        {
            Title = title;
            Description = description;
            Action = action;
        }
    }
}
