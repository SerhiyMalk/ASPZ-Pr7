# Практична робота №7: Системне програмування в Linux

Цей репозиторій містить рішення завдань із системного програмування під Linux мовою C. Метою роботи є поглиблене вивчення системних викликів (syscalls), роботи з файловими дескрипторами, процесами, конвеєрами та управління доступом. 

У рамках роботи були реалізовані спрощені аналоги стандартних утиліт UNIX (`ls`, `grep`, `more` тощо) без прямого використання системних команд через `system()`.

##  Опис завдань (Загальна частина)
Task 1 (task1.c) — Зв'язок команд (Конвеєр): Використовує popen() для передачі виводу команди rwho до утиліти more. Демонструє міжпроцесну взаємодію через канали (pipes).
<img width="502" height="100" alt="Screenshot 2026-05-17 181533" src="https://github.com/user-attachments/assets/36314b33-c1e5-46a3-b8ba-e016818d7af4" />

Task 2 (task2.c) — Аналог ls -l: Імітує роботу ls -l. Читає поточну директорію (opendir/readdir) та виводить детальну інформацію про кожен файл (права доступу, власник, розмір, дата модифікації), використовуючи структуру stat.
<img width="851" height="708" alt="Screenshot 2026-05-17 181613" src="https://github.com/user-attachments/assets/6a136d49-d035-4dc3-93bb-063d3ac54703" />


Task 3 (task3.c) — Аналог grep: Шукає задане слово у файлі та виводить рядки, що його містять. Приймає слово та ім'я файлу як аргументи командного рядка.
<img width="1090" height="126" alt="Screenshot 2026-05-17 181713" src="https://github.com/user-attachments/assets/827ecfeb-b4a9-4da7-8691-e63f885f078d" />

Task 4 (task4.c) — Аналог more: Виводить вміст файлів із зупинкою кожні 20 рядків. Реалізовано читання натискань клавіатури безпосередньо з /dev/tty.
<img width="1424" height="555" alt="Screenshot 2026-05-17 181827" src="https://github.com/user-attachments/assets/24604f9a-3ebb-4f64-b84f-0108e271efcf" />

Task 5 (task5.c) — Рекурсивний обхід директорій: Рекурсивно проходить і виводить усі файли у поточному каталозі та всіх його підкаталогах.
<img width="1467" height="699" alt="Screenshot 2026-05-17 182024" src="https://github.com/user-attachments/assets/0c926a9a-63f7-4112-8d09-8b82c70cec8b" />

Task 6 (task6.c) — Алфавітне сортування підкаталогів: Перелічує лише директорії у поточному каталозі, відсортовані за алфавітом. Реалізовано за допомогою scandir() та alphasort().
<img width="641" height="292" alt="Screenshot 2026-05-17 182119" src="https://github.com/user-attachments/assets/e8425c63-1b0e-4703-98be-d8f13dbbf8fa" />

Task 7 (task7.c) — Інтерактивна зміна прав доступу: Знаходить усі файли з розширенням .c, які належать поточному користувачу (getuid()), і пропонує змінити їхні права доступу (додати права на читання для групи та інших через chmod()).
<img width="881" height="474" alt="Screenshot 2026-05-17 182349" src="https://github.com/user-attachments/assets/6aba643a-3b41-4f35-ac59-abdaed0a71ef" />
<img width="944" height="462" alt="Screenshot 2026-05-17 182338" src="https://github.com/user-attachments/assets/2cb75d16-4d86-417a-8201-ba1744351b6d" />
Task 8 (task8.c) — Інтерактивне видалення файлів: Дозволяє користувачу безпечно та інтерактивно видаляти файли в поточній директорії за допомогою системного виклику unlink().

<img width="607" height="204" alt="Screenshot 2026-05-17 182541" src="https://github.com/user-attachments/assets/a37ecab1-a592-4c72-83d2-a0565215c9da" />
<img width="672" height="534" alt="Screenshot 2026-05-17 182535" src="https://github.com/user-attachments/assets/0a18faf8-3959-4249-9c34-4f443d8bbbe3" />

Task 9 (task9.c) — Профілювання часу: Вимірює час виконання фрагмента коду в мілісекундах за допомогою gettimeofday().
<img width="603" height="147" alt="Screenshot 2026-05-17 182628" src="https://github.com/user-attachments/assets/a37ce5c6-d633-444e-becb-4e84eba14de3" />

Task 10 (task10.c) — Унікальний генератор чисел: Генерує послідовності випадкових чисел з плаваючою комою у діапазонах (0.0 – 1.0) та (0.0 – n). Використовує srand(time(NULL)) для унікальності.
<img width="518" height="375" alt="Screenshot 2026-05-17 182718" src="https://github.com/user-attachments/assets/9c7043f9-4d2a-4f67-83b4-e9c0ecd81357" />

## Індивідуальне завдання (Варіант 11)
Task 11 (task11.c) — Аналізатор історії команд:
Завдання: Розробити програму, яка визначає найменш використовувані команди в історії користувача (.bash_history), не аналізуючи сам файл напряму в коді C.
Рішення: Використано делегування системі. Програма створює складний конвеєр стандартних утиліт (cat, grep, awk, sort, uniq, head) та виконує його через popen(), беручи на себе лише форматований вивід результату.
<img width="591" height="395" alt="Screenshot 2026-05-17 182834" src="https://github.com/user-attachments/assets/c22d8759-0f13-4046-beec-8e366bdf9183" />


