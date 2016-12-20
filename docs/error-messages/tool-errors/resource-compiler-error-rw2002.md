---
title: "資源編譯器錯誤 RW2002 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2002"
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資源編譯器錯誤 RW2002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

剖析處理錯誤  
  
### 若要修正，請檢查下列可能原因  
  
1.  **需要的快速鍵類型 \(ASCII 或 VIRTKEY\)**  
  
     **ACCELERATORS** 陳述式中的 `type` 欄位必須包含 ASCII 或 VIRTKEY 值。  
  
2.  **快速鍵對應表中必須有 BEGIN**  
  
     **BEGIN** 關鍵字必須緊接在 **ACCELERATORS** 關鍵字的後面。  
  
3.  **對話中必須有 BEGIN**  
  
     **BEGIN** 關鍵字必須緊接在 **DIALOG** 關鍵字的後面。  
  
4.  **功能表中必須有 BEGIN**  
  
     **BEGIN** 關鍵字必須緊接在 **MENU** 關鍵字的後面。  
  
5.  **RCData 中必須有 BEGIN**  
  
     **BEGIN** 關鍵字必須緊接在 **RCDATA** 關鍵字的後面。  
  
6.  **字串資料表中必須有 BEGIN 關鍵字**  
  
     **BEGIN** 關鍵字必須緊接在 **STRINGTABLE** 關鍵字的後面。  
  
7.  **無法重複使用字串常數**  
  
     您在 **STRINGTABLE** 陳述式中使用兩次相同的值，  請確定您未混淆重疊的十進位及十六進位值。  **STRINGTABLE** 中的每項 ID 都必須具有唯一性。  為了達到最高的效率，請使用 16 的倍數開始的連續常數。  
  
8.  **控制字元超出範圍 \[^A \- ^Z\]**  
  
     **ACCELERATORS** 陳述式中的控制字元無效。  跟著插入號 \(**^**\) 後面的字元必須在 A 到 Z 之間 \(含 A 與 Z\)。  
  
9. **不允許空的功能表**  
  
     **END** 關鍵字出現在 **MENU** 陳述式中定義的功能表項目之前。  資源編譯器不允許功能表是空的。  請確定 **MENU** 陳述式中沒有任何左引號。  
  
10. **對話方塊中必須有 END**  
  
     **END** 關鍵字必須出現在 **DIALOG** 陳述式的結尾。  請確定先前陳述式未留下任何左引號。  
  
11. **功能表中必須有 END**  
  
     **END** 關鍵字必須出現在 **MENU** 陳述式的結尾。  請確定沒有任何左引號或是 **BEGIN** 和 **END** 陳述式中無法對應的配對。  
  
12. **快速鍵對應表中必須有逗號**  
  
     在資源編譯器的 **ACCELERATORS** 陳述式中，`event` 和 *idvalue* 兩欄位之間必須有逗號。  
  
13. **必須是控制項類別名稱**  
  
     **DIALOG** 陳述式中 **CONTROL** 陳述式的 `class` 欄位必須是下列其中一種類型：BUTTON、COMBOBOX、EDIT、LISTBOX、SCROLLBAR、STATIC 或使用者自訂。  請確定類別的拼字正確。  
  
14. **必須是字體名稱**  
  
     **DIALOG** 陳述式中 FONT 選項的 *typeface* 欄位必須是以雙引號括住的 ASCII 字元字串。  這個欄位指定字型的名稱。  
  
15. **功能表項目必須有 ID 值**  
  
     **MENU** 陳述式必須包含 *menuID* 欄位，能夠指定用來識別功能表資源的名稱或號碼。  
  
16. **必須是功能表字串**  
  
     每項 **MENUITEM** 和 **POPUP** 陳述式都必須包含 *text* 欄位，也就是能夠指定功能表項目或快顯功能表名稱且以雙引號括住的字串。  **MENUITEM SEPARATOR** 陳述式不需要以引號括住的字串。  
  
17. **必須是數字命令值**  
  
     資源編譯器在 **ACCELERATORS** 陳述式中必須有數字 *idvalue* 欄位。  請確定是使用 `#define` 常數來指定此值，且常數的拼字正確。  
  
18. **字串資料表中必須有數字常數**  
  
     在 `#define` 陳述式中定義的數字常數必須緊接在 **STRINGTABLE** 陳述式中 **BEGIN** 關鍵字的後面。  
  
19. **必須是數字點數大小**  
  
     **DIALOG** 陳述式中 FONT 選項的 *pointsize* 欄位必須是整數值的點數。  
  
20. **必須有數值對話常數**  
  
     **DIALOG** 陳述式在 *x*、*y*、寬度 \(width\) 和高度 \(height\) 欄位需要整數值。  請確定 **DIALOG** 關鍵字之後已包含有這些數值，而且必須為正值。  
  
21. **STRINGTABLE 中必須是字串**  
  
     **STRINGTABLE** 陳述式中每項 *stringid* 值之後都必須接著字串。  
  
22. **必須是字串或常數快速鍵命令**  
  
     資源編譯器無法判斷設定快速鍵的索引鍵種類。  **ACCELERATORS** 陳述式中的 `event` 欄位可能無效。  
  
23. **ID 必須是數字**  
  
     **DIALOG** 陳述式中控制項陳述式的 `id` 欄位必須有數字。  請確定控制項 ID 具有數字或 `#define` 陳述式。  
  
24. **對話方塊類別中必須是以引號括住的字串**  
  
     **DIALOG** 陳述式中 CLASS 選項的 `class` 欄位必須是以雙引號括住的整數或字串。  
  
25. **對話方塊標題必須是以引號括住的字串**  
  
     **DIALOG** 陳述式中 CAPTION 選項的 `captiontext` 欄位必須是以雙引號括住的 ASCII 字元字串。  
  
26. **找不到檔案：檔名**  
  
     找不到資源編譯器命令列中指定的檔案。  請檢查檔案是否移到其他目錄，以及是否輸入正確的檔名或路徑。  可能的話，使用 **INCLUDE** 環境變數或 Visual Workbench 設定來搜尋檔案。  
  
27. **字型名稱必須是序數**  
  
     FONT 陳述式中的 *pointsize* 欄位必須是整數，而非字串。  
  
28. **無效的快速鍵**  
  
     無法辨認 **ACCELERATORS** 陳述式中的 `event` 欄位，或是長度超過兩個字元。  
  
29. **無效的快速鍵類型 \(ASCII 或 VIRTKEY\)**  
  
     **ACCELERATORS** 陳述式中的 `type` 欄位必須包含 ASCII 或 VIRTKEY 值。  
  
30. **無效的控制字元**  
  
     **ACCELERATORS** 陳述式中的控制字元無效。  有效的控制字元是由 \(僅限\) 單一字母跟隨著插入號 \(^\) 所組成。  
  
31. **無效的控制項型別**  
  
     **DIALOG** 陳述式中的每一個項控制項陳述式必須是下列其中一項：CHECKBOX、COMBOBOX、CONTROL、CTEXT、DEFPUSHBUTTON、EDITTEXT、GROUPBOX、ICON、LISTBOX、LTEXT、PUSHBUTTON、RADIOBUTTON、RTEXT、SCROLLBAR。  請確定這些控制項陳述式的拼字正確。  
  
32. **無效的類型**  
  
     資源類型不在 WINDOWS.h 檔案所定義的類型當中。  
  
33. **控制項中必須有文字字串或序數**  
  
     **DIALOG** 陳述式中 **CONTROL** 陳述式的 *text* 欄位必須是參考控制類型的文字字串或序數。  若使用序數，請確定控制項具有 `#define` 陳述式。  
  
34. **無對應的括號**  
  
     請確定 **DIALOG** 陳述式中的每個左括號都有對應的右括號。  
  
35. **RCData 中出現未預期的值**  
  
     **RCDATA** 陳述式中的 *raw\-data* 值必須是以逗號分隔的整數或字串。  請確定您沒有遺漏逗號或者遺漏字串前後的引號。  
  
36. **未知的功能表子型別**  
  
     **MENU** 陳述式的 *item\-definition* 欄位只能包含 **MENUITEM** 和 **POPUP** 陳述式。