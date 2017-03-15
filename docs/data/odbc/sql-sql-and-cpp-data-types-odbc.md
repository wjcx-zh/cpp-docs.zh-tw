---
title: "SQL：SQL 和 C++ 資料類型 (ODBC) | Microsoft Docs"
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
  - "資料類型 [C++], SQL 和 C++ 的比較"
  - "SQL [C++], 和 C++ 資料類型的比較"
  - "SQL 資料類型 [C++]"
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL：SQL 和 C++ 資料類型 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本資訊適用於 MFC ODBC 類別。  如果您正在使用 MFC DAO 類別，請參閱《DAO 說明》中的＜比較 Microsoft Jet Database Engine SQL 與 ANSI SQL＞主題。  
  
 下表內容列出了對應至 C\+\+ 資料型別的 ANSI SQL 資料型別。  這補充了在 MSDN Library CD 內《ODBC SDK 程式設計人員參考》的附錄 D 中所提供的 C 語言資訊。  精靈會為您管理大多數的資料型別對應。  若您不要使用精靈，您可使用對應資訊來幫您手動寫入欄位交換程式碼。  
  
### ANSI SQL 資料型別對應至 C\+\+ 資料型別  
  
|ANSI SQL 資料型別|C\+\+ 資料型別|  
|-------------------|----------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**INTEGER**|**long**|  
|**FLOAT**|**double**|  
|**DOUBLE**|**double**|  
|**NUMERIC**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**BIT**|**BOOL**|  
|**TINYINT**|**BYTE**|  
|**BIGINT**|`CString` 1|  
|**BINARY**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATE**|`CTime`, `CString`|  
|**TIME**|**CTime、CString**|  
|**TIMESTAMP**|**CTime、CString**|  
  
 1.  由於 **SQL\_C\_CHAR** 是預設的 ODBC 轉換型別，ANSI **DECIMAL** 和 **NUMERIC** 會對應至 `CString`。  
  
 2.  對應至 `CString` 時，預設情況是超過 255 個字元的字元資料會被截斷。  您可藉由明確地設定 `RFX_Text` 的 `nMaxLength` 引數來擴充截斷長度。  
  
 3.  在對應至 `CByteArray` 時，預設情況是超過 255 個字元的 Binary 資料會被截斷。  您可藉由明確地設定 `RFX_Binary` 的 `nMaxLength` 引數來擴充截斷長度。  
  
 若您不是使用 ODBC 資料指標程式庫 \(Cursor Library\)，則您在嘗試使用 Microsoft SQL Server ODBC 驅動程式和 MFC ODBC 資料庫類別來更新兩個或多個長整數 \(Long\) 的可變長度欄位時，可能會出現問題。  **SQL\_LONGVARCHAR** 和 **SQL\_LONGVARBINARY** 這兩個 ODBC 型別會對應至 SQL Server 型別 text 和 image。  如果您以同樣呼叫至 `CRecordset::Update` 來更新兩個或多個長整數的可變長度欄位時，會擲回 `CDBException`。  因此，請不要同時使用 `CRecordset::Update` 來更新多個長整數的資料行。  您可使用 ODBC API **SQLPutData** 來同時更新多個長整數的資料行。  您也可使用 ODBC 資料指標程式庫，但不建議您用於驅動程式，如 SQL Server 驅動程式，雖然支援指標，但不需要指標程式庫。  
  
 如果您正在 MFC ODBC 資料庫類別與 Microsoft SQL Server ODBC 驅動程式上使用 ODBC 資料指標程式庫，則在呼叫 `CRecordset::Requery` 後又呼叫 `CRecordset::Update` 時，便可能會發生 **ASSERT** 以及 `CDBException`。  因此您須呼叫 `CRecordset::Close` 和 `CRecordset::Open`，而不要呼叫 `CRecordset::Requery`。  其他的方案是不要使用 ODBC 資料指標程式庫，因為 SQL Server 和 SQL Server ODBC 驅動程式原本就有對指標提供原生支援，所以不需要 ODBC 資料指標程式庫。  
  
## 請參閱  
 [SQL](../../data/odbc/sql.md)   
 [SQL：製作直接的 SQL 呼叫 \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)