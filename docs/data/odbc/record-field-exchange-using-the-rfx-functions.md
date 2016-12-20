---
title: "資料錄欄位交換：RFX 函式的使用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料類型 [C++], ODBC 資料錄欄位交換"
  - "DoFieldExchange 方法, 和 RFX 函式"
  - "函式呼叫, RFX 函式"
  - "ODBC [C++], 資料類型"
  - "ODBC [C++], RFX"
  - "RFX (ODBC) [C++], 資料類型"
  - "RFX (ODBC) [C++], 函式語法和參數"
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄欄位交換：RFX 函式的使用
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題說明如何使用構成您的 `DoFieldExchange` 覆寫函式主體的 RFX 函式呼叫。  
  
> [!NOTE]
>  這個主題適用於未實作大量資料列擷取的 [CRecordset](../../mfc/reference/crecordset-class.md) 衍生物件。  如果您要使用大量資料列擷取，就實作大量資料錄欄位交換 \(Bulk RFX\)。  Bulk RFX 類似 RFX。  若要了解兩者間的差異，請參閱[資料錄集：擷取 大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 RFX 全域函式會在資料來源的資料行和您的資料錄集的欄位資料成員間交換資料。  您在資料錄集的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 成員函式內寫入 RFX 函式呼叫。  這個主題簡介說明這個函式，並示範 RFX 函式可用的資料型別。  [技術提示 43](../../mfc/tn043-rfx-routines.md) 說明如何為額外的資料型別撰寫您自己的 RFX 函式。  
  
##  <a name="_core_rfx_function_syntax"></a> RFX 函式語法  
 每個 RFX 函式接受三個參數 \(某些會接受可選擇的第四或第五個參數\)：  
  
-   [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 物件的指標。  您只要將它們與 `pFX` 指標一起傳遞至 `DoFieldExchange`。  
  
-   資料行名稱與出現在資料來源上的相同。  
  
-   資料錄集類別內對應的欄位資料成員或參數資料成員之名稱。  
  
-   \(選擇項\) 在某些函式中，也會傳輸字串或陣列的最大長度。  預設值為 255 個位元組，但您可能想要變更長度。  大小上限是根據 `CString` 物件的大小上限 ─ **INT\_MAX** \(2,147,483,647\) 位元組 ─ 但在此上限前，您將可能遇到驅動程式的限制。  
  
-   \(選擇項\) 在 `RFX_Text` 函式中，您有時會使用第五個參數來指定資料行的資料型別。  
  
 如需詳細資訊，請參閱《類別庫參考手冊》內[巨集和全域變數](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)下的 RFX 函式。  如需您何時可能會想特別使用參數的範例，請參閱文件[資料錄集：取得 SUM 和其他彙總結果 \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)。  
  
##  <a name="_core_rfx_data_types"></a> RFX 資料型別  
 類別庫提供 RFX 函式在資料來源和您的資料錄集間傳輸許多不同的資料型別。  以下的清單按資料型別摘要地列出 RFX 函式。  當您必須撰寫自己的 RFX 函式呼叫時，請按資料型別從這些函式中來選出。  
  
|功能|資料型別|  
|--------|----------|  
|`RFX_Bool`|**BOOL**|  
|`RFX_Byte`|**BYTE**|  
|`RFX_Binary`|`CByteArray`|  
|`RFX_Double`|**double**|  
|`RFX_Single`|**float**|  
|`RFX_Int`|`int`|  
|`RFX_Long`|**long**|  
|`RFX_LongBinary`|`CLongBinary`|  
|`RFX_Text`|`CString`|  
|`RFX_Date`|`CTime`|  
  
 如需詳細資訊，請參閱《類別庫參考》內[巨集和全域變數](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)中的 RFX 函式文件。  如需 C\+\+ 資料型別如何對應至 SQL 資料型別的詳細資訊，請參閱在 [SQL：SQL 和 C\+\+ 資料型別 \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md) 內對應至 C\+\+ 資料型別的 ANSI SQL 資料型別表格。  
  
## 請參閱  
 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)