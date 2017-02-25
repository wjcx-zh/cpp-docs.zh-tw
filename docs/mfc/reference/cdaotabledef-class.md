---
title: "CDaoTableDef Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoTableDef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoTableDef class"
  - "資料庫類別 [C++], DAO"
  - "database tables [C++], attached table definition"
  - "database tables [C++], base table definition"
  - "tabledefs [C++]"
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDaoTableDef Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示基底資料表或已附加的資料表中儲存的定義。  
  
## 語法  
  
```  
class CDaoTableDef : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDaoTableDef::CDaoTableDef](../Topic/CDaoTableDef::CDaoTableDef.md)|**CDaoTableDef** 建構物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDaoTableDef::Append](../Topic/CDaoTableDef::Append.md)|將新的資料表加入至資料庫。|  
|[CDaoTableDef::CanUpdate](../Topic/CDaoTableDef::CanUpdate.md)|傳回非零，如果資料表可更新 \(您可以修改欄位或資料表屬性的定義\)。|  
|[CDaoTableDef::Close](../Topic/CDaoTableDef::Close.md)|關閉已開啟 tabledef。|  
|[CDaoTableDef::Create](../Topic/CDaoTableDef::Create.md)|建立使用 [附加](../Topic/CDaoTableDef::Append.md)，可加入至資料庫中的資料表。|  
|[CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)|呼叫會建立資料表的欄位。|  
|[CDaoTableDef::CreateIndex](../Topic/CDaoTableDef::CreateIndex.md)|呼叫會建立資料表的索引。|  
|[CDaoTableDef::DeleteField](../Topic/CDaoTableDef::DeleteField.md)|呼叫資料表刪除資料的欄位。|  
|[CDaoTableDef::DeleteIndex](../Topic/CDaoTableDef::DeleteIndex.md)|呼叫刪除資料表的索引。|  
|[CDaoTableDef::GetAttributes](../Topic/CDaoTableDef::GetAttributes.md)|傳回值 `CDaoTableDef` 的一個或多個物件特性的值。|  
|[CDaoTableDef::GetConnect](../Topic/CDaoTableDef::GetConnect.md)|傳回所提供之資料表的來源相關資訊的值。|  
|[CDaoTableDef::GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md)|傳回基礎 `CDaoTableDef` 物件的基底資料表建立的日期和時間。|  
|[CDaoTableDef::GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md)|傳回所做的最新變更的日期和時間轉換為基底資料表的設計。|  
|[CDaoTableDef::GetFieldCount](../Topic/CDaoTableDef::GetFieldCount.md)|傳回表示資料表之欄位的值。|  
|[CDaoTableDef::GetFieldInfo](../Topic/CDaoTableDef::GetFieldInfo.md)|傳回特定型別欄位相關的資料表中的資訊。|  
|[CDaoTableDef::GetIndexCount](../Topic/CDaoTableDef::GetIndexCount.md)|傳回索引數目的資料表中的資料。|  
|[CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)|傳回特定型別有關的資訊之資料表的。|  
|[CDaoTableDef::GetName](../Topic/CDaoTableDef::GetName.md)|傳回資料表的使用者定義名稱。|  
|[CDaoTableDef::GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md)|會傳回資料表中的資料錄總數。|  
|[CDaoTableDef::GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md)|傳回包含來源資料庫中指定其他的資料表名稱的值。|  
|[CDaoTableDef::GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md)|傳回資料欄位驗證資料的值，以變更或加入至資料表。|  
|[CDaoTableDef::GetValidationText](../Topic/CDaoTableDef::GetValidationText.md)|傳回指定訊息文字、應用程式顯示的值，如果欄位物件的值不符合指定的驗證規則。|  
|[CDaoTableDef::IsOpen](../Topic/CDaoTableDef::IsOpen.md)|如果資料表開啟，則會傳回非零。|  
|[CDaoTableDef::Open](../Topic/CDaoTableDef::Open.md)|開啟資料庫中的 TableDef 之集合中所儲存的現有 tabledef。|  
|[CDaoTableDef::RefreshLink](../Topic/CDaoTableDef::RefreshLink.md)|若要更新已附加之資料表的連接資訊。|  
|[CDaoTableDef::SetAttributes](../Topic/CDaoTableDef::SetAttributes.md)|設定值 `CDaoTableDef` 的一個或多個物件特性的值。|  
|[CDaoTableDef::SetConnect](../Topic/CDaoTableDef::SetConnect.md)|將提供有關資料表來源的相關資訊的值。|  
|[CDaoTableDef::SetName](../Topic/CDaoTableDef::SetName.md)|設定資料表的名稱。|  
|[CDaoTableDef::SetSourceTableName](../Topic/CDaoTableDef::SetSourceTableName.md)|設定在來源資料庫中指定附加的資料表名稱的值。|  
|[CDaoTableDef::SetValidationRule](../Topic/CDaoTableDef::SetValidationRule.md)|設定資料欄位驗證資料的值，以變更或加入至資料表。|  
|[CDaoTableDef::SetValidationText](../Topic/CDaoTableDef::SetValidationText.md)|設定指定訊息文字、應用程式顯示的值，如果欄位物件的值不符合指定的驗證規則。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDaoTableDef::m\_pDAOTableDef](../Topic/CDaoTableDef::m_pDAOTableDef.md)|對基礎物件的 DAO tabledef 介面的指標。|  
|[CDaoTableDef::m\_pDatabase](../Topic/CDaoTableDef::m_pDatabase.md)|這個資料表的來源資料庫。|  
  
## 備註  
 每個 DAO 資料庫物件所維護的集合，所以呼叫 TableDefs，其中包含所有已儲存的 DAO tabledef 物件。  
  
 使用 `CDaoTableDef` 物件，可以管理資料表定義。  例如，您可以：  
  
-   會檢查資料庫中的所有區域的欄位和索引結構，附加或外部資料表。  
  
-   呼叫附加之資料表的 `SetConnect` 和 `SetSourceTableName` 成員函式，並使用 `RefreshLink` 成員函式更新與其他資料表的連結。  
  
-   呼叫 `CanUpdate` 成員函式來決定是否在資料表中編輯欄位定義。  
  
-   使用 `GetValidationRule` 和 `SetValidationRule`和 `GetValidationText` 和 `SetValidationText` 成員函式，取得或設定驗證符合。  
  
-   使用 **開啟** 成員函式建立桌、dynaset\-或快照集類型 `CDaoRecordset` 物件。  
  
    > [!NOTE]
    >  DAO 資料庫類別會根據 Open 開放式資料庫連接的 MFC 資料庫類別本身不同 \(ODBC\)。  所有 DAO 資料庫類別名稱中有「CDao」前置詞。  您仍然可以存取使用 DAO 類別的 ODBC 資料來源，，因為它們是針對 Microsoft Jet 資料庫引擎， DAO 類別通常會提供絕佳的功能。  
  
### 使用 tabledef 物件使用現有資料表來使用或建立新的資料表。  
  
1.  在所有情況下，請先 `CDaoTableDef` 建構物件，提供指標的資料表所屬的 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 物件。  
  
2.  然後根據執行下列動作，您需要:  
  
    -   若要使用現有儲存資料表， [開啟](../Topic/CDaoTableDef::Open.md) tabledef 呼叫物件的成員函式，提供儲存的資料表名稱。  
  
    -   若要建立新的資料表，請呼叫 [建立](../Topic/CDaoTableDef::Create.md) tabledef 物件的成員函式，提供資料表的名稱。  呼叫 [CreateField](../Topic/CDaoTableDef::CreateField.md) 和 [CreateIndex](../Topic/CDaoTableDef::CreateIndex.md) 加入欄位和索引的資料表。  
  
    -   呼叫 [附加](../Topic/CDaoTableDef::Append.md) 透過附加它會將資料表加入至資料庫的 TableDefs 集合。  **建立** tabledef 放至處於開啟狀態，因此，在呼叫 **建立** 之後您就不會呼叫 **開啟**。  
  
        > [!TIP]
        >  最簡單的方法會建立儲存的資料表會建立資料並儲存在資料庫中使用 Microsoft Access。  然後您可以開啟和使用它們以 MFC 程式碼。  
  
 若要使用您開啟或建立的 tabledef 物件，建立並開啟 `CDaoRecordset` 物件，指定 tabledef 名稱與 **dbOpenTable** 的值。 `nOpenType` 參數。  
  
 當您呼叫時，要使用 [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md)tabledef 物件建立 `CDaoRecordset` 物件，您必須建立或如上所述通常會開啟 tabledef，然後建構資料錄集物件，將指標傳遞至 tabledef 物件。  您傳入的 tabledef 必須處於開啟狀態。  如需詳細資訊，請參閱類別 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 當您完成使用 tabledef 物件時，請呼叫其成員函式， [關閉](../Topic/CDaoRecordset::Close.md) 然後終結 tabledef 物件。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)