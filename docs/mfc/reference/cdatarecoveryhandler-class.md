---
title: CDataRecoveryHandler 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7eedad2e1efb72d85da893764fbd1201b9ac4b3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417276"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler 類別

`CDataRecoveryHandler`時，自動儲存文件，並將它們還原，如果應用程式意外結束。

## <a name="syntax"></a>語法

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>成員

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
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|刪除所有目前的會檔案。|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|刪除指定的會檔案。|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|會產生與提供的文件檔案名稱相關聯的自動儲存檔案的名稱。|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|傳回自動儲存嘗試之間的間隔。|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|傳回會檔案的路徑。|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|擷取的文件名稱`CDocument`物件。|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|擷取指定的文件的一般標題。|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|建立並傳回已復原的文件的標題。|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|擷取應用程式的重新啟動唯一識別碼。|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|指出是否`CDataRecoveryHandler`目前閒置迴圈上執行自動儲存。|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|指出是否重新啟動管理員造成應用程式結束。|
|[CDataRecoveryHandler::Initialize](#initialize)|初始化 `CDataRecoveryHandler`。|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|向使用者顯示的對話方塊中的每個文件，`CDataRecoveryHandler`會。 對話方塊會決定使用者是否想要還原會文件。|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|從登錄載入開啟的文件清單。|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|從開啟的文件清單中移除提供的文件。|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|會開啟先前開啟的文件。|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|根據使用者輸入會文件，會還原。|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|將目前開啟的文件的清單儲存至 Windows 登錄中。|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|設定以毫秒為單位的自動儲存循環之間的時間。|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|設定會檔案儲存所在的目錄。|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|設定這個執行個體的唯一的重新啟動識別碼`CDataRecoveryHandler`。|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|設定是否`CDataRecoveryHandler`將開啟的文件資訊儲存至 Windows 登錄中，目前閒置的循環期間。|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|設定是否重新啟動管理員所造成的應用程式先前的結束。|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|因為儲存它的使用者，請更新文件的資訊。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|m_bRestoringPreviousOpenDocs|表示資料復原處理常式是否要重新開啟先前開啟的文件。|
|m_bSaveDocumentInfoOnIdle|指出是否在下一步 的閒置迴圈上的資料復原處理常式時，自動儲存文件。|
|m_bShutdownByRestartManager|指出是否重新啟動管理員會導致應用程式結束。|
|m_dwRestartManagerSupportFlags|旗標，表示項目支援重新啟動管理員提供應用程式。|
|m_lstAutosavesToDelete|會與原始文件已關閉時未刪除的檔案清單。 應用程式結束時，重新啟動管理員重試刪除檔案。|
|m_mapDocNameToAutosaveName|會檔案名稱之文件名稱的對應。|
|m_mapDocNameToDocumentPtr|文件名稱的對應[CDocument](../../mfc/reference/cdocument-class.md)指標。|
|m_mapDocNameToRestoreBool|布林值參數，指出是否要還原會文件之文件名稱的對應。|
|m_mapDocumentPtrToDocName|對應`CDocument`文件名稱的指標。|
|m_mapDocumentPtrToDocTitle|對應`CDocument`文件標題的指標。 這些項目用來儲存檔案。|
|m_nAutosaveInterval|時間 （毫秒） 之間時，自動儲存。|
|m_nTimerID|自動儲存計時器識別項。|
|m_strAutosavePath|儲存會文件位置。|
|m_strRestartIdentifier|重新啟動管理員 GUID 的字串表示。|

## <a name="remarks"></a>備註

重新啟動管理員會使用`CDataRecoveryHandler`類別，以記錄所有開啟的文件，並自動儲存其當做追蹤必要。 若要啟用自動儲存，請使用[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)方法。 這個方法會指示`CDataRecoveryHandler`下一步 的閒置迴圈上執行自動儲存。 重新啟動管理員呼叫`SetSaveDocumentInfoOnIdle`當`CDataRecoveryHandler`應該執行自動儲存。

所有的方法`CDataRecoveryHandler`類別都是虛擬的。 覆寫這個類別來建立您自己自訂的資料復原處理常式中的方法。 除非您建立您自己的資料復原處理常式，或重新啟動管理員，否則請勿執行個體化 CDataRecoveryHandler。 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)建立`CDataRecoveryHandler`為需要的物件。

您可以使用之前`CDataRecoveryHandler`物件，您必須呼叫[CDataRecoveryHandler::Initialize](#initialize)。

因為`CDataRecoveryHandler`類別緊密連接以重新啟動管理員 中，`CDataRecoveryHandler`取決於全域參數`m_dwRestartManagerSupportFlags`。 這個參數會決定重新啟動管理員有哪些權限，以及它如何與您的應用程式互動。 若要重新啟動管理員併入現有的應用程式中，您必須指派`m_dwRestartManagerSupportFlags`中主應用程式的建構函式的適當值。 如需如何使用重新啟動管理員的詳細資訊，請參閱[如何： 加入重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)。

## <a name="requirements"></a>需求

**標頭：** afxdatarecovery.h

##  <a name="autosavealldocumentinfo"></a>  CDataRecoveryHandler::AutosaveAllDocumentInfo

使用註冊的每個檔案時，自動儲存`CDataRecoveryHandler`類別。

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>傳回值

如果`CDataRecoveryHandler`儲存所有文件;如果未儲存任何文件，則為 FALSE。

### <a name="remarks"></a>備註

如果不有任何必須儲存的文件，這個方法會傳回 TRUE。 它也會傳回 TRUE 而不儲存任何文件，如果擷取`CWinApp`或`CDocManager`應用程式會產生錯誤。

若要使用這個方法，AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL 必須設定`m_dwRestartManagerSupportFlags`。 請參閱[m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)如需詳細資訊。

##  <a name="autosavedocumentinfo"></a>  CDataRecoveryHandler::AutosaveDocumentInfo

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
|*pDocument*|[in]指標`CDocument`儲存。|
|*bResetModifiedFlag*|[in]TRUE 表示`CDataRecoveryHandler`考慮*pDocument*修改;FALSE 表示此架構會考慮*pDocument*是未修改。 請參閱 < 備註 > 一節這個旗標的效果的詳細資訊。|

### <a name="return-value"></a>傳回值

如果設定了適當的旗標，則為 TRUE 並*pDocument*有效`CDocument`物件。

### <a name="remarks"></a>備註

每個`CDocument`物件具有旗標，指出是否已變更從上次儲存之後。 使用[CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified)來判斷這個旗標的狀態。 如果`CDocument`最後一個檔案中之後, 並未變更`AutosaveDocumentInfo`會刪除任何會檔案，該文件。 如果文件已經從上次儲存後變更，關閉它會提示使用者儲存文件關閉之前。

> [!NOTE]
>  使用*bResetModifiedFlag*將文件的狀態變更為未修改可能會導致使用者遺失未儲存的資料。 如果架構認為未經修改的文件，關閉它不會提示使用者儲存。

這個方法會擲回的例外狀況[ASSERT](diagnostic-services.md#assert)巨集如果*pDocument*不是有效`CDocument`物件。

若要使用這個方法，AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL 必須設定*m_dwRestartManagerSupportFlags*。

##  <a name="cdatarecoveryhandler"></a>  CDataRecoveryHandler::CDataRecoveryHandler

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
|*dwRestartManagerSupportFlags*|[in]指出哪一個選項，重新啟動管理員支援。|
|*nAutosaveInterval*|[in]時，自動儲存之間的時間。 這個參數是以毫秒為單位。|

### <a name="remarks"></a>備註

MFC 架構會自動建立`CDataRecoveryHandler`當您使用您的應用程式的物件**新的專案**精靈。 除非您要自訂的資料復原行為或重新啟動管理員，您不應建立`CDataRecoveryHandler`物件。


##  <a name="createdocumentinfo"></a>  CDataRecoveryHandler::CreateDocumentInfo

將文件加入至開啟的文件的清單。

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[in]指標`CDocument`。 這個方法會建立此文件資訊`CDocument`。|

### <a name="return-value"></a>傳回值

預設實作會傳回 TRUE。

### <a name="remarks"></a>備註

這個方法會檢查是否*pDocument*再予以新增文件已經是在這份文件。 如果*pDocument*已在清單中，這個方法會檔案相關聯的刪除*pDocument*。

若要使用這個方法，AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL 必須設定*m_dwRestartManagerSupportFlags*。

##  <a name="deleteallautosavedfiles"></a>  CDataRecoveryHandler::DeleteAllAutosavedFiles

刪除所有目前的會檔案。

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>傳回值

預設實作永遠傳回 TRUE。

##  <a name="deleteautosavedfile"></a>  CDataRecoveryHandler::DeleteAutosavedFile

刪除指定的會檔案。

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*strAutosavedFile*|[in]包含會檔案名稱的字串。|

### <a name="return-value"></a>傳回值

預設實作永遠傳回 TRUE。

### <a name="remarks"></a>備註

如果這個方法無法刪除會檔案，它會將檔案的名稱儲存在清單中。 解構函式`CDataRecoveryHandler`嘗試刪除該清單中指定每個會檔案。

##  <a name="generateautosavefilename"></a>  CDataRecoveryHandler::GenerateAutosaveFileName

會產生與提供的文件檔案名稱相關聯的自動儲存檔案的名稱。

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>參數

*strDocumentName*<br/>
[in]包含文件名稱的字串。 `GenerateAutosaveFileName` 您可以使用此文件名稱來產生對應的自動儲存檔案名稱。

### <a name="return-value"></a>傳回值

從產生的自動儲存檔案名稱*strDocumentName*。

### <a name="remarks"></a>備註

每個文件名稱會有一對一的對應，並有自動儲存檔案名稱。

##  <a name="getautosaveinterval"></a>  CDataRecoveryHandler::GetAutosaveInterval

傳回自動儲存嘗試之間的間隔。

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>傳回值

會嘗試自動儲存之間的毫秒數。

##  <a name="getautosavepath"></a>  CDataRecoveryHandler::GetAutosavePath

傳回會檔案的路徑。

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>傳回值

儲存會文件位置。

##  <a name="getdocumentlistname"></a>  CDataRecoveryHandler::GetDocumentListName

擷取的文件名稱`CDocument`物件。

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[in]指標`CDocument`。 `GetDocumentListName` 這會擷取文件名稱`CDocument`。|

### <a name="return-value"></a>傳回值

中的文件名稱*pDocument*。

### <a name="remarks"></a>備註

`CDataRecoveryHandler`文件名稱做為中的索引鍵*m_mapDocNameToAutosaveName*， *m_mapDocNameToDocumentPtr*，和*m_mapDocNameToRestoreBool*。 這些參數會啟用`CDataRecoveryHandler`監視`CDocument`物件、 自動儲存檔案名稱和自動儲存設定。

##  <a name="getnormaldocumenttitle"></a>  CDataRecoveryHandler::GetNormalDocumentTitle

擷取指定的文件的一般標題。

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[in]指標`CDocument`。|

### <a name="return-value"></a>傳回值

指定的文件一般標題。

### <a name="remarks"></a>備註

一般文件的標題通常是不含路徑的文件的檔案名稱。 這是中的項目**檔名**欄位**另存新檔** 對話方塊。

##  <a name="getrecovereddocumenttitle"></a>  CDataRecoveryHandler::GetRecoveredDocumentTitle

建立並傳回已復原的文件的標題。

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>參數

*strDocumentTitle*<br/>
[in]一般文件標題。

### <a name="return-value"></a>傳回值

復原後的文件標題。

### <a name="remarks"></a>備註

根據預設，復原文件的標題是以一般的標題 **[已復原]** 附加到它。 復原的標題會顯示給使用者時`CDataRecoveryHandler`查詢使用者還原會文件。

##  <a name="getrestartidentifier"></a>  CDataRecoveryHandler::GetRestartIdentifier

擷取應用程式的重新啟動唯一識別碼。

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>傳回值

唯一的重新啟動的識別項。

### <a name="remarks"></a>備註

重新啟動識別碼是唯一的應用程式每次執行。

`CDataRecoveryHandler`會儲存在登錄中目前開啟的文件相關的資訊。 當重新啟動管理員會結束應用程式，並將它重新啟動時，它提供的重新啟動識別碼`CDataRecoveryHandler`。 `CDataRecoveryHandler`會使用重新啟動識別碼來擷取先前開啟的文件的清單。 這可讓`CDataRecoveryHandler`嘗試尋找並還原會檔案。

##  <a name="getsavedocumentinfoonidle"></a>  CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

指出是否`CDataRecoveryHandler`目前閒置迴圈上執行自動儲存。

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示`CDataRecoveryHandler`上目前的閒置迴圈; 時，自動儲存FALSE 表示它並不會。

##  <a name="getshutdownbyrestartmanager"></a>  CDataRecoveryHandler::GetShutdownByRestartManager

指出是否重新啟動管理員造成應用程式結束。

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示重新啟動管理員造成應用程式結束。FALSE 表示它不提供支援。

##  <a name="initialize"></a>  CDataRecoveryHandler::Initialize

初始化 `CDataRecoveryHandler`。

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>傳回值

如果初始化成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

初始化處理程序載入路徑來存放從登錄自動儲存檔案。 如果`Initialize`方法找不到此目錄，或若路徑會是 NULL，`Initialize`會失敗並傳回`FALSE`。

使用[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)在應用程式初始化之後，變更自動儲存路徑`CDataRecoveryHandler`。

`Initialize`方法也會啟動計時器來監視何時發生下一步 自動儲存。 使用[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)來變更自動儲存間隔之後您的應用程式初始化, `CDataRecoveryHandler`。

##  <a name="queryrestoreautosaveddocuments"></a>  CDataRecoveryHandler::QueryRestoreAutosavedDocuments

向使用者顯示的對話方塊中的每個文件，`CDataRecoveryHandler`會。 對話方塊會決定使用者是否想要還原會文件。

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>備註

如果您的應用程式是 Unicode，這個方法會顯示[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)給使用者。 否則，架構會使用[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)向使用者查詢。

在後`QueryRestoreAutosavedDocuments`會收集所有回應，不讓使用者將資訊儲存在成員變數*m_mapDocNameToRestoreBool*。 這個方法不會還原會文件。

##  <a name="readopendocumentlist"></a>  CDataRecoveryHandler::ReadOpenDocumentList

從登錄載入開啟的文件清單。

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>傳回值

TRUE 表示`ReadOpenDocumentList`從登錄載入至少一份文件的資訊FALSE 表示載入任何文件資訊。

### <a name="remarks"></a>備註

此函式會從登錄載入所開啟的文件資訊，並將它儲存在成員變數*m_mapDocNameToAutosaveName*。

之後`ReadOpenDocumentList`載入所有資料時，它會從登錄中刪除文件資訊。

##  <a name="removedocumentinfo"></a>  CDataRecoveryHandler::RemoveDocumentInfo

從開啟的文件清單中移除提供的文件。

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[in]要移除文件指標。|

### <a name="return-value"></a>傳回值

則為 TRUE *pDocument*已從清單移除如果發生錯誤，則為 FALSE。

### <a name="remarks"></a>備註

當使用者關閉文件時，架構會使用從開啟的文件的清單中移除這個方法。

如果`RemoveDocumentInfo`找不到*pDocument*在開啟的文件清單中，它不執行任何動作，則傳回 TRUE。

必須在中設定要使用此方法，AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*。

##  <a name="reopenpreviousdocuments"></a>  CDataRecoveryHandler::ReopenPreviousDocuments

會開啟先前開啟的文件。

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>傳回值

如果至少一個文件已開啟，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會開啟先前開啟的文件的最新的儲存。 如果未儲存的文件或會，`ReopenPreviousDocuments`開啟該檔案類型的範本為基礎的空白文件。

必須在中設定要使用此方法，AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*。 如果未設定此參數，`ReopenPreviousDocuments`不執行任何動作且會傳回 FALSE。

如果沒有儲存在先前開啟的文件，這份文件`ReopenPreviousDocuments`不執行任何動作且會傳回 FALSE。

##  <a name="restoreautosaveddocuments"></a>  CDataRecoveryHandler::RestoreAutosavedDocuments

根據使用者輸入會文件，會還原。

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>傳回值

這個方法已成功還原文件，其值為 TRUE。

### <a name="remarks"></a>備註

這個方法會呼叫[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)來判斷此文件的使用者想要還原。 如果使用者決定不會文件中，還原`RestoreAutosavedDocuments`刪除自動儲存檔案。 否則，`RestoreAutosavedDocuments`取代會版本中開啟的文件。

若要使用這個方法，AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 或 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 必須設定`m_dwRestartManagerSupportFlags`。

##  <a name="saveopendocumentlist"></a>  CDataRecoveryHandler::SaveOpenDocumentList

將目前開啟的文件的清單儲存至 Windows 登錄中。

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>傳回值

如果不有任何開啟的文件儲存，或如果他們已成功儲存，則為 TRUE。 如果有文件儲存至登錄，但它們未儲存，因為發生錯誤，則為 FALSE。

### <a name="remarks"></a>備註

重新啟動管理員呼叫`SaveOpenDocumentList`應用程式時非預期地結束或便會結束升級。 當應用程式重新啟動時，它會使用[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)擷取開啟的文件的清單。

這個方法會將儲存開啟的文件的清單。 此方法[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)負責儲存文件本身。

##  <a name="setautosaveinterval"></a>  CDataRecoveryHandler::SetAutosaveInterval

設定以毫秒為單位的自動儲存循環之間的時間。

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>參數

*nAutosaveInterval*<br/>
[in]以毫秒為單位，新的自動儲存間隔。

##  <a name="setautosavepath"></a>  CDataRecoveryHandler::SetAutosavePath

設定會檔案儲存所在的目錄。

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*strAutosavePath*|[in]儲存自動儲存檔案的路徑。|

### <a name="remarks"></a>備註

變更自動儲存目錄不會移動目前會檔案。

##  <a name="setrestartidentifier"></a>  CDataRecoveryHandler::SetRestartIdentifier

設定這個執行個體的唯一的重新啟動識別碼`CDataRecoveryHandler`。

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*strRestartIdentifier*|[in]重新啟動管理員唯一識別項。|

### <a name="remarks"></a>備註

重新啟動管理員會記錄在登錄中開啟的文件的相關資訊。 這項資訊會儲存具有唯一的重新啟動識別項，做為索引鍵。 重新啟動識別碼是唯一的應用程式的每個執行個體，因為應用程式的多個執行個體可能會意外結束，並重新啟動管理員可以復原每個。

##  <a name="setsavedocumentinfoonidle"></a>  CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

設定是否`CDataRecoveryHandler`將開啟的文件資訊儲存至 Windows 登錄中，目前閒置的循環期間。

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*bSaveOnIdle*|[in]若要儲存在目前的閒置週期; 文件資訊，則為 TRUE如果為 false，則不會執行儲存。|

##  <a name="setshutdownbyrestartmanager"></a>  CDataRecoveryHandler::SetShutdownByRestartManager

設定是否重新啟動管理員所造成的應用程式先前的結束。

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*bShutdownByRestartManager*|[in]TRUE 表示重新啟動管理員造成應用程式結束。如果為 false，則表示應用程式已結束，因為其他原因。|

### <a name="remarks"></a>備註

Framework 的行為會根據前一個結束是否非預期或由重新啟動管理員來啟動。

##  <a name="updatedocumentinfo"></a>  CDataRecoveryHandler::UpdateDocumentInfo

因為儲存它的使用者，請更新文件的資訊。

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[in]儲存的文件指標。|

### <a name="return-value"></a>傳回值

如果此方法刪除會文件，且更新過的文件資訊;，則為 TRUE。如果發生錯誤，則為 FALSE。

### <a name="remarks"></a>備註

當使用者儲存文件時，應用程式會移除會檔案，因為不再需要它。 `UpdateDocumentInfo` 刪除檔案會藉由呼叫[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)。 `UpdateDocumentInfo` 然後將新增的資訊*pDocument*清單中的目前開啟文件因為`RemoveDocumentInfo`刪除該資訊，但已儲存文件仍為開啟狀態。

必須在中設定要使用此方法，AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[如何：新增重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)

