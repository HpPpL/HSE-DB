# Наполнение базы данных

## persons
```sql
INSERT INTO public.persons (name, surname, patronymic)
VALUES
    ('Иван', 'Иванов', 'Иванович'),
    ('Петр', 'Петров', 'Петрович'),
    ('Сидор', 'Сидоров', 'Сидорович'),
    ('Анна', 'Иванова', 'Ивановна'),
    ('Елена', 'Петрова', 'Петровна'),
    ('Ольга', 'Сидорова', 'Сидоровна'),
    ('Николай', 'Николаев', 'Николаевич'),
    ('Михаил', 'Михайлов', 'Михайлович'),
    ('Сергей', 'Сергеев', 'Сергеевич'),
    ('Дмитрий', 'Дмитриев', 'Дмитриевич');

```

## plot_status
```sql
INSERT INTO public.plot_status (id, status)
VALUES
    (0, 'Неактивный'),
    (1, 'Активный');

```

## plot_status
```sql
INSERT INTO public.ownership_type (type)
VALUES
    ('Покупатель'),
    ('Наследник'),
    ('Арендатор');
```

## plots
```sql
INSERT INTO public.plots (id, status_id)
VALUES
    (1, 1),
    (2, 1),
    (3, 1),
    (4, 0),
    (5, 0),
    (6, 1),
    (7, 1),
    (8, 1),
    (9, 1),
    (10, 1);
```

## periods
```sql
INSERT INTO public.periods (month, year)
VALUES
    (11, 2023),
    (12, 2023),
    (1, 2024),
    (2, 2024),
    (3, 2024),
    (4, 2024),
    (5, 2024),
    (6, 2024),
    (7, 2024),
    (8, 2024);
```

## expenses
```sql
INSERT INTO public.expenses (name)
VALUES
    ('Электроэнергия'),
    ('Вывоз мусора'),
    ('Охрана'),
    ('Обслуживание банка'),
    ('Канцелярские расходы'),
    ('Интернет и связь'),
    ('Ремонт и обслуживание оборудования'),
    ('Зарплата сотрудникам'),
    ('Аренда помещения'),
    ('Покупка программного обеспечения');
```

## incomes
```sql
INSERT INTO public.incomes (name)
VALUES
    ('Членские взносы'),
    ('Дополнительные взносы'),
    ('Целевые взносы'),
    ('Оплата за электроэнергию'),
    ('Доходы от аренды помещений'),
    ('Доходы от проведения мероприятий'),
    ('Продажа продукции'),
    ('Благотворительные взносы'),
    ('Гранты и субсидии'),
    ('Проценты по депозитам');
```

## plot_expenses
```sql
INSERT INTO public.plot_expenses (id, period_id, plot_id, expense_id, value)
VALUES
    -- Расходы для участка 1
    (uuid_generate_v4(), 1, 1, 1, 1500.00),  -- Ноябрь 2023, Электроэнергия
    (uuid_generate_v4(), 2, 1, 2, 500.00),   -- Декабрь 2023, Вывоз мусора
    (uuid_generate_v4(), 3, 1, 3, 2000.00),  -- Январь 2024, Охрана
    (uuid_generate_v4(), 4, 1, 4, 300.00),   -- Февраль 2024, Обслуживание банка
    (uuid_generate_v4(), 5, 1, 5, 250.00),   -- Март 2024, Канцелярские расходы

    -- Расходы для участка 2
    (uuid_generate_v4(), 1, 2, 1, 1600.00),  -- Ноябрь 2023, Электроэнергия
    (uuid_generate_v4(), 2, 2, 2, 550.00),   -- Декабрь 2023, Вывоз мусора
    (uuid_generate_v4(), 3, 2, 3, 2100.00),  -- Январь 2024, Охрана
    (uuid_generate_v4(), 4, 2, 6, 600.00),   -- Февраль 2024, Интернет и связь
    (uuid_generate_v4(), 5, 2, 7, 700.00),   -- Март 2024, Ремонт и обслуживание оборудования

    -- Расходы для участка 3
    (uuid_generate_v4(), 1, 3, 1, 1700.00),  -- Ноябрь 2023, Электроэнергия
    (uuid_generate_v4(), 2, 3, 8, 8000.00),  -- Декабрь 2023, Зарплата сотрудникам
    (uuid_generate_v4(), 3, 3, 9, 12000.00), -- Январь 2024, Аренда помещения
    (uuid_generate_v4(), 4, 3, 10, 1500.00), -- Февраль 2024, Покупка программного обеспечения
    (uuid_generate_v4(), 5, 3, 2, 600.00);   -- Март 2024, Вывоз мусора
```

## partnership_income
```sql
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
```

```sql
INSERT INTO public.partnership_income (id, persona_id, income_id, period_id, plot_id, value)
VALUES
    (uuid_generate_v4(), 1, 1, 1, 1, 5000.00),  -- Членские взносы, Ноябрь 2023, Участок 1
    (uuid_generate_v4(), 2, 2, 2, 2, 3000.00),  -- Дополнительные взносы, Декабрь 2023, Участок 2
    (uuid_generate_v4(), 3, 3, 3, 3, 7000.00),  -- Целевые взносы, Январь 2024, Участок 3
    (uuid_generate_v4(), 4, 4, 4, 1, 4500.00),  -- Оплата за электроэнергию, Февраль 2024, Участок 1
    (uuid_generate_v4(), 5, 5, 5, 2, 6000.00),  -- Доходы от аренды помещений, Март 2024, Участок 2
    (uuid_generate_v4(), 6, 6, 6, 3, 8000.00),  -- Доходы от проведения мероприятий, Ноябрь 2023, Участок 3
    (uuid_generate_v4(), 7, 7, 7, 7, 12000.00), -- Продажа продукции, Декабрь 2023, Участок 1
    (uuid_generate_v4(), 8, 8, 8, 8, 2000.00),  -- Благотворительные взносы, Январь 2024, Участок 2
    (uuid_generate_v4(), 9, 9, 9, 9, 9000.00),  -- Гранты и субсидии, Февраль 2024, Участок 3
    (uuid_generate_v4(), 10, 10, 10, 10, 4000.00);-- Проценты по депозитам, Март 2024, Участок 1
```

## ownership

```sql
INSERT INTO public.ownership (person_id, plot_id, ownership_id, start_period_id, end_period_id)
VALUES
    (1, 1, 1, 1, 5),  -- Иван Иванов, Участок 1, Покупатель, с Ноября 2023 по Март 2024
    (2, 2, 2, 2, 6),  -- Петр Петров, Участок 2, Наследник, с Декабря 2023 по Апрель 2024
    (3, 3, 3, 3, 7),  -- Сидор Сидоров, Участок 3, Арендатор, с Января 2024 по Май 2024
    (4, 4, 1, 1, 5),  -- Анна Иванова, Участок 4, Покупатель, с Ноября 2023 по Март 2024
    (5, 5, 2, 2, 6),  -- Елена Петрова, Участок 5, Наследник, с Декабря 2023 по Апрель 2024
    (6, 6, 3, 3, 7),  -- Ольга Сидорова, Участок 6, Арендатор, с Января 2024 по Май 2024
    (7, 7, 1, 1, 5),  -- Николай Николаев, Участок 7, Покупатель, с Ноября 2023 по Март 2024
    (8, 8, 2, 2, 6),  -- Михаил Михайлов, Участок 8, Наследник, с Декабря 2023 по Апрель 2024
    (9, 9, 3, 3, 7),  -- Сергей Сергеев, Участок 9, Арендатор, с Января 2024 по Май 2024
    (10, 10, 1, 1, 5); -- Дмитрий Дмитриев, Участок 10, Покупатель, с Ноября 2023 по Март 2024

```

# Проверка выполнения sql-запросов
## Найти всех владельцев, являющихся собственниками более чем одного участка
```sql
SELECT 
    o.person_id,
    p.name,
    p.surname,
    p.patronymic,
    COUNT(o.plot_id) as plot_count
FROM 
    public.ownership o
JOIN 
    public.persons p ON o.person_id = p.id
GROUP BY 
    o.person_id, p.name, p.surname, p.patronymic
HAVING 
    COUNT(o.plot_id) > 1;
```

## Найти все участки, приобретенные (владельцы с типом «покупатель») за заданный период

```sql
SELECT 
    o.plot_id,
    o.person_id,
    p.name,
    p.surname,
    p.patronymic,
    o.start_period_id,
    o.end_period_id
FROM 
    public.ownership o
JOIN 
    public.ownership_type ot ON o.ownership_id = ot.id
JOIN 
    public.persons p ON o.person_id = p.id
WHERE 
    ot.type = 'Покупатель' 
    AND o.start_period_id >= 1   -- Ноябрь 2023
    AND o.end_period_id <= 5;   -- Март 2024
```

## Найти все участки, принадлежащие владельцам с указанным типом на заданную дату

```sql
SELECT 
    o.plot_id,
    o.person_id,
	ot.type AS ownership_type,
    p.name,
    p.surname,
    p.patronymic,
    o.start_period_id,
    o.end_period_id
FROM 
    public.ownership o
JOIN 
    public.ownership_type ot ON o.ownership_id = ot.id
JOIN 
    public.persons p ON o.person_id = p.id
WHERE 
    ot.type = 'Покупатель'   -- Можно заменить на требуемый тип персоны
    AND o.start_period_id >= 1   -- Можно заменить на требуемый начальный период
    AND o.end_period_id <= 5;   -- Можно заменить на требуемый конечный период


```

## Определить размер взноса с заданного участка на погашение расходов по заданной статье расходов

Быть честным - не совсем понял, что требуется в запросе (иначе проектировал БД). Поэтому сделаю суммарный доход по всем статьям в выбранном участке за период + суммарные рассходы по каждой статье в отдельных столбцах за период.

```sql
SELECT 
    p.id AS period_id,
    p.month,
    p.year,
    COALESCE(SUM(pi.value), 0) AS total_income,
    COALESCE(SUM(pe1.value), 0) AS total_expense_electricity,
    COALESCE(SUM(pe2.value), 0) AS total_expense_trash_removal,
    COALESCE(SUM(pe3.value), 0) AS total_expense_security,
    COALESCE(SUM(pe4.value), 0) AS total_expense_bank_service,
    COALESCE(SUM(pe5.value), 0) AS total_expense_office_supplies,
    COALESCE(SUM(pe6.value), 0) AS total_expense_internet,
    COALESCE(SUM(pe7.value), 0) AS total_expense_equipment_maintenance,
    COALESCE(SUM(pe8.value), 0) AS total_expense_salaries,
    COALESCE(SUM(pe9.value), 0) AS total_expense_rent,
    COALESCE(SUM(pe10.value), 0) AS total_expense_software_purchase
FROM 
    public.periods p
LEFT JOIN 
    public.partnership_income pi ON p.id = pi.period_id AND pi.plot_id = 1
LEFT JOIN 
    public.plot_expenses pe1 ON p.id = pe1.period_id AND pe1.plot_id = 1 AND pe1.expense_id = 1
LEFT JOIN 
    public.plot_expenses pe2 ON p.id = pe2.period_id AND pe2.plot_id = 1 AND pe2.expense_id = 2
LEFT JOIN 
    public.plot_expenses pe3 ON p.id = pe3.period_id AND pe3.plot_id = 1 AND pe3.expense_id = 3
LEFT JOIN 
    public.plot_expenses pe4 ON p.id = pe4.period_id AND pe4.plot_id = 1 AND pe4.expense_id = 4
LEFT JOIN 
    public.plot_expenses pe5 ON p.id = pe5.period_id AND pe5.plot_id = 1 AND pe5.expense_id = 5
LEFT JOIN 
    public.plot_expenses pe6 ON p.id = pe6.period_id AND pe6.plot_id = 1 AND pe6.expense_id = 6
LEFT JOIN 
    public.plot_expenses pe7 ON p.id = pe7.period_id AND pe7.plot_id = 1 AND pe7.expense_id = 7
LEFT JOIN 
    public.plot_expenses pe8 ON p.id = pe8.period_id AND pe8.plot_id = 1 AND pe8.expense_id = 8
LEFT JOIN 
    public.plot_expenses pe9 ON p.id = pe9.period_id AND pe9.plot_id = 1 AND pe9.expense_id = 9
LEFT JOIN 
    public.plot_expenses pe10 ON p.id = pe10.period_id AND pe10.plot_id = 1 AND pe10.expense_id = 10
WHERE
    p.id BETWEEN 1 AND 5 -- Можно заменить на требуемый начальный и конечный периоды
GROUP BY 
    p.id, p.month, p.year
ORDER BY 
    p.year, p.month;
```

## Определить самый популярный период внесения взносов

```sql
SELECT 
    p.id AS period_id,
    p.month,
    p.year,
    COUNT(pi.id) AS contributions_count
FROM 
    public.partnership_income pi
JOIN 
    public.periods p ON pi.period_id = p.id
GROUP BY 
    p.id, p.month, p.year
ORDER BY 
    contributions_count DESC
LIMIT 1;
```

## Вывести список всех статусов участка с указанием процента от общего
количества участков в СНТ
```sql
SELECT 
    ps.status,
    COUNT(pl.id) AS count,
    ROUND((COUNT(pl.id) * 100.0 / (SELECT COUNT(*) FROM public.plots)), 2) AS percentage
FROM 
    public.plot_status ps
LEFT JOIN 
    public.plots pl ON ps.id = pl.status_id
GROUP BY 
    ps.status;

```

## Сформировать приходную ведомость, имеющую следующую структуру: "№ участка", "ФИО владельца", "Статья прихода", "Сумма"

Тоже не совсем понял запроса, поэтому сделаю суммарный доход по каждой статье за все время для каждого участка.

```sql
SELECT 
    pl.id AS "№ участка",
    CONCAT(p.surname, ' ', p.name, ' ', p.patronymic) AS "ФИО владельца",
    COALESCE(SUM(CASE WHEN pi.income_id = 1 THEN pi.value ELSE 0 END), 0) AS "Членские взносы",
    COALESCE(SUM(CASE WHEN pi.income_id = 2 THEN pi.value ELSE 0 END), 0) AS "Дополнительные взносы",
    COALESCE(SUM(CASE WHEN pi.income_id = 3 THEN pi.value ELSE 0 END), 0) AS "Целевые взносы",
    COALESCE(SUM(CASE WHEN pi.income_id = 4 THEN pi.value ELSE 0 END), 0) AS "Оплата за электроэнергию",
    COALESCE(SUM(CASE WHEN pi.income_id = 5 THEN pi.value ELSE 0 END), 0) AS "Доходы от аренды помещений",
    COALESCE(SUM(CASE WHEN pi.income_id = 6 THEN pi.value ELSE 0 END), 0) AS "Доходы от проведения мероприятий",
    COALESCE(SUM(CASE WHEN pi.income_id = 7 THEN pi.value ELSE 0 END), 0) AS "Продажа продукции",
    COALESCE(SUM(CASE WHEN pi.income_id = 8 THEN pi.value ELSE 0 END), 0) AS "Благотворительные взносы",
    COALESCE(SUM(CASE WHEN pi.income_id = 9 THEN pi.value ELSE 0 END), 0) AS "Гранты и субсидии",
    COALESCE(SUM(CASE WHEN pi.income_id = 10 THEN pi.value ELSE 0 END), 0) AS "Проценты по депозитам"
FROM 
    public.plots pl
LEFT JOIN 
    public.ownership o ON pl.id = o.plot_id
LEFT JOIN 
    public.persons p ON o.person_id = p.id
LEFT JOIN 
    public.partnership_income pi ON pl.id = pi.plot_id
GROUP BY 
    pl.id, p.surname, p.name, p.patronymic
ORDER BY 
    pl.id;
```

## Сформировать смету расходов в виде таблицы "Статья расхода" и "Сумма" для СНТ за заданный период
```sql
SELECT 
    p.year,
    p.month,
    COALESCE(SUM(CASE WHEN pe.expense_id = 1 THEN pe.value ELSE 0 END), 0) AS "Электроэнергия",
    COALESCE(SUM(CASE WHEN pe.expense_id = 2 THEN pe.value ELSE 0 END), 0) AS "Вывоз мусора",
    COALESCE(SUM(CASE WHEN pe.expense_id = 3 THEN pe.value ELSE 0 END), 0) AS "Охрана",
    COALESCE(SUM(CASE WHEN pe.expense_id = 4 THEN pe.value ELSE 0 END), 0) AS "Обслуживание банка",
    COALESCE(SUM(CASE WHEN pe.expense_id = 5 THEN pe.value ELSE 0 END), 0) AS "Канцелярские расходы",
    COALESCE(SUM(CASE WHEN pe.expense_id = 6 THEN pe.value ELSE 0 END), 0) AS "Интернет",
    COALESCE(SUM(CASE WHEN pe.expense_id = 7 THEN pe.value ELSE 0 END), 0) AS "Ремонт и обслуживание оборудования",
    COALESCE(SUM(CASE WHEN pe.expense_id = 8 THEN pe.value ELSE 0 END), 0) AS "Зарплата сотрудникам",
    COALESCE(SUM(CASE WHEN pe.expense_id = 9 THEN pe.value ELSE 0 END), 0) AS "Аренда помещения",
    COALESCE(SUM(CASE WHEN pe.expense_id = 10 THEN pe.value ELSE 0 END), 0) AS "Покупка программного обеспечения",
    COALESCE(SUM(pe.value), 0) AS "Суммарные расходы"
FROM 
    public.plot_expenses pe
JOIN 
    public.periods p ON pe.period_id = p.id
WHERE 
    p.id BETWEEN 1 AND 5 -- Можно заменить на требуемый начальный и конечный периоды
GROUP BY 
    p.year, p.month
ORDER BY 
    p.year, p.month;

```
