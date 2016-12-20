---
title: "CDaoDatabase Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoDatabase class"
  - "CDaoDatabase class, and workspace"
  - "CDaoDatabase class, vs. CDatabase class"
  - "CDatabase 類別, vs. CDaoDatabase class"
  - "資料庫類別 [C++], DAO"
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoDatabase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代表與您可以操作資料之資料庫的連接。  
  
## 語法  
  
```  
class CDaoDatabase : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDaoDatabase::CDaoDatabase](../Topic/CDaoDatabase::CDaoDatabase.md)|建構 `CDaoDatabase` 物件。  呼叫 **開啟** 連接至資料庫中的物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDaoDatabase::CanTransact](../Topic/CDaoDatabase::CanTransact.md)|傳回非零，如果資料庫支援交易。|  
|[CDaoDatabase::CanUpdate](../Topic/CDaoDatabase::CanUpdate.md)|傳回非零，如果 `CDaoDatabase` 物件不可更新 \(唯讀\)。|  
|[CDaoDatabase::Close](../Topic/CDaoDatabase::Close.md)|關閉資料庫連接。|  
|[CDaoDatabase::Create](../Topic/CDaoDatabase::Create.md)|建立基礎 DAO 資料庫物件並 `CDaoDatabase` 初始化物件。|  
|[CDaoDatabase::CreateRelation](../Topic/CDaoDatabase::CreateRelation.md)|定義在資料表中的新的關聯至資料庫。|  
|[CDaoDatabase::DeleteQueryDef](../Topic/CDaoDatabase::DeleteQueryDef.md)|刪除資料庫中的 QueryDefs 集合儲存 querydef 物件。|  
|[CDaoDatabase::DeleteRelation](../Topic/CDaoDatabase::DeleteRelation.md)|刪除資料表之間的現有關聯至資料庫。|  
|[CDaoDatabase::DeleteTableDef](../Topic/CDaoDatabase::DeleteTableDef.md)|刪除一個資料表的定義於資料庫中。  這個刪除實際資料表及其所有資料。|  
|[CDaoDatabase::Execute](../Topic/CDaoDatabase::Execute.md)|執行動作查詢。  呼叫傳回結果擲回例外狀況的查詢的 **執行** 。|  
|[CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md)|傳回用來連接字串會連接至資料庫的 `CDaoDatabase` 物件。  用於 ODBC。|  
|[CDaoDatabase::GetName](../Topic/CDaoDatabase::GetName.md)|傳回目前使用中之資料庫的名稱。|  
|[CDaoDatabase::GetQueryDefCount](../Topic/CDaoDatabase::GetQueryDefCount.md)|傳回為資料庫中定義的查詢數目。|  
|[CDaoDatabase::GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md)|傳回有關資料庫中定義的指定查詢的詳細資訊。|  
|[CDaoDatabase::GetQueryTimeout](../Topic/CDaoDatabase::GetQueryTimeout.md)|傳回秒數，之後資料庫查詢作業會逾時。  會影響所有後續開啟，加入新的，更新和編輯作業和其他作業在 ODBC 資料來源 \(例如\) 只 **執行** 呼叫。|  
|[CDaoDatabase::GetRecordsAffected](../Topic/CDaoDatabase::GetRecordsAffected.md)|傳回上次修改影響的資料錄數目，編輯或透過呼叫或將作業加入至 **執行**。|  
|[CDaoDatabase::GetRelationCount](../Topic/CDaoDatabase::GetRelationCount.md)|傳回關聯的數目會定義於資料庫中的資料表之間。|  
|[CDaoDatabase::GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md)|傳回與指定之相關聯的資訊是在資料庫中的資料表之間。|  
|[CDaoDatabase::GetTableDefCount](../Topic/CDaoDatabase::GetTableDefCount.md)|傳回資料庫中定義的資料表數目。|  
|[CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md)|傳回與指定之資料表的資訊保存在資料庫中。|  
|[CDaoDatabase::GetVersion](../Topic/CDaoDatabase::GetVersion.md)|會傳回資料庫引擎的版本與資料庫。|  
|[CDaoDatabase::IsOpen](../Topic/CDaoDatabase::IsOpen.md)|如果 `CDaoDatabase` 物件目前連接到資料庫，則會傳回非零。|  
|[CDaoDatabase::Open](../Topic/CDaoDatabase::Open.md)|建立與資料庫的連接。|  
|[CDaoDatabase::SetQueryTimeout](../Topic/CDaoDatabase::SetQueryTimeout.md)|將秒數，之後資料庫查詢作業 \(僅在 ODBC 資料來源\) 會逾時。  會影響所有後續開啟，加入新的，更新和刪除作業。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDaoDatabase::m\_pDAODatabase](../Topic/CDaoDatabase::m_pDAODatabase.md)|對基礎 DAO 資料庫物件的指標。|  
|[CDaoDatabase::m\_pWorkspace](../Topic/CDaoDatabase::m_pWorkspace.md)|out 包含資料庫並定義其交易空間的 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 物件的指標。|  
  
## 備註  
 如需支援的資料庫格式的詳細資訊，請參閱 [GetName](../Topic/CDaoWorkspace::GetName.md) 成員函式。  您可以同時具有一或多個物件 `CDaoDatabase` 作用在指定「工作區」，表示由 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 物件。  工作區維持開啟的資料庫物件的集合，所以呼叫資料庫設定。  
  
> [!NOTE]
>  MFC DAO 資料庫類別從 ODBC 架構的 MFC 資料庫類別是不同的。  所有 DAO 資料庫類別名稱中有「CDao」前置詞。  類別 `CDaoDatabase` 提供介面類似 ODBC 類別 [CDatabase](../../mfc/reference/cdatabase-class.md)。  主要差異是 `CDatabase` 透過開放式資料庫連接 \(Open Database Connectivity，ODBC\) 存取 DBMS 和這個 DBMS 的 ODBC 驅動程式。  `CDaoDatabase` 存取資料的方式是將資料存取物件會根據 Microsoft Jet 資料庫引擎的 \(DAO\)。  一般而言，根據的 MFC DAO 類別比 ODBC 架構的 MFC 類別功能;以 DAO 類別的類別可以存取資料，包括透過 ODBC 驅動程式，將它們自己的資料庫引擎。  DAO 架構的類別會透過類別也支援資料定義語言 \(DDL\) \(DDL\) 作業，例如，加入資料表，而不需要直接呼叫 DAO。  
  
## 使用方式  
 然後，當您建立資料錄集物件時，您可以隱含建立資料庫物件。  但是，您可以明確地建立資料庫物件。  若要明確使用現有的資料庫與 `CDaoDatabase`，請執行下列任一步驟:  
  
-   `CDaoDatabase` 建構物件，並傳遞指標至開啟 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 物件。  
  
-   或者 `CDaoDatabase` 建構物件，而不需要指定工作區 \(MFC 建立暫時工作區物件\)。  
  
 建立新的 Microsoft Jet \(.MDB\) 資料庫， `CDaoDatabase` 建構物件並呼叫它的 [建立](../Topic/CDaoDatabase::Create.md) 成員函式。  不要在 **建立**之後呼叫 **開啟** 。  
  
 開啟現有的資料庫， `CDaoDatabase` 建構物件並呼叫它的 [開啟](../Topic/CDaoDatabase::Open.md) 成員函式。  
  
 這些技術的任一個附加至工作區的資料庫集合的 DAO 資料庫物件並開啟與資料連接。  當您然後再建運作的 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 物件在連接的資料庫時，請傳遞這些物件的建構函式指標至 `CDaoDatabase` 物件。  當您完成使用連接時，請呼叫 [關閉](../Topic/CDaoDatabase::Close.md) 成員函式和終結 `CDaoDatabase` 物件。  **關閉** 結束您先前未關閉的所有資料錄集。  
  
## 交易  
 資料庫交易處理會在工作區層級 \(請參閱 [BeginTrans](../Topic/CDaoWorkspace::BeginTrans.md)、 [CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md)和 [復原](../Topic/CDaoWorkspace::Rollback.md) 類別 `CDaoWorkspace`的成員函式。  
  
## ODBC 連接。  
 建議的 ODBC 資料來源一起使用會附加外部資料表至 Microsoft Jet \(.MDB\) 資料庫。  
  
## 集合  
 每個資料庫維護它、tabledef querydef、資料錄集和關聯物件的集合。  類別 `CDaoDatabase` 提供管理這些物件的成員函式。  
  
> [!NOTE]
>  物件會儲存在 DAO，無法在 MFC 資料庫物件。  MFC 提供類別、tabledef querydef 和資料錄集物件的，但沒有關聯的物件。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoDatabase`  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)