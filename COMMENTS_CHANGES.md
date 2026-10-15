# Исправление и добавление номеров в комментариях GlobalVariables.txt

Область: только переменные с Retain = True (967 шт.). Номера сверялись с масками экранов (`Interfaces/OSSTDmCHBE/Device1/Terminal2/*.otws`).
Номер на экране привязывался к переменной, стоящей на той же строке маски, а если на строке с номером переменной нет, то к переменной строкой ниже.

Итого изменено 50 строк: 5 исправлений неверных номеров и 45 добавлений недостающих. Остальной файл не тронут.

## 1. Исправлены неверные номера (5)

| Строка файла | Переменная | Было | Стало | Экран |
|---|---|---|---|---|
| 9 | GlbAlrm_Logic | A053 | A076 | A_Plant / S_DOutLogicP8 |
| 766 | RemAlrmDin_Logic | A046 | A066 | A_Plant / S_DInLogicP1 |
| 903 | UnitOnOffDin_Logic | A048 | A067 | A_Plant / S_DInLogicP3 |
| 5630 | Temp_Fun1_diff | E70b | E070b | E_Source / M_SourceFanType_OnOff_1 |
| 6465 | Temp_Fun2_diff | E70d | E070d | E_Source / M_SourceFanType_OnOff_2 |

## 2. Добавлены номера (45)

Если комментарий был, номер дописан в начало в формате `Номер - текст`. Если комментарий был пустой, записан только номер.

С текстом (24):
- Смещения датчиков (`*.Offset`): SuctTempPrb_Circ1..4 (Ca37, Ca39, Ca37a, Ca39a), DscgTempPrb_Circ1..4 (Ca36, Ca38, Ca36a, Ca38a), DscgP_Prb_Circ1..4 (Ca41, Ca44, Ca41a, Ca44a), SuctP_Prb_Circ1..4 (Ca42, Ca45, Ca42a, Ca45a), ExtTempPrb (E056).
- BmsOnOff_En (Ge16), En_BMS_PwrReq (Ge17), SrcFanNo (E091), DfrSmartStartT (E077).
- SrcFan2Circ1HrsThrsh (E006b), SrcFan2Circ2HrsThrsh (E084), SrcFan3Circ2HrsThrsh (E086).

Только номер, комментарий был пустой (21):
- BACnet_ID (Ge22), Oil_Separator_Heat_Circ1..4.Manual (Ca81a..d).
- Ch_Min_def[63..70] (Ca54a, Ca57a, Ca54b, Ca57b, Ca54c, Ca57c, Ca54d, Ca57d).
- Ch_Max_def[63..70] (Ca55a, Ca58a, Ca55b, Ca58b, Ca55c, Ca58c, Ca55d, Ca58d).

## 3. Не добавлено, чтобы не получить дубль (5)

| Переменная | Номер на экране | Причина |
|---|---|---|
| W_InTempUserPrb.Offset | A063 | A063 уже в комментарии En_FC |
| SrcFan3Circ1HrsThrsh | E082 | E082 уже в комментарии SrcFanCirc3Circ4HrsThrsh |
| SrcFlwSw_Din.Logic | E059 | E059 уже в комментарии SrcFlwSw_Logic |
| SrcFan2Circ3HrsThrsh | E084 | на экране те же номера, что у контура 2 (копия маски) |
| SrcFan3Circ3HrsThrsh | E086 | то же |

## 4. Не менялось, нужно ваше решение

| Переменная | Комментарий сейчас | Номер на экране | Почему |
|---|---|---|---|
| Comp1Circ2HrsThrsh | Ca06 | Ca04 | Ca04 уже занят Comp3Circ1HrsThrsh; для контура 2 по порядку Ca06, Ca08, Ca10 |
| Comp2Circ2HrsThrsh | Ca08 | Ca06 | то же |
| W_OutTempUserPrb.Offset | без номера | A064 и A053 | на двух экранах разные номера |
| STD_UOM_ZONE_UI | Gb00 | десятки экранов | служебная переменная |

Номера A066 и A067 теперь у двух переменных: у цифровых входов (по экрану) и у переменных Freecooling (User_Sp_Fc, Min_T_Ext_ComprOff). Те переменные ни на одном экране не показаны, поэтому их номера проверить нельзя.

Ещё около 740 retain-переменных не показаны на экранах с номером или не показаны вообще. Их комментарии остались без изменений.
