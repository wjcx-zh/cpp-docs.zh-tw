---
title: "CDaoWorkspace Class | Microsoft Docs"
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
  - "CDaoWorkspace"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoWorkspace class"
  - "DAO workspaces [C++]"
  - "DAO workspaces [C++], CDaoWorkspace class"
  - "database engine [C++], accessing via workspace"
  - "DDLs [C++]"
  - "default workspaces [C++]"
  - "default workspaces [C++], DAO"
  - "預設值 [C++], 工作區"
  - "ODBC 類別 [C++], vs. DAO classes"
  - "persistence [C++], DAO workspace"
  - "security [MFC]"
  - "security [MFC], DAO workspaces"
  - "sessions [C++], DAO workspace"
  - "transaction spaces [C++]"
  - "transaction spaces [C++], DAO workspace"
  - "Workspace class"
  - "workspaces [C++], DAO"
  - "workspaces [C++], 預設"
  - "workspaces [C++], interface to database engine"
  - "workspaces [C++], 保存性"
  - "Workspaces collection"
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoWorkspace Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理從註冊的具名，密碼保護資料庫工作階段 \(Session\) 登出，由單一使用者。  
  
## 語法  
  
```  
class CDaoWorkspace : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDaoWorkspace::CDaoWorkspace](../Topic/CDaoWorkspace::CDaoWorkspace.md)|工作區建構物件。  之後，呼叫 **建立** 或 **開啟**。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDaoWorkspace::Append](../Topic/CDaoWorkspace::Append.md)|附加新建立的工作區對應資料庫引擎的工作區集合。|  
|[CDaoWorkspace::BeginTrans](../Topic/CDaoWorkspace::BeginTrans.md)|啟動新的交易，適用於所有資料庫開啟在工作區。|  
|[CDaoWorkspace::Close](../Topic/CDaoWorkspace::Close.md)|關閉它所包含的工作區和所有物件。  暫止的交易。|  
|[CDaoWorkspace::CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md)|完成目前的異動並儲存變更。|  
|[CDaoWorkspace::CompactDatabase](../Topic/CDaoWorkspace::CompactDatabase.md)|壓縮 \(或重複的資料庫\)。|  
|[CDaoWorkspace::Create](../Topic/CDaoWorkspace::Create.md)|建立新的 DAO 工作區物件。|  
|[CDaoWorkspace::GetDatabaseCount](../Topic/CDaoWorkspace::GetDatabaseCount.md)|傳回 DAO 資料庫中之物件數目的工作區的資料庫的集合。|  
|[CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md)|傳回關於在工作區的資料庫集合定義的指定 DAO 資料庫的資訊。|  
|[CDaoWorkspace::GetIniPath](../Topic/CDaoWorkspace::GetIniPath.md)|傳回 Microsoft Jet 資料庫引擎的初始化設定的位置在 Windows 登錄中。|  
|[CDaoWorkspace::GetIsolateODBCTrans](../Topic/CDaoWorkspace::GetIsolateODBCTrans.md)|傳回值以指出是否涉及相同 ODBC 資料來源將資料來源的強制的多個連接隔離的多個交易。|  
|[CDaoWorkspace::GetLoginTimeout](../Topic/CDaoWorkspace::GetLoginTimeout.md)|傳回秒數，在錯誤發生之前，當使用者嘗試登入至 ODBC 資料庫時。|  
|[CDaoWorkspace::GetName](../Topic/CDaoWorkspace::GetName.md)|傳回使用者定義的名稱工作區物件。|  
|[CDaoWorkspace::GetUserName](../Topic/CDaoWorkspace::GetUserName.md)|在工作區中建立，則會傳回指定的使用者名稱。  這是工作區的擁有人的名稱。|  
|[CDaoWorkspace::GetVersion](../Topic/CDaoWorkspace::GetVersion.md)|傳回包含資料庫引擎版本與工作區的字串。|  
|[CDaoWorkspace::GetWorkspaceCount](../Topic/CDaoWorkspace::GetWorkspaceCount.md)|傳回在 DAO 資料庫引擎的工作區集合的工作區中物件的數目。|  
|[CDaoWorkspace::GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md)|傳回關於在資料庫引擎的工作區集合定義的指定 DAO 工作區的相關資訊。|  
|[CDaoWorkspace::Idle](../Topic/CDaoWorkspace::Idle.md)|讓資料庫引擎執行背景工作。|  
|[CDaoWorkspace::IsOpen](../Topic/CDaoWorkspace::IsOpen.md)|如果工作區中開啟，則會傳回非零。|  
|[CDaoWorkspace::Open](../Topic/CDaoWorkspace::Open.md)|明確開啟工作區與 DAO 的預設工作區相關聯。|  
|[CDaoWorkspace::RepairDatabase](../Topic/CDaoWorkspace::RepairDatabase.md)|嘗試修復損毀的資料庫。|  
|[CDaoWorkspace::Rollback](../Topic/CDaoWorkspace::Rollback.md)|結束目前的交易，且不儲存變更。|  
|[CDaoWorkspace::SetDefaultPassword](../Topic/CDaoWorkspace::SetDefaultPassword.md)|設定資料庫引擎所使用的密碼編譯工作區域物件的建立時間，不含特定的密碼。|  
|[CDaoWorkspace::SetDefaultUser](../Topic/CDaoWorkspace::SetDefaultUser.md)|設定資料庫引擎所使用的使用者名稱工作區物件的建立時間，而不需要特定的使用者名稱。|  
|[CDaoWorkspace::SetIniPath](../Topic/CDaoWorkspace::SetIniPath.md)|設定 Microsoft Jet 資料庫引擎的初始化設定的位置在 Windows 登錄中。|  
|[CDaoWorkspace::SetIsolateODBCTrans](../Topic/CDaoWorkspace::SetIsolateODBCTrans.md)|指定涉及相同 ODBC 資料來源的多個交易是否可以強制與資料來源的多個連接隔離。|  
|[CDaoWorkspace::SetLoginTimeout](../Topic/CDaoWorkspace::SetLoginTimeout.md)|將秒數，在錯誤發生之前，當使用者嘗試登入至 ODBC 資料來源時。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDaoWorkspace::m\_pDAOWorkspace](../Topic/CDaoWorkspace::m_pDAOWorkspace.md)|對基礎 DAO 工作區物件。|  
  
## 備註  
 在許多情況下，您並不需要多個工作區，因此，您不需要明確建立工作區物件;當您開啟資料庫和資料錄集物件時，會使用 DAO 的預設工作區相關聯。  不過，如果有需要，您一次最多個工作階段都會建立不同的工作區物件執行。  每個工作區物件可以在自己的資料庫集合包含多個開啟的資料庫物件。  在 MFC 中，工作區是主要交易管理員，指定一組開啟資料庫都位在相同的交易「空間」。  
  
> [!NOTE]
>  DAO 資料庫類別會根據 Open 開放式資料庫連接的 MFC 資料庫類別本身不同 \(ODBC\)。  所有 DAO 資料庫類別名稱中有「CDao」前置詞。  一般而言，根據的 MFC DAO 類別比 ODBC 架構的 MFC 類別的功能。  DAO 架構的類別會透過 Microsoft Jet 資料庫引擎來存取資料，包括 ODBC 驅動程式。  透過類別也支援資料定義語言 \(DDL\) \(DDL\) 作業，例如建立資料庫並加入資料表，和欄位，而不需要直接呼叫 DAO。  
  
## 功能  
 類別 `CDaoWorkspace` 提供下列項目:  
  
-   明確存取，如有需要，為預設工作區，可以初始化資料庫引擎。  通常您會使用 DAO 的預設工作區隱含地透過建立資料庫和資料錄集物件。  
  
-   交易適用於所有資料庫開啟在工作區的交易空間。  您可以建立其他工作區管理個別的交易空間。  
  
-   對基礎 Microsoft Jet 資料庫引擎的許多屬性的介面 \(請參閱靜態成員函式\)。  開啟或建立工作區或呼叫靜態成員函式，在中開啟或建立，初始化資料庫引擎之前。  
  
-   對資料庫引擎的工作區集合的存取權，儲存所有作用中工作區域附加至其中。  您也可以建立和使用工作區，而不用附加至集合。  
  
## 安全性  
 MFC 不實作使用者並不在 DAO 群組的集合，提供安全控制項使用。  如果您需要 DAO 層面，您必須透過直接呼叫程式設計它們至 DAO 介面。  如需詳細資訊，請參閱 [Technical Note 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
## 使用方式  
 您可以使用類別 `CDaoWorkspace` :  
  
-   請明確開啟預設工作區。  
  
     通常—例如，當您開啟新的 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件時，會預設工作區的用途是隱含的。  例如，但是您可能需要明確存取它\)，來存取資料庫引擎屬性或工作區集合。  請參閱「若要預設工作區的隱含使用」。  
  
-   建立新的工作區。  如果您想要將它們加入至工作區集合，請呼叫 [附加](../Topic/CDaoWorkspace::Append.md) 。  
  
-   開啟工作區集合中現有的工作區。  
  
 建立尚未存在於工作區中集合的新工作區內所述 [建立](../Topic/CDaoWorkspace::Create.md) 成員函式底下。  工作區物件不以任何方式 datababase 引擎在工作階段之間保存。  如果您的應用程式連結 MFC 靜態，關閉應用程式 uninitializes 資料庫引擎。  如果您使用 MFC 的應用程式連結動態，資料庫引擎尚未初始化，並在 MFC DLL 卸載。  
  
 明確開啟預設工作區或開啟現有的工作區與工作區集合，說明在 [開啟](../Topic/CDaoWorkspace::Open.md) 成員函式底下。  
  
 藉由關閉有 [關閉](../Topic/CDaoWorkspace::Close.md) 成員函式的工作區工作區結束工作階段。  **關閉** 關閉您先前未關閉的所有資料庫，復原任何未認可的交易。  
  
## 交易  
 DAO 處理交易在工作區層級，因此，在工作區的交易有多個開啟資料庫的適用於所有資料庫。  例如，在中，如果兩個資料庫有未經認可的更新，但您呼叫 [CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md)，所有進行更新。  如果您想要限制交易至單一資料庫，您需要其不同的工作區物件。  
  
## 對預設工作區的隱含使用  
 使用 MFC DAO 的預設工作區隱含下列情況:  
  
-   如果您建立新的 `CDaoDatabase` 物件，但透過現有的 `CDaoWorkspace` 物件沒有這樣做， MFC 建立自己的暫時工作區物件，對應至 DAO 的預設工作區相關聯。  如果您為多個資料庫來達成，所有資料庫物件與預設工作區。  您可以 `CDaoDatabase` 資料成員存取資料庫的工作區。  
  
-   同樣地，因此，如果您建立 `CDaoRecordset` 物件，但未提供指標的 `CDaoDatabase` 物件、MFC 建立暫存資料庫物件，而且，依副檔名，暫時工作區物件。  您可以 `CDaoRecordset` 資料成員存取資料錄集的資料庫和間接其工作區。  
  
## 其他作業  
 其他資料庫作業也提供，例如修復損毀的資料庫或 Compact 資料庫。  
  
 如需直接呼叫 DAO 和檔案的相關資訊。如需 DAO 安全性，請參閱 [Technical Note 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)