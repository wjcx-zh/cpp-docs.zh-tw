---
title: "CFieldExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFieldExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFieldExchange class"
  - "資料型別 [C++], 自訂"
  - "enum FieldType"
  - "enum FieldType, CFieldExchange"
  - "FieldType enumeration"
  - "RFX (record field exchange) [C++]"
  - "RFX (record field exchange) [C++], classes for"
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CFieldExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援資料錄欄位交換 \(RFX\)，並且大量資料錄欄位資料庫使用的交換 \(Bulk RFX\) 常式分類。  
  
## 語法  
  
```  
  
class CFieldExchange  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFieldExchange::IsFieldType](../Topic/CFieldExchange::IsFieldType.md)|目前作業，則為，更新的欄位的型別為適當的傳回非零。|  
|[CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md)|指定資料錄集的所有後續的呼叫內資料行或參數—所表示之資料成員的型別設定為 RFX 函式直到下一次呼叫 `SetFieldType`。|  
  
## 備註  
 `CFieldExchange` 不具有基底類別。  
  
 請使用這個類別中，如果您為自訂資料型別寫入資料交換常式，或當您實作大量資料列擷取時，否則，您不會直接使用這個類別。  RFX 和 Bulk RFX 交換資料在資料錄集物件的欄位資料成員和目前資料錄的對應欄位之間的資料來源。  
  
> [!NOTE]
>  如果您使用存取資料時使用物件 \(DAO\) 類別而不是開放式資料庫連接 \(ODBC\) 類別會使用類別， [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) 。  如需詳細資訊，請參閱本文 [概觀: 資料庫程式開發](../../data/data-access-programming-mfc-atl.md)。  
  
 `CFieldExchange` 物件為資料錄欄位交換或大量資料錄欄位交換提供所需的內容資訊時發生。  `CFieldExchange` 物件支援許多作業，包括內建參數和欄位資料成員和設定各種旗標在目前資料錄的欄位。  RFX 和 Bulk RFX 作業在資料錄集類別 `enum`定義型別的資料成員會執行**FieldType** 在 `CFieldExchange`。  **FieldType** 可能的值為:  
  
-   欄位資料成員的**CFieldExchange::outputColumn** 。  
  
-   **CFieldExchange::inputParam** 或 **CFieldExchange::param** 輸入參數資料成員。  
  
-   輸出參數資料成員的**CFieldExchange::outputParam** 。  
  
-   輸入\/輸出參數資料成員的**CFieldExchange::inoutParam** 。  
  
 大部分類別的成員函式和資料成員是您開始撰寫自訂 RFX 常式提供。  您最常使用 `SetFieldType` 。  如需詳細資訊，請參閱 Microsoft 知識庫文件 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md) 和 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)。  如需大量資料列擷取的詳細資訊，請參閱本文 [資料錄集:擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  如需 RFX 和 Bulk RFX 全域函式的詳細資訊，請參閱此參考的 MFC 巨集和全域部分的 [資料錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md) 。  
  
## 繼承階層架構  
 `CFieldExchange`  
  
## 需求  
 **Header:** afxdb.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)