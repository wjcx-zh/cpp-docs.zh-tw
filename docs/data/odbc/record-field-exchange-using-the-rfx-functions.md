---
title: "資料錄欄位交換： RFX 函式的使用 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a270b26fc0fd9be721ee0656f9f0d14ab579b477
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>資料錄欄位交換：RFX 函式的使用
本主題說明如何使用 RFX 函式呼叫的主體構成您`DoFieldExchange`覆寫。  
  
> [!NOTE]
>  本主題適用於衍生自類別[CRecordset](../../mfc/reference/crecordset-class.md)的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，被實作大量資料錄欄位交換 (Bulk RFX)。 大量 RFX 與 RFX 相似。 若要了解的差異，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 RFX 全域函式會交換資料錄集中的資料來源和欄位資料成員的資料行之間的資料。 您可以撰寫 RFX 函式呼叫中資料錄集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成員函式。 本主題簡要描述函式，並顯示哪些 RFX 函式可以使用的資料類型。 [技術提示 43](../../mfc/tn043-rfx-routines.md)說明如何撰寫您自己 RFX 函式的其他資料類型。  
  
##  <a name="_core_rfx_function_syntax"></a>RFX 函式語法  
 每個 RFX 函式接受三個參數 （和一些接受選擇性的第四個或第五個參數）：  
  
-   指標[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件。 您只需傳遞沿著`pFX`指標傳遞至`DoFieldExchange`。  
  
-   因為它的資料行名稱會出現在資料來源。  
  
-   對應的欄位資料成員或資料錄集類別中的參數資料成員的名稱。  
  
-   （選擇性）在某些函式、 字串或陣列所傳輸的最大長度。 預設值為 255 個位元組，但您可能想要變更它。 大小上限為基礎的最大大小`CString`物件 — **INT_MAX** (2,147,483,647) 個位元組，但您可能會遇到驅動程式的限制。  
  
-   （選擇性）在`RFX_Text`函式，您有時使用第五個參數來指定資料行的資料類型。  
  
 如需詳細資訊，請參閱 RFX 函式下的[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)中*類別庫參考*。 如需當您可能會建立特殊的範例使用的參數，請參閱[資料錄集： 取得 Sum 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)。  
  
##  <a name="_core_rfx_data_types"></a>RFX 資料類型  
 類別庫提供 RFX 函式的資料來源和您的資料錄集之間傳送許多不同的資料類型。 下列清單摘要說明 RFX 函式的資料型別。 在您必須撰寫您自己 RFX 函式呼叫的情況下，選取從資料類型的這些函式。  
  
|功能|資料類型|  
|--------------|---------------|  
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
  

 如需詳細資訊，請參閱底下的 RFX 函式文件[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)中*類別庫參考*。 如需 c + + 資料類型如何對應至 SQL 資料類型資訊，請參閱 < ANSI SQL 資料類型對應至 c + + 資料類型的資料表中[SQL: SQL 和 c + + 資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)