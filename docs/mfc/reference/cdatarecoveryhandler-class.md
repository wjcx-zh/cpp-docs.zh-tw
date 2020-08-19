---
title: CDataRecoveryHandler 類別
ms.date: 03/27/2019
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
ms.openlocfilehash: c796f24ad37b3bae11314e2885bf25e25f85aba6
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561969"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler 類別

`CDataRecoveryHandler`當應用程式意外結束時，autosaves 會記錄並還原它們。

## <a name="syntax"></a>語法

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[CDataRecoveryHandler：： CDataRecoveryHandler](#cdatarecoveryhandler)|建構 `CDataRecoveryHandler` 物件。|

### <a name="methods"></a>方法

|||
|-|-|
|[CDataRecoveryHandler：： AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Autosaves 每個以類別註冊的檔案 `CDataRecoveryHandler` 。|
|[CDataRecoveryHandler：： AutosaveDocumentInfo](#autosavedocumentinfo)|Autosaves 指定的檔。|
|[CDataRecoveryHandler：： CreateDocumentInfo](#createdocumentinfo)|將檔新增至開啟的檔案清單。|
|[CDataRecoveryHandler：:D eleteAllAutosavedFiles](#deleteallautosavedfiles)|刪除所有目前自動儲存的檔案。|
|[CDataRecoveryHandler：:D eleteAutosavedFile](#deleteautosavedfile)|刪除指定的自動儲存檔案。|
|[CDataRecoveryHandler：： GenerateAutosaveFileName](#generateautosavefilename)|產生與所提供檔檔案名相關聯之自動儲存檔案的名稱。|
|[CDataRecoveryHandler：： GetAutosaveInterval](#getautosaveinterval)|傳回自動儲存嘗試之間的間隔。|
|[CDataRecoveryHandler：： GetAutosavePath](#getautosavepath)|傳回自動儲存之檔案的路徑。|
|[CDataRecoveryHandler：： GetDocumentListName](#getdocumentlistname)|從物件捕獲檔案名稱 `CDocument` 。|
|[CDataRecoveryHandler：： GetNormalDocumentTitle](#getnormaldocumenttitle)|抓取指定檔的一般標題。|
|[CDataRecoveryHandler：： GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|建立並傳回已復原檔的標題。|
|[CDataRecoveryHandler：： GetRestartIdentifier](#getrestartidentifier)|抓取應用程式的唯一重新開機識別碼。|
|[CDataRecoveryHandler：： GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|指出是否會 `CDataRecoveryHandler` 在目前的閒置迴圈上執行自動儲存。|
|[CDataRecoveryHandler：： GetShutdownByRestartManager](#getshutdownbyrestartmanager)|指出重新開機管理員是否造成應用程式結束。|
|[CDataRecoveryHandler：： Initialize](#initialize)|初始化 `CDataRecoveryHandler`。|
|[CDataRecoveryHandler：： QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|針對已自動儲存的每份檔，向使用者顯示對話方塊 `CDataRecoveryHandler` 。 對話方塊會判斷使用者是否想要還原自動儲存的檔。|
|[CDataRecoveryHandler：： ReadOpenDocumentList](#readopendocumentlist)|從登錄載入開啟的檔案清單。|
|[CDataRecoveryHandler：： RemoveDocumentInfo](#removedocumentinfo)|從開啟的檔案清單中移除提供的檔。|
|[CDataRecoveryHandler：： ReopenPreviousDocuments](#reopenpreviousdocuments)|開啟先前開啟的檔。|
|[CDataRecoveryHandler：： RestoreAutosavedDocuments](#restoreautosaveddocuments)|根據使用者輸入來還原自動儲存的檔。|
|[CDataRecoveryHandler：： SaveOpenDocumentList](#saveopendocumentlist)|將目前開啟的檔案清單儲存至 Windows 登錄。|
|[CDataRecoveryHandler：： SetAutosaveInterval](#setautosaveinterval)|設定自動儲存迴圈之間的時間（以毫秒為單位）。|
|[CDataRecoveryHandler：： SetAutosavePath](#setautosavepath)|設定儲存自動儲存檔案的目錄。|
|[CDataRecoveryHandler：： SetRestartIdentifier](#setrestartidentifier)|設定這個實例的唯一重新開機識別碼 `CDataRecoveryHandler` 。|
|[CDataRecoveryHandler：： SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|設定是否在 `CDataRecoveryHandler` 目前的閒置週期期間，將開啟的檔資訊儲存至 Windows 登錄。|
|[CDataRecoveryHandler：： SetShutdownByRestartManager](#setshutdownbyrestartmanager)|設定重新開機管理員是否造成先前的應用程式結束。|
|[CDataRecoveryHandler：： UpdateDocumentInfo](#updatedocumentinfo)|更新檔的資訊，因為使用者已儲存檔。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|m_bRestoringPreviousOpenDocs|指出資料恢復處理常式是否重新開啟先前開啟的檔。|
|m_bSaveDocumentInfoOnIdle|指出資料恢復處理常式是否 autosaves 下一個閒置迴圈的檔。|
|m_bShutdownByRestartManager|指出重新開機管理員是否造成應用程式結束。|
|m_dwRestartManagerSupportFlags|旗標，指出重新開機管理員為應用程式提供的支援。|
|m_lstAutosavesToDelete|當原始檔案關閉時，未刪除的自動儲存檔案清單。 當應用程式結束時，重新開機管理員會重試刪除檔案。|
|m_mapDocNameToAutosaveName|檔案名稱對應至自動儲存的檔案名。|
|m_mapDocNameToDocumentPtr|[CDocument](../../mfc/reference/cdocument-class.md)指標的檔案名稱對應。|
|m_mapDocNameToRestoreBool|將檔案名稱對應至布林值參數，指出是否要還原自動儲存的檔。|
|m_mapDocumentPtrToDocName|`CDocument`檔案名稱指標的對應。|
|m_mapDocumentPtrToDocTitle|`CDocument`檔標題的指標對應。 這些標題可用來儲存檔案。|
|m_nAutosaveInterval|Autosaves 之間的時間（以毫秒為單位）。|
|m_nTimerID|自動儲存計時器的識別碼。|
|m_strAutosavePath|儲存自動儲存之檔的位置。|
|m_strRestartIdentifier|重新開機管理員之 GUID 的字串表示。|

## <a name="remarks"></a>備註

重新開機管理員會使用 `CDataRecoveryHandler` 類別來追蹤所有開啟的檔，並視需要將它們自動儲存。 若要啟用自動儲存，請使用 [CDataRecoveryHandler：： SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) 方法。 這個方法會指示， `CDataRecoveryHandler` 以在下一個閒置迴圈執行自動儲存。 重新開機管理員 `SetSaveDocumentInfoOnIdle` `CDataRecoveryHandler` 會在應該執行自動儲存時呼叫。

類別的所有方法 `CDataRecoveryHandler` 都是虛擬的。 覆寫這個類別中的方法，以建立您自己的自訂資料恢復處理常式。 除非您建立自己的資料修復處理常式或重新開機管理員，否則請勿具現化 CDataRecoveryHandler。 [CWinApp 類別](../../mfc/reference/cwinapp-class.md) `CDataRecoveryHandler` 會視需要建立物件。

在您可以使用 `CDataRecoveryHandler` 物件之前，您必須先 [呼叫 CDataRecoveryHandler：： Initialize](#initialize)。

由於 `CDataRecoveryHandler` 類別會緊密地連接到重新開機管理員，因此 `CDataRecoveryHandler` 相依于全域參數 `m_dwRestartManagerSupportFlags` 。 此參數會決定重新開機管理員所擁有的許可權，以及與您的應用程式互動的方式。 若要將重新開機管理員併入現有的應用程式，您必須 `m_dwRestartManagerSupportFlags` 在主要應用程式的函式中指派適當的值。 如需如何使用重新開機管理員的詳細資訊，請參閱 [如何：新增重新開機管理員支援](../../mfc/how-to-add-restart-manager-support.md)。

## <a name="requirements"></a>規格需求

**標頭：** afxdatarecovery。h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a> CDataRecoveryHandler：： AutosaveAllDocumentInfo

Autosaves 每個以類別註冊的檔案 `CDataRecoveryHandler` 。

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>傳回值

如果儲存所有檔，則為 TRUE `CDataRecoveryHandler` ;如果未儲存任何檔，則為 FALSE。

### <a name="remarks"></a>備註

如果沒有必須儲存的檔，這個方法會傳回 TRUE。 如果抓取 `CWinApp` 或 `CDocManager` 應用程式產生錯誤，則它也會傳回 TRUE，而不會儲存任何檔。

若要使用這個方法，您必須在中設定 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL `m_dwRestartManagerSupportFlags` 。 如需詳細資訊，請參閱 [如何：新增重新開機管理員支援](../../mfc/how-to-add-restart-manager-support.md)。

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a> CDataRecoveryHandler：： AutosaveDocumentInfo

Autosaves 指定的檔。

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>參數

*pDocument*\
在要儲存之的指標 `CDocument` 。

*bResetModifiedFlag*\
在TRUE 表示 `CDataRecoveryHandler` 會考慮要修改的 *pDocument* ;FALSE 表示架構會將 *pDocument* 視為未修改。 如需此旗標效果的詳細資訊，請參閱「備註」一節。

### <a name="return-value"></a>傳回值

如果已設定適當的旗標，且 *pDocument* 為有效的物件，則為 TRUE `CDocument` 。

### <a name="remarks"></a>備註

每個 `CDocument` 物件都有旗標，指出上次儲存之後是否已變更。 使用 [CDocument：： IsModified](../../mfc/reference/cdocument-class.md#ismodified) 來判斷此旗標的狀態。 如果 `CDocument` 自上次儲存後未變更，則 `AutosaveDocumentInfo` 會刪除該檔的任何自動儲存檔案。 如果檔自上次儲存後已變更，則關閉它會在關閉前提示使用者儲存檔。

> [!NOTE]
> 使用 *bResetModifiedFlag* 將檔的狀態變更為未修改，可能會導致使用者遺失未儲存的資料。 如果架構將檔視為未修改，則關閉它並不會提示使用者進行儲存。

如果*pDocument*不是有效的物件，這個方法會擲回具有[ASSERT](diagnostic-services.md#assert)宏的例外狀況 `CDocument` 。

若要使用這個方法，必須在 *m_dwRestartManagerSupportFlags*中設定 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL。

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a> CDataRecoveryHandler：： CDataRecoveryHandler

建構 `CDataRecoveryHandler` 物件。

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>參數

*dwRestartManagerSupportFlags*\
在指出支援重新開機管理員的選項。

*nAutosaveInterval*\
在Autosaves 之間的時間。 這個參數是以毫秒為單位。

### <a name="remarks"></a>備註

`CDataRecoveryHandler`當您使用 [**新增專案**] 嚮導時，MFC 架構會自動為您的應用程式建立物件。 除非您要自訂資料修復行為或重新開機管理員，否則您不應該建立 `CDataRecoveryHandler` 物件。

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a> CDataRecoveryHandler：： CreateDocumentInfo

將檔新增至開啟的檔案清單。

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

*pDocument*\
在的指標 `CDocument` 。 這個方法會建立這個的檔資訊 `CDocument` 。

### <a name="return-value"></a>傳回值

預設的實值會傳回 TRUE。

### <a name="remarks"></a>備註

這個方法會先檢查 *pDocument* 是否已存在於檔案清單中，然後再新增檔。 如果 *pDocument* 已經在清單中，這個方法會刪除與 *pDocument*相關聯的自動儲存檔案。

若要使用這個方法，必須在 *m_dwRestartManagerSupportFlags*中設定 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL。

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a> CDataRecoveryHandler：:D eleteAllAutosavedFiles

刪除所有目前自動儲存的檔案。

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>傳回值

預設的實值一律會傳回 TRUE。

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a> CDataRecoveryHandler：:D eleteAutosavedFile

刪除指定的自動儲存檔案。

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>參數

*strAutosavedFile*\
在字串，其中包含自動檔案的檔案名。

### <a name="return-value"></a>傳回值

預設的實值一律會傳回 TRUE。

### <a name="remarks"></a>備註

如果這個方法無法刪除自動儲存的檔案，則會將檔案的名稱儲存在清單中。 的函式 `CDataRecoveryHandler` 會嘗試刪除該清單中指定的每個可保存的檔案。

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a> CDataRecoveryHandler：： GenerateAutosaveFileName

產生與所提供檔檔案名相關聯之自動儲存檔案的名稱。

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>參數

*strDocumentName*<br/>
在包含檔案名稱的字串。 `GenerateAutosaveFileName` 使用此檔案名稱來產生對應的自動儲存檔案名稱。

### <a name="return-value"></a>傳回值

從 *strDocumentName*產生的自動儲存檔案名稱。

### <a name="remarks"></a>備註

每個檔案名稱都有一個具有自動儲存檔案名的一對一對應。

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a> CDataRecoveryHandler：： GetAutosaveInterval

傳回自動儲存嘗試之間的間隔。

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>傳回值

自動儲存嘗試之間的毫秒數。

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a> CDataRecoveryHandler：： GetAutosavePath

傳回自動儲存之檔案的路徑。

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>傳回值

儲存自動儲存之檔的位置。

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a> CDataRecoveryHandler：： GetDocumentListName

從物件捕獲檔案名稱 `CDocument` 。

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>參數

*pDocument*\
在的指標 `CDocument` 。 `GetDocumentListName` 從此開始抓取檔案名稱 `CDocument` 。

### <a name="return-value"></a>傳回值

來自 *pDocument*的檔案名稱。

### <a name="remarks"></a>備註

會 `CDataRecoveryHandler` 使用檔案名稱做為 *m_mapDocNameToAutosaveName*、 *m_mapDocNameToDocumentPtr*和 *m_mapDocNameToRestoreBool*中的索引鍵。 這些參數可讓 `CDataRecoveryHandler` 監視 `CDocument` 物件、自動儲存檔案名稱和自動儲存設定。

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a> CDataRecoveryHandler：： GetNormalDocumentTitle

抓取指定檔的一般標題。

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>參數

*pDocument*\
在的指標 `CDocument` 。

### <a name="return-value"></a>傳回值

指定檔的一般標題。

### <a name="remarks"></a>備註

檔的一般標題通常是檔的檔案名，不含路徑。 這是 [**另存**新檔] 對話方塊的 [**檔案名**] 欄位中的標題。

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a> CDataRecoveryHandler：： GetRecoveredDocumentTitle

建立並傳回已復原檔的標題。

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>參數

*strDocumentTitle*<br/>
在檔的一般標題。

### <a name="return-value"></a>傳回值

復原的檔標題。

### <a name="remarks"></a>備註

根據預設，檔的復原標題為一般標題，並附加 **[已復原]** 。 當查詢使用者還原自動儲存的檔時，就會向使用者顯示覆原的標題 `CDataRecoveryHandler` 。

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a> CDataRecoveryHandler：： GetRestartIdentifier

抓取應用程式的唯一重新開機識別碼。

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>傳回值

唯一的重新開機識別碼。

### <a name="remarks"></a>備註

每次執行應用程式時，重新開機識別碼都是唯一的。

會在 `CDataRecoveryHandler` 登錄中儲存目前開啟之檔的相關資訊。 當重新開機管理員結束應用程式並重新啟動它時，它會將重新開機識別碼提供給 `CDataRecoveryHandler` 。 會 `CDataRecoveryHandler` 使用重新開機識別碼來取出先前開啟的檔案清單。 這可讓嘗試 `CDataRecoveryHandler` 尋找及還原自動儲存的檔案。

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a> CDataRecoveryHandler：： GetSaveDocumentInfoOnIdle

指出是否會 `CDataRecoveryHandler` 在目前的閒置迴圈上執行自動儲存。

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示 `CDataRecoveryHandler` 目前閒置迴圈上的 autosaves;FALSE 表示它不是。

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a> CDataRecoveryHandler：： GetShutdownByRestartManager

指出重新開機管理員是否造成應用程式結束。

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示重新開機管理員造成應用程式結束;FALSE 表示它不是。

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a> CDataRecoveryHandler：： Initialize

初始化 `CDataRecoveryHandler`。

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>傳回值

如果初始化成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

初始化程式會從登錄載入儲存自動儲存檔案的路徑。 如果 `Initialize` 方法找不到此目錄，或路徑為 Null，則 `Initialize` 會失敗並傳回 `FALSE` 。

在您的應用程式初始化之後，請使用 [CDataRecoveryHandler：： SetAutosavePath](#setautosavepath) 來變更自動儲存路徑 `CDataRecoveryHandler` 。

`Initialize`方法也會啟動計時器，以監視下次進行自動儲存的時間。 在應用程式初始化之後，使用 [CDataRecoveryHandler：： SetAutosaveInterval](#setautosaveinterval) 變更自動儲存間隔 `CDataRecoveryHandler` 。

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a> CDataRecoveryHandler：： QueryRestoreAutosavedDocuments

針對已自動儲存的每份檔，向使用者顯示對話方塊 `CDataRecoveryHandler` 。 對話方塊會判斷使用者是否想要還原自動儲存的檔。

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>備註

如果您的應用程式是 Unicode，這個方法會向使用者顯示 [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) 。 否則，架構會使用 [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) 來查詢使用者。

`QueryRestoreAutosavedDocuments`從使用者收集所有回應之後，會將資訊儲存在成員變數*m_mapDocNameToRestoreBool*中。 這個方法不會還原自動儲存的檔。

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a> CDataRecoveryHandler：： ReadOpenDocumentList

從登錄載入開啟的檔案清單。

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>傳回值

TRUE 表示 `ReadOpenDocumentList` 從登錄至少載入一個檔的資訊;FALSE 表示未載入任何檔資訊。

### <a name="remarks"></a>備註

此函式會從登錄載入開啟的檔資訊，並將其儲存在 *m_mapDocNameToAutosaveName*的成員變數中。

`ReadOpenDocumentList`載入所有資料之後，它會從登錄中刪除檔資訊。

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a> CDataRecoveryHandler：： RemoveDocumentInfo

從開啟的檔案清單中移除提供的檔。

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

*pDocument*\
在要移除之檔的指標。

### <a name="return-value"></a>傳回值

如果 *pDocument* 已從清單中移除，則為 TRUE;如果發生錯誤，則為 FALSE。

### <a name="remarks"></a>備註

當使用者關閉檔時，架構會使用這個方法，從開啟的檔案清單中移除它。

如果 `RemoveDocumentInfo` 在開啟的檔案清單中找不到 *pDocument* ，則不會執行任何動作，且會傳回 TRUE。

若要使用這個方法，必須在 *m_dwRestartManagerSupportFlags*中設定 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a> CDataRecoveryHandler：： ReopenPreviousDocuments

開啟先前開啟的檔。

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>傳回值

如果至少開啟一份檔，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會開啟先前開啟之檔的最新儲存。 如果檔未儲存或保存，則 `ReopenPreviousDocuments` 會根據該檔案類型的範本開啟空白檔。

若要使用這個方法，必須在 *m_dwRestartManagerSupportFlags*中設定 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。 如果未設定此參數，則 `ReopenPreviousDocuments` 不會執行任何動作，而且會傳回 FALSE。

如果先前開啟的檔案清單中沒有儲存的檔，則 `ReopenPreviousDocuments` 不會執行任何動作，而且會傳回 FALSE。

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a> CDataRecoveryHandler：： RestoreAutosavedDocuments

根據使用者輸入來還原自動儲存的檔。

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>傳回值

如果此方法成功還原檔，則為 TRUE。

### <a name="remarks"></a>備註

這個方法會呼叫 [CDataRecoveryHandler：： QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) ，以判斷使用者想要還原哪些檔。 如果使用者決定不還原自動儲存的檔，則會刪除自動儲存檔案 `RestoreAutosavedDocuments` 。 否則，會 `RestoreAutosavedDocuments` 以自動儲存的版本取代開啟的檔。

若要使用這個方法，您必須在中設定 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 或 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES `m_dwRestartManagerSupportFlags` 。

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a> CDataRecoveryHandler：： SaveOpenDocumentList

將目前開啟的檔案清單儲存至 Windows 登錄。

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>傳回值

如果沒有任何開啟的檔可儲存或儲存成功，則為 TRUE。 如果有檔要儲存到登錄中，則為 FALSE，但因為發生錯誤，所以不會儲存它們。

### <a name="remarks"></a>備註

`SaveOpenDocumentList`當應用程式意外結束或結束進行升級時，重新開機管理員會呼叫。 當應用程式重新開機時，它會使用 [CDataRecoveryHandler：： ReadOpenDocumentList](#readopendocumentlist) 來取得開啟的檔案清單。

這個方法只會儲存開啟的檔案清單。 [CDataRecoveryHandler：： AutosaveDocumentInfo](#autosavedocumentinfo)方法負責儲存檔本身。

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a> CDataRecoveryHandler：： SetAutosaveInterval

設定自動儲存迴圈之間的時間（以毫秒為單位）。

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>參數

*nAutosaveInterval*<br/>
在新的自動儲存間隔（以毫秒為單位）。

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a> CDataRecoveryHandler：： SetAutosavePath

設定儲存自動儲存檔案的目錄。

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>參數

*strAutosavePath*\
在儲存自動儲存檔案的路徑。

### <a name="remarks"></a>備註

變更自動儲存目錄並不會移動目前自動儲存的檔案。

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a> CDataRecoveryHandler：： SetRestartIdentifier

設定這個實例的唯一重新開機識別碼 `CDataRecoveryHandler` 。

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>參數

*strRestartIdentifier*\
在重新開機管理員的唯一識別碼。

### <a name="remarks"></a>備註

重新開機管理員會在登錄中記錄開啟檔的相關資訊。 這項資訊會與唯一的重新開機識別碼一起儲存為金鑰。 由於重新開機識別碼對於每個應用程式實例而言是唯一的，因此應用程式的多個實例可能會意外結束，而且重新開機管理員可以復原每個實例。

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a> CDataRecoveryHandler：： SetSaveDocumentInfoOnIdle

設定是否在 `CDataRecoveryHandler` 目前的閒置週期期間，將開啟的檔資訊儲存至 Windows 登錄。

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>參數

*bSaveOnIdle*\
在TRUE 表示在目前的閒置週期期間儲存檔資訊;FALSE 表示不執行儲存。

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a> CDataRecoveryHandler：： SetShutdownByRestartManager

設定重新開機管理員是否造成先前的應用程式結束。

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>參數

*bShutdownByRestartManager*\
在TRUE 表示重新開機管理員造成應用程式結束;FALSE 表示應用程式因其他原因而結束。

### <a name="remarks"></a>備註

架構的行為會根據先前的結束是否未預期，或是否由重新開機管理員所起始而有所不同。

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a> CDataRecoveryHandler：： UpdateDocumentInfo

更新檔的資訊，因為使用者已儲存檔。

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

*pDocument*\
在已儲存檔的指標。

### <a name="return-value"></a>傳回值

如果這個方法刪除自動儲存的檔並更新檔資訊，則為 TRUE。如果發生錯誤，則為 FALSE。

### <a name="remarks"></a>備註

當使用者儲存檔時，應用程式會移除自動儲存的檔案，因為不再需要它。 `UpdateDocumentInfo` 藉由呼叫 [CDataRecoveryHandler：： RemoveDocumentInfo](#removedocumentinfo)來刪除自動儲存的檔案。 `UpdateDocumentInfo` 然後，將 *pDocument* 中的資訊加入目前開啟的檔案清單中 `RemoveDocumentInfo` ，因為刪除該資訊，但儲存的檔仍在開啟。

若要使用這個方法，必須在 *m_dwRestartManagerSupportFlags*中設定 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[如何：加入重新開機管理員支援](../../mfc/how-to-add-restart-manager-support.md)
