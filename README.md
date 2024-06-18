//_______________________________________________________________
//________________________О П И С А Н И Е________________________      
(*                                                          
    Данный стек предназначен для анализа и обработки сигналов. 
    Он позволяет отслеживать и контролировать различные аспекты работы системы, включая: 
    длительность сигнала, производительность и временные интервалы между сигналами. 
    Это помогает оптимизировать работу системы и повысить её надёжность.
    Временные интервалы между сигналами позволяют анализировать динамику 
    работы системы и выявлять возможные проблемы или узкие места.
*)
//_______________________________________________________________
//____________________________В В О Д____________________________
//_______________________________________________________________     
                                                      
(*
Per_Min0 (
    PM_Start       := Сигнал_активации,
    PM_Input       := Контролируемый_сигнал,
    PM_Multiplier  := Коэффициент_таймера,
    PM_TimeCycel   => Длительность_сигнала,
    PM_PerMomental => Моментальная_производительность,
    PM_PerMinute   => Производительность_в_минуту,
    PM_PerHour     => Производительность_в_час,
    PM_TimeRTR     => Rising_to_Rising,
    PM_TimeRTE     => Rising_to_End,
    PM_TimeETR     => End_to_Rising,
    PM_TimeETE     => End_to_End,
);

*)
//_______________________________________________________________
//_______________________П Р О Ч И Т А Т Ь_______________________
//_______________________________________________________________
(*
    1.   Сигнал активации — Сигнал, инициирующий работу функционального блока.
    2.   Контролируемый сигнал — сигнал, требующий мониторинга, например, 
         флаг состояния цикла машины или сигнал с датчика.
    3.   Коэффициент таймера — Множитель единицы измерения таймеров от 0 до 2, 
         где 0 соответствует секундному таймеру, 1 — таймеру в 100 мс, а 2 — таймеру в 10 мс. 
         Используется для корреляции полученных временных интервалов.
    4.   Длительность сигнала - Продолжительность текущего сигнала.
    5.   Моментальная производительность - Скорость, определяемая количеством сигналов за одну секунду.
    6.   Производительность в минуту — Среднее количество сигналов за одну минуту.
    7.   Производительность в час — Среднее количество сигналов за один час. 
    8.   Rising to Rising (Интервал нарастания до нарастания ) — 
         Временной промежуток между началом одного сигнала, его спадом и началом следующего сигнала.
    9.   Rising to End (Интервал нарастания до конца) — 
         Временной промежуток между началом одного сигнала, его спадом и концом следующего сигнала.
    10.  End to Rising (Интервал от конца до нарастания) — 
         Временной промежуток между концом одного сигнала и началом следующего сигнала.
    11.  End to End (Интервал от конца до конца) — 
         Временной промежуток между концом одного сигнала и концом следующего сигнала.
        
    *Для корректной работы требуются дополнительные функциональные блоки: DFB_R_TRIG и DFB_F_TRIG0.
*)

//_______________________________________________________________
//_____________________Ц И К Л О Г Р А М М А_____________________
//_______________________________________________________________ 

(*Время цикла - RisingToEnd*)
//     __       __
//____|  |_____|  |_____ (Сигнал)
//     __       __
//____|  |_____|  |_____ (Время)


(*Интервал циклов - RisingToRising*)
//     __       __
//____|  |_____|  |_____ (Сигнал)
//     ________
//____|        |________ (Время)

(*Интервал циклов - EndToEnd*)
//     __       __
//____|  |_____|  |_____ (Сигнал)
//        ________
//_______|        |_____ (Время)


(*Интервал циклов - RisingToEnd*)
//     __       __
//____|  |_____|  |_____ (Сигнал)
//     ___________
//____|           |_____ (Время)


(*Интервал циклов - EndToRising*)
//     __       __
//____|  |_____|  |_____ (Сигнал)
//        _____
//_______|     |________ (Время)
