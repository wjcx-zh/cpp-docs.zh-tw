---
title: "資源編譯器錯誤 RW2002 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW2002
dev_langs:
- C++
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db322791c3804f387c452b3839260826585a2e30
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rw2002"></a>資源編譯器錯誤 RW2002
剖析錯誤  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  **快速鍵類型所需 （ASCII 或 VIRTKEY）**  
  
     `type` ACCELERATORS **陳述式中的** 欄位必須包含 ASCII 或 VIRTKEY 值。  
  
2.  **快速鍵對應表中預期為 BEGIN**  
  
     **BEGIN** 關鍵字必須緊接在 **ACCELERATORS** 關鍵字之後。  
  
3.  **在對話方塊中預期為 BEGIN**  
  
     **開始**關鍵字必須緊接**對話方塊**關鍵字。  
  
4.  **在功能表中預期為 BEGIN**  
  
     **BEGIN** 關鍵字必須緊接在 **MENU** 關鍵字之後。  
  
5.  **RCData 中預期為 BEGIN**  
  
     **BEGIN** 關鍵字必須緊接在 **RCDATA** 關鍵字之後。  
  
6.  **字串資料表中必須要有 BEGIN 關鍵字**  
  
     **開始**關鍵字必須緊接**STRINGTABLE**關鍵字。  
  
7.  **無法重新使用字串常數**  
  
     您要使用相同的值在兩次**STRINGTABLE**陳述式。 請確定您未混淆重疊的十進位和十六進位值。 在每個識別碼**STRINGTABLE**必須是唯一的。 最大效率，使用連續的常數，以開始 16 的倍數。  
  
8.  **控制字元超出範圍 [^ A-^ Z]**  
  
     **ACCELERATORS** 陳述式中的控制字元無效。 插入號 (**^**) 後的字元必須介於 A 與 Z (含) 之間。  
  
9. **不允許空的功能表**  
  
     **結束**關鍵字出現在定義所有功能表項目之前**功能表**陳述式。 資源編譯器不允許空的功能表。 請確定您沒有任何開啟的引號內**功能表**陳述式。  
  
10. **在對話方塊中預期為 END**  
  
     **結束**關鍵字必須發生在結尾**對話方塊**陳述式。 請確定任何先前陳述式左引號。  
  
11. **在功能表中預期為 END**  
  
     **END** 關鍵字必須放在 **MENU** 陳述式結尾。 請確定您沒有不完整的引號或不成對的 **BEGIN** 和 **END** 陳述式。  
  
12. **在快速鍵對應表中必須要有的逗號**  
  
     資源編譯器需要 `event` ACCELERATORS *陳述式的* 與 **idvalue** 欄位之間有一個逗號。  
  
13. **預期的控制項類別名稱**  
  
     `class`欄位**控制項**陳述式中的**對話方塊**陳述式必須是下列類型之一： 按鈕、 下拉式方塊、 編輯、 清單方塊、 捲軸、 靜態，或使用者定義。 請確定類別的拼法正確。  
  
14. **預期的字體名稱**  
  
     *DIALOG* 陳述式中 FONT 選項的 **typeface** 欄位必須是以雙引號括住的 ASCII 字串。 此欄位指定字型的名稱。  
  
15. **功能表項目預期的識別碼值**  
  
     **MENU** 陳述式必須包含 *menuID* 欄位，指定識別功能表資源的名稱或數字。  
  
16. **必須是的功能表字串**  
  
     每個 **MENUITEM** 和 **POPUP** 陳述式皆必須包含「文字」  欄位，該欄位為以雙引號括住並指定功能表項目或快顯功能表名稱的字串。 A **MENUITEM 分隔符號**陳述式需要沒有加上引號的字串。  
  
17. **必須是數字命令值**  
  
     資源編譯器需要數值*idvalue*欄位**加速器**陳述式。 請確定您已使用`#define`常數，以指定的值和常數的拼字正確。  
  
18. **字串資料表中必須是數值常數**  
  
     數值常數，定義在 `#define` 陳述式中，必須緊接在 **STRINGTABLE** 陳述式的 **BEGIN** 關鍵字之後。  
  
19. **必須是數值點數大小**  
  
     *DIALOG* 陳述式之字型選項的 [點數大小]  欄位必須是整數點大小值。  
  
20. **必須是數值對話常數**  
  
     A**對話方塊**陳述式會需要整數值*x、 y、 寬度*，和*高度*欄位。 請確定這些值都會包含在之後**對話方塊**關鍵字，而且它們不是負數。  
  
21. **STRINGTABLE 中必須是的字串**  
  
     在 *STRINGTABLE* 陳述式中的每個 **stringid** 值後面必須是字串。  
  
22. **必須是的字串或常數快速鍵命令**  
  
     資源編譯器無法判斷為加速器所設定的按鍵類型。 `event` ACCELERATORS **陳述式中的** 欄位可能無效。  
  
23. **識別碼必須是數字**  
  
     必須是數字作為`id`欄位中的控制陳述式**對話方塊**陳述式。 請確定您有數字或`#define`陳述式的控制項 id。  
  
24. **在對話方塊類別中必須要有加上引號的字串**  
  
     `class` DIALOG **陳述式中 CLASS 選項的** 欄位必須是以雙引號括住的整數或字串。  
  
25. **對話方塊標題中必須要有加上引號的字串**  
  
     `captiontext` DIALOG **陳述式中 CAPTION 選項的** 欄位必須是以雙引號括住的 ASCII 字串。  
  
26. **找不到檔案： filename**  
  
     找不到資源編譯器命令列中所指定的檔案。 請確認是否已將檔案移至另一個目錄，以及是否正確地輸入檔名或路徑。 搜尋檔案使用**INCLUDE**環境變數或 [Visual Workbench] 設定，如果有的話。  
  
27. **字型名稱必須是序數**  
  
     *Pointsize*字型陳述式中的欄位必須是整數，而不是字串。  
  
28. **無效的快速鍵**  
  
     `event` ACCELERATORS **陳述式中的** 欄位無法辨識，或長度超過兩個字元。  
  
29. **無效的快速鍵類型 （ASCII 或 VIRTKEY）**  
  
     `type` ACCELERATORS **陳述式中的** 欄位必須包含 ASCII 或 VIRTKEY 值。  
  
30. **無效的控制字元**  
  
     **ACCELERATORS** 陳述式中的控制字元無效。 有效的控制字元 （僅限） 隨著插入號 (^) 的一個字母所組成。  
  
31. **無效的控制項類型**  
  
     在每個控制項陳述式**對話方塊**陳述式必須是下列其中之一： 核取方塊、 下拉式方塊、 控制項、 SYSCOMMENTS、 DEFPUSHBUTTON、 EDITTEXT、 GROUPBOX、 圖示、 清單方塊、 LTEXT、 按鈕、 選項按鈕、 RTEXT、 捲軸。 請確定這些控制陳述式的拼寫正確。  
  
32. **無效的類型**  
  
     資源類型不是在 WINDOWS.h 檔案中定義的型別之間。  
  
33. **文字字串或序數控制項中必須有**  
  
     *文字*欄位**控制項**陳述式中的**對話方塊**陳述式必須是文字字串或序數參考的控制項類型。 如果使用序數，請確定控制項具有 `#define` 陳述式。  
  
34. **不相符的括號**  
  
     請確定您關閉每個左括弧**對話方塊**陳述式。  
  
35. **RCData 中預期的值**  
  
     *RCDATA* 陳述式中的 **raw-data** 值必須是整數或字串，並以逗號區隔。 請確定您未遺漏逗號或字串周圍的引號。  
  
36. **未知的功能表子類型**  
  
     *項目定義*欄位**功能表**陳述式只能包含**MENUITEM**和**快顯**陳述式。