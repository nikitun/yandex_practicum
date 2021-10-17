# Подготовка прототипа модели для металлообрабатывающего предприятия

**Описание проекта**

Подготовьте прототип модели машинного обучения для «Цифры». Компания разрабатывает решения для эффективной работы промышленных предприятий.

Модель должна предсказать коэффициент восстановления золота из золотосодержащей руды. Используйте данные с параметрами добычи и очистки.

Модель поможет оптимизировать производство, чтобы не запускать предприятие с убыточными характеристиками.

Вам нужно:

1. Подготовить данные;
2. Провести исследовательский анализ данных;
3. Построить и обучить модель.

**Описание данных**

Обозначения, используемые в названиях признаков на всех этапах очистки:
- ag &mdash; концетрация серебра;
- pb &mdash; концетрация свинца;
- sol &mdash; концетрация солей;
- au &mdash; концетрация золота;
- feed_size &mdash; размер гранул сырья;
- feed_rate &mdash; скорость подачи;
- sulfate &mdash; концентрация сульфида натрия;
- xanthate &mdash; концентрация ксантогента;
- air &mdash; объём воздуха;
- level &mdash; уровень жидкости;
- recovery &mdash; эффективность обогащения чернового концентрата/руды.

Этап флотации:
- Параметры сырья:
    - rougher.input.feed_ag;
    - rougher.input.feed_pb;
    - rougher.input.feed_sol;
    - rougher.input.feed_au;
    - rougher.input.feed_size;
    - rougher.input.feed_rate;
- Параметры флотационной установки:
    - rougher.input.floatbank10_sulfate;
    - rougher.input.floatbank10_xanthate;
    - rougher.input.floatbank11_sulfate;
    - rougher.input.floatbank11_xanthate;
- Параметры состояние этапа:
    - rougher.state.floatbank10_a_air;
    - rougher.state.floatbank10_a_level;
    - rougher.state.floatbank10_b_air;
    - rougher.state.floatbank10_b_level;
    - rougher.state.floatbank10_c_air;
    - rougher.state.floatbank10_c_level;
    - rougher.state.floatbank10_d_air;
    - rougher.state.floatbank10_d_level;
    - rougher.state.floatbank10_e_air;
    - rougher.state.floatbank10_e_level;
    - rougher.state.floatbank10_f_air;
    - rougher.state.floatbank10_f_level;
- Параметры продукта:
    - rougher.output.concentrate_ag;
    - rougher.output.concentrate_pb;
    - rougher.output.concentrate_sol;
    - rougher.output.concentrate_au;
    - rougher.output.recovery;
- Параметры отвальных хвостов:
    - rougher.output.tail_ag;
    - rougher.output.tail_pb;
    - rougher.output.tail_sol;
    - rougher.output.tail_au;
- Вычисляемые параметры:
    - rougher.calculation.sulfate_to_au_concentrate;
    - rougher.calculation.floatbank10_sulfate_to_au_feed;
    - rougher.calculation.floatbank11_sulfate_to_au_feed;
    - rougher.calculation.au_pb_ratio.

Этап первичной очистки:
- Параметры сырья:
    - primary_cleaner.input.feed_size;
    - primary_cleaner.input.sulfate;
- Параметры очистительной установки:
    - primary_cleaner.input.depressant;
    - primary_cleaner.input.xanthate;
- Параметры состояние этапа:
    - primary_cleaner.state.floatbank8_a_air;
    - primary_cleaner.state.floatbank8_a_level;
    - primary_cleaner.state.floatbank8_b_air;
    - primary_cleaner.state.floatbank8_b_level;
    - primary_cleaner.state.floatbank8_c_air;
    - primary_cleaner.state.floatbank8_c_level;
    - primary_cleaner.state.floatbank8_d_air;
    - primary_cleaner.state.floatbank8_d_level;
- Параметры продукта:
    - primary_cleaner.output.concentrate_ag;
    - primary_cleaner.output.concentrate_pb;
    - primary_cleaner.output.concentrate_sol;
    - primary_cleaner.output.concentrate_au;
- Параметры отвальных хвостов:
    - primary_cleaner.output.tail_ag;
    - primary_cleaner.output.tail_pb;
    - primary_cleaner.output.tail_sol;
    - primary_cleaner.output.tail_au.

Этап вторичной (финальной) очистки:
- Параметры состояние этапа:
    - secondary_cleaner.state.floatbank2_a_air;
    - secondary_cleaner.state.floatbank2_a_level;
    - secondary_cleaner.state.floatbank2_b_air;
    - secondary_cleaner.state.floatbank2_b_level;
    - secondary_cleaner.state.floatbank3_a_air;
    - secondary_cleaner.state.floatbank3_a_level;
    - secondary_cleaner.state.floatbank3_b_air;
    - secondary_cleaner.state.floatbank3_b_level;
    - secondary_cleaner.state.floatbank4_a_air;
    - secondary_cleaner.state.floatbank4_a_level;
    - secondary_cleaner.state.floatbank4_b_air;
    - secondary_cleaner.state.floatbank4_b_level;
    - secondary_cleaner.state.floatbank5_a_air;
    - secondary_cleaner.state.floatbank5_a_level;
    - secondary_cleaner.state.floatbank5_b_air;
    - secondary_cleaner.state.floatbank5_b_level;
    - secondary_cleaner.state.floatbank6_a_air;
    - secondary_cleaner.state.floatbank6_a_level;
- Параметры отвальных хвостов:
    - secondary_cleaner.output.tail_ag;
    - secondary_cleaner.output.tail_pb;
    - secondary_cleaner.output.tail_sol;
    - secondary_cleaner.output.tail_au;
- Параметры финального продукта:
    - final.output.concentrate_ag;
    - final.output.concentrate_pb;
    - final.output.concentrate_sol;
    - final.output.concentrate_au;
    - final.output.recovery;
- Параметры финальных (накопленных за все этапы) отвальных хвостов:   
    - final.output.tail_ag;
    - final.output.tail_pb;
    - final.output.tail_sol;
    - final.output.tail_au.

**Инструменты и навыки**

Pandas, sklearn, numpy, seaborn, matplotlib, math, машинное обучение.