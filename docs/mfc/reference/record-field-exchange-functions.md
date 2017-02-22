---
title: "資料錄欄位交換函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO (資料存取物件), 資料錄欄位交換 (DFX)"
  - "ODBC, Bulk RFX 資料交換函式"
  - "RFX (資料錄欄位交換), ODBC 類別"
  - "DFX (DAO 資料錄欄位交換), 資料交換函式"
  - "DFX 函式"
  - "大量 RFX 函式"
  - "DFX (DAO 資料錄欄位交換)"
  - "RFX (資料錄欄位交換), DAO 類別"
  - "ODBC, RFX"
  - "RFX (資料錄欄位交換), 資料交換函式"
  - "RFX (資料錄欄位交換)"
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 資料錄欄位交換函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題列出資料錄欄位交換 \([RFX](#_mfc_rfx_functions_.28.odbc.29)、[Bulk RFX](#_mfc_bulk_rfx_functions_.28.odbc.29) 和 [DFX](#_mfc_dfx_functions_.28.dao.29)\) 函式，您可以使用這些函式將資料錄集物件與其資料來源之間的資料傳輸自動化，並對資料執行其他作業。  
  
 如果您使用 ODBC 類別並已實作大量資料列擷取，您必須針對對應至資料來源資料行的每個資料成員呼叫 Bulk RFX 函式，以手動方式覆寫 `CRecordset` 的 `DoBulkFieldExchange` 成員函式。  
  
 如果您未在 ODBC 類別中實作大量資料列擷取，或是使用 DAO 類別，則 ClassWizard 會為資料錄集中的每個欄位資料成員呼叫 RFX 函式 \(適用於 ODBC 類別\) 或 DFX 函式 \(適用於 DAO 類別\)，以覆寫 `CRecordset` 或 `CDaoRecordset` 的 `DoFieldExchange` 成員函式。  
  
 每次架構呼叫 `DoFieldExchange` 或 `DoBulkFieldExchange` 時，資料錄欄位交換函式都會傳輸資料。 每個函式會傳輸特定資料類型。  
  
 如需這些函式使用方式的詳細資訊，請參閱[資料錄欄位交換：RFX 的運作方式 \(ODBC\)](../../data/odbc/record-field-exchange-how-rfx-works.md) 一文。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 一文。  
  
 針對您動態繫結的資料行，您也可以自行呼叫 RFX 或 DFX 函式，如[資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) 一文中所述。 此外，您可以撰寫自己的自訂 RFX 或 DFX 常式，如技術提示 [43](../../mfc/tn043-rfx-routines.md) \(適用於 ODBC\) 和技術提示 [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) \(適用於 DAO\) 中所述。  
  
 如需 RFX 和 Bulk RFX 函式顯示在 `DoFieldExchange` 和 `DoBulkFieldExchange` 函式中的範例，請參閱 [RFX\_Text](../Topic/RFX_Text.md) 和 [RFX\_Text\_Bulk](../Topic/RFX_Text_Bulk.md)。 DFX 函式與 RFX 函式很類似。  
  
### RFX 函式 \(ODBC\)  
  
|||  
|-|-|  
|[RFX\_Binary](../Topic/RFX_Binary.md)|傳輸 [CByteArray](../../mfc/reference/cbytearray-class.md) 類型的位元組陣列。|  
|[RFX\_Bool](../Topic/RFX_Bool.md)|傳輸布林值資料。|  
|[RFX\_Byte](../Topic/RFX_Byte.md)|傳輸資料的單一位元組。|  
|[RFX\_Date](../Topic/RFX_Date.md)|傳輸使用 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 或 **TIMESTAMP\_STRUCT** 的時間和日期資料。|  
|[RFX\_Double](../Topic/RFX_Double.md)|傳輸雙精確度浮點數資料。|  
|[RFX\_Int](../Topic/RFX_Int.md)|傳輸整數資料。|  
|[RFX\_Long](../Topic/RFX_Long.md)|傳輸長整數資料。|  
|[RFX\_LongBinary](../Topic/RFX_LongBinary.md)|傳輸物件類別為 [CLongBinary](../../mfc/reference/clongbinary-class.md) 的二進位大型物件 \(BLOB\) 資料。|  
|[RFX\_Single](../Topic/RFX_Single.md)|傳輸浮點數資料。|  
|[RFX\_Text](../Topic/RFX_Text.md)|傳輸字串資料。|  
  
### Bulk RFX 函式 \(ODBC\)  
  
|||  
|-|-|  
|[RFX\_Binary\_Bulk](../Topic/RFX_Binary_Bulk.md)|傳輸位元組資料陣列。|  
|[RFX\_Bool\_Bulk](../Topic/RFX_Bool_Bulk.md)|傳輸布林值資料陣列。|  
|[RFX\_Byte\_Bulk](../Topic/RFX_Byte_Bulk.md)|傳輸單一位元組陣列。|  
|[RFX\_Date\_Bulk](../Topic/RFX_Date_Bulk.md)|傳輸 **TIMESTAMP\_STRUCT** 類型的資料陣列。|  
|[RFX\_Double\_Bulk](../Topic/RFX_Double_Bulk.md)|傳輸雙精確度浮點數資料陣列。|  
|[RFX\_Int\_Bulk](../Topic/RFX_Int_Bulk.md)|傳輸整數資料陣列。|  
|[RFX\_Long\_Bulk](../Topic/RFX_Long_Bulk.md)|傳輸長整數資料陣列。|  
|[RFX\_Single\_Bulk](../Topic/RFX_Single_Bulk.md)|傳輸浮點數資料陣列。|  
|[RFX\_Text\_Bulk](../Topic/RFX_Text_Bulk.md)|傳輸 **LPSTR** 類型的資料陣列。|  
  
### DFX 函式 \(DAO\)  
  
|||  
|-|-|  
|[DFX\_Binary](../Topic/DFX_Binary.md)|傳輸 [CByteArray](../../mfc/reference/cbytearray-class.md) 類型的位元組陣列。|  
|[DFX\_Bool](../Topic/DFX_Bool.md)|傳輸布林值資料。|  
|[DFX\_Byte](../Topic/DFX_Byte.md)|傳輸資料的單一位元組。|  
|[DFX\_Currency](../Topic/DFX_Currency.md)|傳輸 [COleCurrency](../../mfc/reference/colecurrency-class.md) 類型的貨幣資料。|  
|[DFX\_DateTime](../Topic/DFX_DateTime.md)|傳輸 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 類型的時間和日期資料。|  
|[DFX\_Double](../Topic/DFX_Double.md)|傳輸雙精確度浮點數資料。|  
|[DFX\_Long](../Topic/DFX_Long.md)|傳輸長整數資料。|  
|[DFX\_LongBinary](../Topic/DFX_LongBinary.md)|傳輸物件類別為 `CLongBinary` 的二進位大型物件 \(BLOB\) 資料。 若是 DAO，建議您改用 [DFX\_Binary](../Topic/DFX_Binary.md)。|  
|[DFX\_Short](../Topic/DFX_Short.md)|傳輸短整數資料。|  
|[DFX\_Single](../Topic/DFX_Single.md)|傳輸浮點數資料。|  
|[DFX\_Text](../Topic/DFX_Text.md)|傳輸字串資料。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)   
 [CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)   
 [CRecordset::DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)   
 [CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md)