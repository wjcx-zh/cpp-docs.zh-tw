---
title: "資料錄欄位交換：RFX 的使用 | Microsoft Docs"
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
  - "RFX (ODBC), 實作"
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄欄位交換：RFX 的使用
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題會說明以架構使用 RFX 的方式，您應如何使用 RFX。  
  
> [!NOTE]
>  這個主題適用於未實作大量資料列擷取的 [CRecordset](../../mfc/reference/crecordset-class.md) 衍生物件。  如果您要使用大量資料列擷取，就實作大量資料錄欄位交換 \(Bulk RFX\)。  Bulk RFX 類似 RFX。  若要了解兩者間的差異，請參閱[資料錄集：擷取 大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 下列主題包含相關資訊：  
  
-   [資料錄欄位交換：精靈程式碼的使用](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)介紹 RFX 的主要元件並說明 MFC 應用程式精靈和加入類別  \(如[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所說明的\) 所寫入來支援 RFX 的程式碼，以及如何修改精靈程式碼。  
  
-   [資料錄欄位交換：RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)說明如何寫入對 `DoFieldExchange` 覆寫函式中 RFX 函式的呼叫。  
  
 下表說明關於架構為您做的事，您的角色是什麼。  
  
### RFX 的使用：您與架構  
  
|您|架構|  
|-------|--------|  
|使用精靈來宣告您的資料錄集類別。  指定欄位資料成員的名稱和資料型別。|精靈會為您衍生 `CRecordset` 類別並寫入 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 覆寫，包括每個欄位資料成員的 RFX 函式呼叫。|  
|\(選擇項\) 手動將任何需要的參數資料成員加入至類別。  手動為每個參數資料成員 \(Parameter Data Member\) 加入 `DoFieldExchange` 的 RFX 函式呼叫，為參數的群組加入對 [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md) 的呼叫，並在 [m\_nParams](../Topic/CRecordset::m_nParams.md) 內指定參數的總數。  請參閱[資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。||  
|\(選擇項\) 手動繫結額外的資料行至欄位資料成員。  手動地遞增 [m\_nFields](../Topic/CRecordset::m_nFields.md)。  請參閱[資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||  
|建構資料錄集類別的物件。  使用此物件前，若有參數資料成員的值則加以設定。|為了顧及效率，架構會使用 ODBC 預先繫結參數。  當您傳遞參數值，架構會將其傳給資料來源。  除非排序和 \(或\) 篩選條件字串 \(String\) 有變動，否則只會傳送要查詢的參數值。|  
|使用 [CRecordset::Open](../Topic/CRecordset::Open.md) 來開啟資料錄集物件。|執行資料錄集的查詢、繫結資料行至資料錄集的欄位資料成員，並呼叫 `DoFieldExchange` 在第一個選擇的資料錄和資料錄集的欄位資料成員間交換資料。|  
|使用 [CRecordset::Move](../Topic/CRecordset::Move.md) 或功能表或工具列命令來捲動資料錄集。|呼叫 `DoFieldExchange` 以便從目前新增的資料錄傳輸資料至欄位資料成員。|  
|加入、更新和刪除資料錄。|呼叫 `DoFieldExchange` 來傳輸資料至資料來源。|  
  
## 請參閱  
 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [資料錄集：取得 SUM 和其他彙總結果 \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [巨集、全域函式和全域變數](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)