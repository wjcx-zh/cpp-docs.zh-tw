---
title: "CDataRecoveryHandler 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
dev_langs:
- C++
helpviewer_keywords:
- CDataRecoveryHandler class
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c2a99e32a88b8cb3f12d0961451025596886abb0
ms.lasthandoff: 02/24/2017

---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler 類別
`CDataRecoveryHandler`時，自動儲存文件，並還原它們，如果應用程式意外結束。  
  
## <a name="syntax"></a>語法  
  
```  
class CDataRecoveryHandler : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|建構 `CDataRecoveryHandler` 物件。|  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|使用註冊的每個檔案時，自動儲存`CDataRecoveryHandler`類別。|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|時，自動儲存指定的文件。|  
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|將文件加入至開啟的文件的清單。|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|刪除所有目前的 autosaved 檔案。|  
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|刪除指定的 autosaved 檔案。|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|會產生與提供的文件檔案名稱相關聯的自動儲存檔案的名稱。|  
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|傳回伺服器會自動嘗試之間的間隔。|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|傳回 autosaved 檔案的路徑。|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|擷取的文件名稱`CDocument`物件。|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|擷取指定的文件的一般標題。|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|建立並傳回復原的文件的標題。|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|擷取應用程式重新啟動唯一識別項。|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|指出是否`CDataRecoveryHandler`執行自動儲存在目前的閒置迴圈。|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|指出重新啟動管理員是否會造成應用程式結束。|  
|[CDataRecoveryHandler::Initialize](#initialize)|初始化 `CDataRecoveryHandler`。|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|向使用者顯示對話方塊中的每個文件`CDataRecoveryHandler`autosaved。 對話方塊中，決定使用者是否想要還原 autosaved 文件。|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|從登錄載入開啟的文件清單。|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|從開啟的文件清單中移除提供的文件。|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|開啟先前開啟的文件。|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|還原根據使用者輸入的 autosaved 文件。|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Windows 登錄中儲存目前開啟的文件的清單。|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|設定以毫秒為單位的自動儲存循環之間的時間。|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|設定儲存 autosaved 檔案的目錄。|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|設定這個執行個體的唯一重新啟動識別碼`CDataRecoveryHandler`。|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|設定是否`CDataRecoveryHandler`目前閒置週期期間，將開啟的文件資訊儲存至 Windows 登錄。|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|設定是否重新啟動管理員所造成的應用程式之前結束。|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|因為使用者儲存它，請更新文件的資訊。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|表示資料復原處理常式是否要重新開啟先前開啟的文件。|  
|m_bSaveDocumentInfoOnIdle|指出是否資料復原處理常式時，自動儲存文件的下一步的閒置迴圈。|  
|m_bShutdownByRestartManager|指出是否重新啟動管理員，讓應用程式結束。|  
|m_dwRestartManagerSupportFlags|旗標，表示重新啟動管理員支援哪些提供應用程式。|  
|m_lstAutosavesToDelete|並不會刪除原始文件已關閉時的 autosaved 檔案的清單。 應用程式結束時，重新啟動管理員重新嘗試刪除檔案。|  
|m_mapDocNameToAutosaveName|Autosaved 檔案名稱之文件名稱的對應。|  
|m_mapDocNameToDocumentPtr|將文件名稱的對應[CDocument](../../mfc/reference/cdocument-class.md)指標。|  
|m_mapDocNameToRestoreBool|布林值參數，指出是否要還原 autosaved 文件之文件名稱的對應。|  
|m_mapDocumentPtrToDocName|圖表的`CDocument`文件名稱的指標。|  
|m_mapDocumentPtrToDocTitle|圖表的`CDocument`文件標題的指標。 這些項目用於儲存檔案。|  
|m_nAutosaveInterval|以毫秒為單位之間時，自動儲存的時間。|  
|m_nTimerID|自動儲存計時器識別項。|  
|m_strAutosavePath|Autosaved 文件儲存位置。|  
|m_strRestartIdentifier|重新啟動管理員 GUID 的字串表示。|  
  
## <a name="remarks"></a>備註  
 重新啟動管理員會使用`CDataRecoveryHandler`類別，以記錄追蹤的所有開啟的文件，並自動儲存它們所需。 若要啟用自動儲存，使用[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)方法。 這個方法會指示`CDataRecoveryHandler`在下一步的閒置迴圈上執行自動儲存。 重新啟動管理員呼叫`SetSaveDocumentInfoOnIdle`時`CDataRecoveryHandler`應該執行自動儲存。  
  
 所有的方法`CDataRecoveryHandler`類別都是虛擬的。 覆寫這個類別來建立您自己的自訂資料復原處理常式中的方法。 除非您建立您自己的資料復原處理常式，或重新啟動管理員 」，請勿執行個體化 CDataRecoveryHandler。 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)建立`CDataRecoveryHandler`物件，因為它是必要。  
  
 您可以使用之前`CDataRecoveryHandler`物件，您必須呼叫[CDataRecoveryHandler::Initialize](#initialize)。  
  
 因為`CDataRecoveryHandler`類別緊密連接到重新啟動管理員，`CDataRecoveryHandler`相依於通用參數`m_dwRestartManagerSupportFlags`。 這個參數會決定重新啟動管理員具有的權限，以及它如何與您的應用程式互動。 若要併入現有的應用程式重新啟動管理員，您必須指派`m_dwRestartManagerSupportFlags`主應用程式的建構函式中的適當值。 如需如何使用重新啟動管理員的詳細資訊，請參閱[How to︰ 加入重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo  
 使用註冊的每個檔案時，自動儲存`CDataRecoveryHandler`類別。  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`CDataRecoveryHandler`儲存所有文件。`FALSE`如果沒有儲存任何文件。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`TRUE`如果沒有，您必須儲存的文件。 它也會傳回`TRUE`而不儲存任何文件，如果擷取`CWinApp`或`CDocManager`應用程式會產生錯誤。  
  
 若要使用這個方法，或是`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`必須在設定`m_dwRestartManagerSupportFlags`。 請參閱[m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)如需詳細資訊。  
  
##  <a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo  
 時，自動儲存指定的文件。  
  
```  
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,  
    BOOL bResetModifiedFlag = TRUE);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pDocument`|指標`CDocument`儲存。|  
|[in] `bResetModifiedFlag`|`TRUE`表示`CDataRecoveryHandler`認為`pDocument`修改;`FALSE`指出架構會考慮`pDocument`是未經修改。 請參閱 < 備註 > 一節，如此旗標的效果相關的詳細資訊。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果設定了適當的旗標和`pDocument`有效`CDocument`物件。  
  
### <a name="remarks"></a>備註  
 每個`CDocument`物件具有指出是否已變更自上次儲存的旗標。 使用[CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified)來判斷此旗標的狀態。 如果`CDocument`最後一個檔案中之後, 並未變更`AutosaveDocumentInfo`刪除該份文件的任何 autosaved 檔案。 如果文件已經從上次儲存後，關閉它會提示使用者儲存在關閉前的文件。  
  
> [!NOTE]
>  使用`bResetModifiedFlag`文件的狀態變更為未修改可能會造成使用者遺失未儲存的資料。 如果架構將視為未經修改的文件，關閉它不會提示使用者儲存。  
  
 這個方法會擲回例外狀況的[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)巨集如果`pDocument`不是有效`CDocument`物件。  
  
 若要使用這個方法，或是`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL`必須在設定`m_dwRestartManagerSupportFlags`。   
  
##  <a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler  
 建構 `CDataRecoveryHandler` 物件。  
  
```  
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,  
    int nAutosaveInterval);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `dwRestartManagerSupportFlags`|指出哪些選項重新啟動管理員支援。|  
|[in] `nAutosaveInterval`|時，自動儲存之間的時間。 這個參數是以毫秒為單位。|  
  
### <a name="remarks"></a>備註  
 MFC 架構會自動建立`CDataRecoveryHandler`當您使用您的應用程式物件**新的專案**精靈。 除非您要自訂的資料復原問題或重新啟動管理員，您不應該建立`CDataRecoveryHandler`物件。  
  
  
##  <a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo  
 將文件加入至開啟的文件的清單。  
  
```  
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pDocument`|指標`CDocument`。 這個方法會建立這個文件資訊`CDocument`。|  
  
### <a name="return-value"></a>傳回值  
 預設實作會傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 如果這個方法會檢查`pDocument`已在文件清單再增加文件。 如果`pDocument`已經在清單中，這個方法與 autosaved 檔案關聯的刪除`pDocument`。  
  
 若要使用這個方法，或是`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL`必須在設定`m_dwRestartManagerSupportFlags`。 
  
##  <a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles  
 刪除所有目前的 autosaved 檔案。  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>傳回值  
 預設實作一定會傳回`TRUE`。  
  
##  <a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile  
 刪除指定的 autosaved 檔案。  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `strAutosavedFile`|包含 autosaved 檔案名稱的字串。|  
  
### <a name="return-value"></a>傳回值  
 預設實作永遠會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 如果這個方法無法刪除 autosaved 檔案，它會儲存在清單中的檔案名稱。 解構函式的`CDataRecoveryHandler`嘗試刪除該清單中指定每個 autosaved 檔案。  
  
##  <a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName  
 會產生與提供的文件檔案名稱相關聯的自動儲存檔案的名稱。  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `strDocumentName`  
 包含文件名稱的字串。 `GenerateAutosaveFileName`使用此文件名稱產生對應的自動儲存檔案名稱。  
  
### <a name="return-value"></a>傳回值  
 從產生的自動儲存檔案名稱`strDocumentName`。  
  
### <a name="remarks"></a>備註  
 每個文件名稱有一對一的對應，以自動儲存檔案名稱。  
  
##  <a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval  
 傳回伺服器會自動嘗試之間的間隔。  
  
```  
virtual int GetAutosaveInterval() const;  
```  
  
### <a name="return-value"></a>傳回值  
 會嘗試自動儲存之間的毫秒數。  
  
##  <a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath  
 傳回 autosaved 檔案的路徑。  
  
```  
virtual CString GetAutosavePath() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Autosaved 文件儲存位置。  
  
##  <a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName  
 擷取的文件名稱`CDocument`物件。  
  
```  
virtual CString GetDocumentListName(CDocument* pDocument) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pDocument`|指標`CDocument`。 `GetDocumentListName`從這個擷取的文件名稱`CDocument`。|  
  
### <a name="return-value"></a>傳回值  
 文件名稱，從`pDocument`。  
  
### <a name="remarks"></a>備註  
 `CDataRecoveryHandler`使用文件名稱做為金鑰`m_mapDocNameToAutosaveName`， `m_mapDocNameToDocumentPtr`，和`m_mapDocNameToRestoreBool`。 這些參數啟用`CDataRecoveryHandler`監視`CDocument`物件、 自動儲存檔案名稱，以及自動儲存設定。  
  
##  <a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle  
 擷取指定的文件的一般標題。  
  
```  
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pDocument`|指標`CDocument`。|  
  
### <a name="return-value"></a>傳回值  
 指定文件標準的標題。  
  
### <a name="remarks"></a>備註  
 一般文件的標題通常是不包含路徑的文件的檔案名稱。 這是在標題**檔案名稱**欄位**另存新檔**對話方塊。  
  
##  <a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle  
 建立並傳回復原的文件的標題。  
  
```  
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `strDocumentTitle`  
 一般文件的標題。  
  
### <a name="return-value"></a>傳回值  
 復原的文件標題。  
  
### <a name="remarks"></a>備註  
 根據預設，復原文件的標題是一般的標題與**[復原]**附加到它。 復原的標題會顯示給使用者時`CDataRecoveryHandler`會要求使用者還原 autosaved 文件。  
  
##  <a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier  
 擷取應用程式重新啟動唯一識別項。  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>傳回值  
 重新啟動唯一識別項。  
  
### <a name="remarks"></a>備註  
 重新啟動識別碼是每次執行的應用程式唯一的。  
  
 `CDataRecoveryHandler`儲存在登錄中目前開啟的文件的相關資訊。 當重新啟動管理員結束應用程式並將它重新啟動時，會提供重新啟動識別碼`CDataRecoveryHandler`。 `CDataRecoveryHandler`使用重新啟動識別項來擷取先前開啟的文件的清單。 這可讓`CDataRecoveryHandler`嘗試尋找並還原 autosaved 檔案。  
  
##  <a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 指出是否`CDataRecoveryHandler`執行自動儲存在目前的閒置迴圈。  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`指出`CDataRecoveryHandler`時，自動儲存在目前的閒置迴圈。`FALSE`表示它並不會。  
  
##  <a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager  
 指出重新啟動管理員是否會造成應用程式結束。  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`指出重新啟動管理員造成應用程式結束。`FALSE`表示它不提供支援。  
  
##  <a name="initialize"></a>CDataRecoveryHandler::Initialize  
 初始化 `CDataRecoveryHandler`。  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果初始化成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 初始化處理程序載入路徑來存放從登錄自動儲存檔案。 如果`Initialize`方法找不到此目錄，或者如果路徑是`NULL`，`Initialize`失敗，並傳回`FALSE`。  
  
 使用[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)在應用程式初始化後，變更自動儲存路徑`CDataRecoveryHandler`。  
  
 `Initialize`方法也會啟動下一個自動儲存事件時所要監視的計時器。 使用[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)在應用程式初始化後，變更自動儲存間隔`CDataRecoveryHandler`。  
  
##  <a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 向使用者顯示對話方塊中的每個文件`CDataRecoveryHandler`autosaved。 對話方塊中，決定使用者是否想要還原 autosaved 文件。  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>備註  
 如果您的應用程式是 Unicode，這個方法會顯示[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)給使用者。 否則，架構會使用[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)向使用者查詢。  
  
 之後`QueryRestoreAutosavedDocuments`會收集所有回應，不讓使用者將資訊儲存在成員變數`m_mapDocNameToRestoreBool`。 這個方法不會還原 autosaved 文件。  
  
##  <a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList  
 從登錄載入開啟的文件清單。  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`表示`ReadOpenDocumentList`載入至少一個文件的資訊從登錄中。`FALSE`上次載入任何文件資訊。  
  
### <a name="remarks"></a>備註  
 此函式會從登錄載入開啟的文件資訊，並將它儲存在成員變數`m_mapDocNameToAutosaveName`。  
  
 之後`ReadOpenDocumentList`載入所有資料時，它會從登錄中刪除文件資訊。  
  
##  <a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo  
 從開啟的文件清單中移除提供的文件。  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pDocument`|若要移除文件指標。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`pDocument`已從清單中移除`FALSE`發生錯誤。  
  
### <a name="remarks"></a>備註  
 當使用者關閉文件時，架構會使用這個方法來從開啟的文件清單中移除。  
  
 如果`RemoveDocumentInfo`找不到`pDocument`在開啟的文件清單中，它不做任何動作，並傳回`TRUE`。  
  
 若要使用這個方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`必須在設定`m_dwRestartManagerSupportFlags`。   
  
##  <a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments  
 開啟先前開啟的文件。  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已開啟一個以上的文件。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會開啟先前開啟的文件的最新的儲存。 如果不儲存文件或 autosaved，`ReopenPreviousDocuments`開啟該檔案類型的範本為基礎的空白文件。  
  
 若要使用這個方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`必須在設定`m_dwRestartManagerSupportFlags`。 如果未設定此參數，`ReopenPreviousDocuments`不做任何動作，並傳回`FALSE`。  
  
 如果沒有儲存先前開啟的文件的清單中的文件`ReopenPreviousDocuments`不做任何動作，並傳回`FALSE`。  
  
##  <a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments  
 還原根據使用者輸入的 autosaved 文件。  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果這個方法已成功還原這些文件。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)來判斷其文件使用者想要還原。 如果使用者決定不還原 autosaved 文件`RestoreAutosavedDocuments`刪除自動儲存檔案。 否則，`RestoreAutosavedDocuments`取代 autosaved 版本中開啟的文件。  
  
 若要使用這個方法，或是`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`或`AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`必須在設定`m_dwRestartManagerSupportFlags`。   
  
##  <a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList  
 Windows 登錄中儲存目前開啟的文件的清單。  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果沒有儲存開啟的文件，或它們已成功儲存。 `FALSE`如果文件儲存至登錄，但它們所不儲存，因為發生錯誤。  
  
### <a name="remarks"></a>備註  
 重新啟動管理員呼叫`SaveOpenDocumentList`應用程式時意外結束，或便會結束升級。 當應用程式重新啟動時，它會使用[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)擷取開啟的文件的清單。  
  
 這個方法會儲存開啟的文件的清單。 此方法[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)負責儲存文件本身。  
  
##  <a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval  
 設定以毫秒為單位的自動儲存循環之間的時間。  
  
```  
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```  
  
### <a name="parameters"></a>參數  
 [in] `nAutosaveInterval`  
 新的自動儲存間隔 （毫秒）。  
  
##  <a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath  
 設定儲存 autosaved 檔案的目錄。  
  
```  
virtual void SetAutosavePath(const CString& strAutosavePath);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `strAutosavePath`|儲存自動儲存檔案的路徑。|  
  
### <a name="remarks"></a>備註  
 變更自動儲存目錄不會移動目前 autosaved 檔案。  
  
##  <a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier  
 設定這個執行個體的唯一重新啟動識別碼`CDataRecoveryHandler`。  
  
```  
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `strRestartIdentifier`|重新啟動管理員唯一識別項。|  
  
### <a name="remarks"></a>備註  
 重新啟動管理員會記錄在登錄中開啟的文件的相關資訊。 這項資訊會儲存與重新啟動唯一識別項，做為索引鍵。 重新啟動識別項是唯一的應用程式的每個執行個體，因為應用程式的多個執行個體可能會意外結束並重新啟動管理員可以復原每一種。  
  
##  <a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle  
 設定是否`CDataRecoveryHandler`目前閒置週期期間，將開啟的文件資訊儲存至 Windows 登錄。  
  
```  
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `bSaveOnIdle`|`TRUE`若要儲存文件資訊在目前的閒置週期。`FALSE to not perform a save`.|  
  
##  <a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager  
 設定是否重新啟動管理員所造成的應用程式之前結束。  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `bShutdownByRestartManager`|`TRUE`表示重新啟動管理員造成應用程式結束。`FALSE`表示應用程式已結束，因為其他原因。|  
  
### <a name="remarks"></a>備註  
 架構的行為方式根據前一個結束是否已非預期或由重新啟動管理員來啟動。  
  
##  <a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo  
 因為使用者儲存它，請更新文件的資訊。  
  
```  
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pDocument`|儲存的文件指標。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法刪除 autosaved 文件，並更新文件資訊。`FALSE`發生錯誤。  
  
### <a name="remarks"></a>備註  
 當使用者儲存文件時，應用程式會移除 autosaved 檔案，因為已不再需要它。 `UpdateDocumentInfo`藉由呼叫刪除 autosaved 檔案[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)。 `UpdateDocumentInfo`然後將資訊從新增`pDocument`清單目前開啟文件因為`RemoveDocumentInfo`刪除此資訊，但已儲存文件仍為開啟狀態。  
  
 若要使用這個方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`必須在設定`m_dwRestartManagerSupportFlags`。   
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [如何︰ 加入重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)


