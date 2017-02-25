---
title: "CDaoFieldExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoFieldExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoFieldExchange class"
  - "DAO (資料存取物件), record field exchange (DFX)"
  - "DFX (DAO 資料錄欄位交換)"
  - "DFX (DAO 資料錄欄位交換), DAO Record Field Exchange"
  - "exchanging data between databases and recordsets"
  - "field exchange"
  - "field exchange, record for DAO classes"
  - "RFX (資料錄欄位交換)"
  - "RFX (資料錄欄位交換), DAO 類別"
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDaoFieldExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 \(DFX\) 常式。  
  
## 語法  
  
```  
class CDaoFieldExchange  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDaoFieldExchange::IsValidOperation](../Topic/CDaoFieldExchange::IsValidOperation.md)|目前作業，則為，更新的欄位的型別為適當的傳回非零。|  
|[CDaoFieldExchange::SetFieldType](../Topic/CDaoFieldExchange::SetFieldType.md)|指定資料錄集的所有後續呼叫—資料行或參數—所表示之資料成員的型別設定為 DFX 作用直到下一次呼叫 `SetFieldType`。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDaoFieldExchange::m\_nOperation](../Topic/CDaoFieldExchange::m_nOperation.md)|目前呼叫執行的 DFX 作業至資料錄集的成員函式。 `DoFieldExchange`|  
|[CDaoFieldExchange::m\_prs](../Topic/CDaoFieldExchange::m_prs.md)|對 DFX 作業的資料錄集的指標。|  
  
## 備註  
 `CDaoFieldExchange` 不具有基底類別。  
  
 如果您為自訂資料型別，寫入資料交換常式中使用這個類別，否則，您不會直接使用這個類別。  在您的 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) DFX 物件的欄位資料成員和目前資料錄的對應的欄位之間交換資料來源的。  DFX 處理以便在兩個方向，從資料來源和資料來源。  如需撰寫自訂 DFX 常式的詳細資訊，請參閱 [Technical Note 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) 。  
  
> [!NOTE]
>  DAO 資料庫類別會根據 Open 開放式資料庫連接的 MFC 資料庫類別本身不同 \(ODBC\)。  所有 DAO 資料庫類別名稱中有「CDao」前置詞。  您仍然可以存取使用 DAO 類別的 ODBC 資料來源。  一般而言，根據的 MFC DAO 類別比 ODBC 架構的 MFC 類別的功能。  以 DAO 類別的類別可以存取資料，包括透過 ODBC 驅動程式，將它們自己的資料庫引擎。  透過類別也支援資料定義語言 \(DDL\) \(DDL\) 作業，例如將資料表而不必呼叫 DAO。  
  
> [!NOTE]
>  DAO 資料錄欄位交換 \(DFX\) 非常類似於資料錄欄位交換 \(RFX\) 在 ODBC 架構的 MFC 資料庫類別 \(`CDatabase`， `CRecordset`\)。  如果您了解 RFX，您會發現易用的 DFX。  
  
 `CDaoFieldExchange` 物件針對 DAO 資料錄欄位交換提供所需的內容資訊時發生。  `CDaoFieldExchange` 物件支援許多作業，包括內建參數和欄位資料成員和設定各種旗標在目前資料錄的欄位。  DFX 作業在資料錄集類別 `enum`定義型別的資料成員會執行**FieldType** 在 `CDaoFieldExchange`。  **FieldType** 可能的值為:  
  
-   欄位資料成員的**CDaoFieldExchange::outputColumn** 。  
  
-   參數資料成員的**CDaoFieldExchange::param** 。  
  
 [IsValidOperation](../Topic/CDaoFieldExchange::IsValidOperation.md) 成員函式撰寫自訂的 DFX 常式提供。  您在 [CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md) 函式最常使用 [SetFieldType](../Topic/CDaoFieldExchange::SetFieldType.md) 。  如需 DFX 全域函式的詳細資訊，請參閱 [資料錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。  如需資料型別的自訂文字 DFX 常式的詳細資訊，請參閱 [Technical Note 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。  
  
## 繼承階層架構  
 `CDaoFieldExchange`  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)