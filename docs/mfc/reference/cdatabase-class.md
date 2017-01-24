---
title: "CDatabase Class | Microsoft Docs"
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
  - "CDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDatabase 類別"
  - "資料庫類別 [C++], ODBC"
  - "資料庫連接 [C++], CDatabase 類別"
  - "MFC [C++], ODBC"
  - "ODBC [C++], CDatabase 類別"
  - "ODBC database class"
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
caps.latest.revision: 24
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDatabase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示資料來源的連接，您可以在資料來源。  
  
## 語法  
  
```  
  
class CDatabase : public CObject  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDatabase::CDatabase](../Topic/CDatabase::CDatabase.md)|建構 `CDatabase` 物件。  您必須呼叫 `OpenEx` 或 **開啟**初始化物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDatabase::BeginTrans](../Topic/CDatabase::BeginTrans.md)|開始一個交易」— 「為 `AddNew`、 **編輯**、 **刪除**和 **更新** 類別 `CRecordset` 成員函式的一系列可復原的呼叫—在連接的資料來源。  資料來源必須支援 **BeginTrans** 的交易產生作用。|  
|[CDatabase::BindParameters](../Topic/CDatabase::BindParameters.md)|可讓您存取內建參數在呼叫 `CDatabase::ExecuteSQL`之前。|  
|[CDatabase::Cancel](../Topic/CDatabase::Cancel.md)|取消非同步作業或處理序從第二個執行緒。|  
|[CDatabase::CanTransact](../Topic/CDatabase::CanTransact.md)|如果資料來源支援交易，則會傳回非零。|  
|[CDatabase::CanUpdate](../Topic/CDatabase::CanUpdate.md)|傳回非零，如果 `CDatabase` 物件不可更新 \(唯讀\)。|  
|[CDatabase::Close](../Topic/CDatabase::Close.md)|關閉資料來源連接。|  
|[CDatabase::CommitTrans](../Topic/CDatabase::CommitTrans.md)|完成 **BeginTrans**開始的交易。  修改資料來源在交易中執行的命令。|  
|[CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md)|執行 SQL 陳述式。  資料錄不會傳回。|  
|[CDatabase::GetBookmarkPersistence](../Topic/CDatabase::GetBookmarkPersistence.md)|識別書籤在資料錄集物件保存的作業。|  
|[CDatabase::GetConnect](../Topic/CDatabase::GetConnect.md)|傳回用來連接至資料來源的 `CDatabase` ODBC 連接字串物件。|  
|[CDatabase::GetCursorCommitBehavior](../Topic/CDatabase::GetCursorCommitBehavior.md)|識別認可交易的影響至開啟資料錄集物件。|  
|[CDatabase::GetCursorRollbackBehavior](../Topic/CDatabase::GetCursorRollbackBehavior.md)|識別復原交易的影響在開啟資料錄集物件。|  
|[CDatabase::GetDatabaseName](../Topic/CDatabase::GetDatabaseName.md)|傳回目前使用中之資料庫的名稱。|  
|[CDatabase::IsOpen](../Topic/CDatabase::IsOpen.md)|如果 `CDatabase` 物件目前連接到資料來源，則會傳回非零。|  
|[CDatabase::OnSetOptions](../Topic/CDatabase::OnSetOptions.md)|呼叫框架設定標準連接選項。  預設實作會將查詢逾時值。  您可以藉由呼叫 `SetQueryTimeout`事先建立這些選項。|  
|[CDatabase::Open](../Topic/CDatabase::Open.md)|建立資料來源的連接 \(透過 ODBC 驅動程式\)。|  
|[CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md)|建立資料來源的連接 \(透過 ODBC 驅動程式\)。|  
|[CDatabase::Rollback](../Topic/CDatabase::Rollback.md)|在交易期間所做的變更與相反。  資料來源返回之前的狀態，並且定義於 **BeginTrans** 呼叫時，並未變更。|  
|[CDatabase::SetLoginTimeout](../Topic/CDatabase::SetLoginTimeout.md)|將秒數，也就是資料來源連接嘗試將逾時。|  
|[CDatabase::SetQueryTimeout](../Topic/CDatabase::SetQueryTimeout.md)|將秒數，之後資料庫查詢作業會逾時。  會影響所有後續的資料錄集 **開啟**、 `AddNew`、 **編輯**和 **刪除** 呼叫。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDatabase::m\_hdbc](../Topic/CDatabase::m_hdbc.md)|開放式資料庫連接 \(Open Database Connectivity，ODBC\) 資料來源的連接控制代碼。  輸入 **HDBC**。|  
  
## 備註  
 資料來源是某些資料庫管理系統裝載的資料的特定執行個體 \(Referential Integrity\)。  範例包括 Microsoft SQL Server、Microsoft Access， Borland dBASE 和 xBASE。  您可以同時具有一或多個物件 `CDatabase` 現用在您的應用程式。  
  
> [!NOTE]
>  如果您使用存取資料時使用物件 \(DAO\) 類別而不是開放式資料庫連接 \(ODBC\) 類別會使用類別， [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 。  如需詳細資訊，請參閱本文 [概觀:資料庫程式開發](../../data/data-access-programming-mfc-atl.md)。  
  
 使用 `CDatabase`， `CDatabase` 建構物件並呼叫它的 `OpenEx` 成員函式。  這會開啟連接。  當您然後再建運作的 `CRecordset` 物件在連接的資料來源時，請透過資料錄集建構函式指標至 `CDatabase` 物件。  當您完成使用連接時，請呼叫 **關閉** 成員函式和終結 `CDatabase` 物件。  **關閉** 結束您先前未關閉的所有資料錄集。  
  
 如需 `CDatabase`的資訊，請參閱 Microsoft 知識庫文件 [資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md) 和 [概觀:資料庫程式開發](../../data/data-access-programming-mfc-atl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## 需求  
 **Header:** afxdb.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)