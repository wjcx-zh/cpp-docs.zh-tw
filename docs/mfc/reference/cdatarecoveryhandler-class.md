---
title: "CDataRecoveryHandler Class | Microsoft Docs"
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
  - "CDataRecoveryHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataRecoveryHandler class"
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
caps.latest.revision: 18
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataRecoveryHandler Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果應用程式意外關閉， `CDataRecoveryHandler` 自動儲存文件和還原它們。  
  
## 語法  
  
```  
class CDataRecoveryHandler : public CObject  
```  
  
## Members  
  
### 建構函式  
  
|||  
|-|-|  
|[CDataRecoveryHandler::CDataRecoveryHandler](../Topic/CDataRecoveryHandler::CDataRecoveryHandler.md)|建構 `CDataRecoveryHandler` 物件。|  
  
### 方法  
  
|||  
|-|-|  
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](../Topic/CDataRecoveryHandler::AutosaveAllDocumentInfo.md)|自動儲存每一檔案移至 `CDataRecoveryHandler` 註冊類別。|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](../Topic/CDataRecoveryHandler::AutosaveDocumentInfo.md)|自動儲存至指定的文件。|  
|[CDataRecoveryHandler::CreateDocumentInfo](../Topic/CDataRecoveryHandler::CreateDocumentInfo.md)|將文件加入至開啟的文件清單。|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](../Topic/CDataRecoveryHandler::DeleteAllAutosavedFiles.md)|刪除所有目前已自動儲存的檔案。|  
|[CDataRecoveryHandler::DeleteAutosavedFile](../Topic/CDataRecoveryHandler::DeleteAutosavedFile.md)|刪除指定的加以儲存的檔案。|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](../Topic/CDataRecoveryHandler::GenerateAutosaveFileName.md)|產生名稱自動儲存檔案與提供的文件檔案的名稱。|  
|[CDataRecoveryHandler::GetAutosaveInterval](../Topic/CDataRecoveryHandler::GetAutosaveInterval.md)|傳回之間時間間隔自動儲存嘗試。|  
|[CDataRecoveryHandler::GetAutosavePath](../Topic/CDataRecoveryHandler::GetAutosavePath.md)|傳回已自動儲存之檔案的路徑。|  
|[CDataRecoveryHandler::GetDocumentListName](../Topic/CDataRecoveryHandler::GetDocumentListName.md)|從 `CDocument` 物件擷取文件名稱。|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](../Topic/CDataRecoveryHandler::GetNormalDocumentTitle.md)|擷取指定之文件的一般標頭。|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](../Topic/CDataRecoveryHandler::GetRecoveredDocumentTitle.md)|建立並傳回復原的文件的標題。|  
|[CDataRecoveryHandler::GetRestartIdentifier](../Topic/CDataRecoveryHandler::GetRestartIdentifier.md)|擷取應用程式的唯一重新啟動的識別項。|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle.md)|表示 `CDataRecoveryHandler` 是否會在目前的迴圈等等的自動儲存。|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](../Topic/CDataRecoveryHandler::GetShutdownByRestartManager.md)|表示重新啟動管理員是否會導致應用程式結束。|  
|[CDataRecoveryHandler::Initialize](../Topic/CDataRecoveryHandler::Initialize.md)|初始化 `CDataRecoveryHandler`。|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](../Topic/CDataRecoveryHandler::QueryRestoreAutosavedDocuments.md)|顯示對話方塊給 `CDataRecoveryHandler` 自動儲存的每個文件的使用者。  對話方塊會判斷使用者是否要還原已自動儲存的文件。|  
|[CDataRecoveryHandler::ReadOpenDocumentList](../Topic/CDataRecoveryHandler::ReadOpenDocumentList.md)|從登錄載入開啟的文件清單。|  
|[CDataRecoveryHandler::RemoveDocumentInfo](../Topic/CDataRecoveryHandler::RemoveDocumentInfo.md)|從開啟的文件清單中移除所提供的文件。|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](../Topic/CDataRecoveryHandler::ReopenPreviousDocuments.md)|開啟先前開啟的文件。|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](../Topic/CDataRecoveryHandler::RestoreAutosavedDocuments.md)|還原根據使用者輸入的自動儲存的文件。|  
|[CDataRecoveryHandler::SaveOpenDocumentList](../Topic/CDataRecoveryHandler::SaveOpenDocumentList.md)|儲存開啟的文件目前清單至 Windows 登錄中。|  
|[CDataRecoveryHandler::SetAutosaveInterval](../Topic/CDataRecoveryHandler::SetAutosaveInterval.md)|以毫秒為單位設定之間的時間自動儲存循環。|  
|[CDataRecoveryHandler::SetAutosavePath](../Topic/CDataRecoveryHandler::SetAutosavePath.md)|設定存放加以儲存檔案的目錄。|  
|[CDataRecoveryHandler::SetRestartIdentifier](../Topic/CDataRecoveryHandler::SetRestartIdentifier.md)|設定 `CDataRecoveryHandler`的這個執行個體的唯一的重新啟動的識別項。|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle.md)|設定 `CDataRecoveryHandler` 在目前閒置期間，是否儲存開啟的文件資訊至 Windows 登錄中。|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](../Topic/CDataRecoveryHandler::SetShutdownByRestartManager.md)|設定應用程式的匯出先前是以重新啟動管理員所造成。|  
|[CDataRecoveryHandler::UpdateDocumentInfo](../Topic/CDataRecoveryHandler::UpdateDocumentInfo.md)|因為使用者已儲存它，更新檔案的相關資訊。|  
  
### 資料成員  
  
|||  
|-|-|  
|m\_bRestoringPreviousOpenDocs|指出資料復原管理員是否重新開啟先前開啟的文件。|  
|m\_bSaveDocumentInfoOnIdle|指出資料復原管理員是否自動儲存在環境下空的資料。|  
|m\_bShutdownByRestartManager|表示重新啟動管理員是否會導致應用程式結束。|  
|m\_dwRestartManagerSupportFlags|旗標會指示支援重新啟動管理員對應用程式提供。|  
|m\_lstAutosavesToDelete|未刪除加以儲存之檔案的清單，當原始文件關閉。  在應用程式結束時，重新啟動管理員再次嘗試刪除檔案。|  
|m\_mapDocNameToAutosaveName|文件名稱對應至加以儲存的檔案名稱。|  
|m\_mapDocNameToDocumentPtr|文件名稱對應至 [CDocument](../../mfc/reference/cdocument-class.md) 指標的。|  
|m\_mapDocNameToRestoreBool|文件名稱對應至指示是否要還原自動儲存的文件中布林值參數的。|  
|m\_mapDocumentPtrToDocName|`CDocument` 指標的對應至文件名稱。|  
|m\_mapDocumentPtrToDocTitle|`CDocument` 指標的對應至文件的標題。  這些標頭會儲存檔案使用。|  
|m\_nAutosaveInterval|時間之間的毫秒自動儲存。|  
|m\_nTimerID|自動儲存計時器的識別項。|  
|m\_strAutosavePath|儲存加以儲存檔案的位置。|  
|m\_strRestartIdentifier|GUID 的字串表示重新啟動管理員的。|  
  
## 備註  
 重新啟動管理員使用 `CDataRecoveryHandler` 類別記錄所有開啟的文件並會視需要自動儲存它們。  若要針對自動儲存，使用 [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle.md) 方法。  這個方法會指示 `CDataRecoveryHandler` 執行下一個空白環境的自動儲存。  當 `CDataRecoveryHandler` ，應該執行自動儲存時，重新啟動管理員呼叫 `SetSaveDocumentInfoOnIdle` 。  
  
 所有 `CDataRecoveryHandler` 類別的方法是虛擬的。  覆寫這個類別中的方法建立自己的自訂資料復原管理員。  除非您建立自己的資料復原管理員或重新啟動管理員，否則請勿 CDataRecoveryHandler。  當需要 [CWinApp Class](../../mfc/reference/cwinapp-class.md)`CDataRecoveryHandler` ，建立物件。  
  
 在您可以使用 `CDataRecoveryHandler` 物件之前，您必須呼叫 [CDataRecoveryHandler::Initialize](../Topic/CDataRecoveryHandler::Initialize.md)。  
  
 因為類別 `CDataRecoveryHandler` 嚴格地連接至重新啟動管理員， `CDataRecoveryHandler` 取決於全域參數 `m_dwRestartManagerSupportFlags`。  這個參數會判斷要將哪些使用權限重新啟動管理員具有，以及與應用程式互動的方式。  若要合併重新啟動管理員加入至現有的應用程式，您必須指定 `m_dwRestartManagerSupportFlags` 在主要應用程式中建構函式的適當值。  如需如何使用重新啟動管理員的詳細資訊，請參閱 [如何：加入重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)。  
  
## 需求  
 **標題:** afxdatarecovery.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [如何：加入重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)