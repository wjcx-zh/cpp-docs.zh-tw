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
ms.openlocfilehash: bdfcbea6c345235358384691388afcdbbd2d0a42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321937"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler 類別

如果`CDataRecoveryHandler`應用程式意外退出,自動儲存文檔並還原它們。

## <a name="syntax"></a>語法

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[C 資料復原處理程式::C資料復原處理程式](#cdatarecoveryhandler)|建構 `CDataRecoveryHandler` 物件。|

### <a name="methods"></a>方法

|||
|-|-|
|[CData 復原處理程式::自動儲存所有文件資訊](#autosavealldocumentinfo)|自動保存向`CDataRecoveryHandler`類註冊的每個檔。|
|[CData 修復處理程式::自動儲存文件資訊](#autosavedocumentinfo)|自動儲存指定的文檔。|
|[CData 修復處理程式::建立文件資訊](#createdocumentinfo)|將文件添加到打開的文件清單中。|
|[CData 復原處理程式::DeleteAll自動儲存檔案](#deleteallautosavedfiles)|刪除所有目前自動儲存的檔。|
|[CData 修復處理程式::Delete自動儲存檔案](#deleteautosavedfile)|刪除指定的自動儲存檔。|
|[CData 修復處理程式::產生自動儲存檔案名](#generateautosavefilename)|生成與提供的文件檔名關聯的自動儲存檔的名稱。|
|[CData 修復處理程式::抓取自動儲存間隔](#getautosaveinterval)|返回自動保存嘗試之間的間隔。|
|[CData 修復處理程式:抓取自動儲存路徑](#getautosavepath)|返回自動保存檔的路徑。|
|[CData 修復處理程式:取得文件清單名稱](#getdocumentlistname)|從`CDocument`物件檢索文檔名稱。|
|[CData 修復處理程式::取得正常文件標題](#getnormaldocumenttitle)|檢索指定文件的正常標題。|
|[CData 修復處理程式::取得復原文件標題](#getrecovereddocumenttitle)|建立並返回恢復的文件的標題。|
|[CData 復原處理程式::取得重新啟動識別碼](#getrestartidentifier)|檢索應用程式的唯一重新啟動標識符。|
|[CData 復原處理程式::取得儲存文件資訊在空閒](#getsavedocumentinfoonidle)|指示是否`CDataRecoveryHandler`對當前空閒環路執行自動保存。|
|[CData 復原處理程式::取得關閉通過重新啟動管理員](#getshutdownbyrestartmanager)|指示重新啟動管理員是否導致應用程式退出。|
|[CData 修復處理程式::初始化](#initialize)|初始化 `CDataRecoveryHandler`。|
|[CData 修復處理程式::查詢回復自動儲存的文件](#queryrestoreautosaveddocuments)|為使用者顯示自動儲存的每個文件的`CDataRecoveryHandler`對話框。 該對話框確定使用者是否要還原自動儲存的文檔。|
|[CData 修復處理程式::閱讀開啟文件清單](#readopendocumentlist)|從註冊表載入打開的文件清單。|
|[CData 修復處理程式::刪除文件資訊](#removedocumentinfo)|從打開的文件清單中刪除提供的文檔。|
|[CData 復原處理程式::重新開啟以前的文件](#reopenpreviousdocuments)|打開以前打開的文檔。|
|[CData 修復處理程式::還原自動儲存的文件](#restoreautosaveddocuments)|根據使用者輸入還原自動保存的文檔。|
|[CData 修復處理程式::儲存開啟文件清單](#saveopendocumentlist)|將目前打開的文件清單保存到 Windows 註冊表。|
|[CData 復原處理程式::設定自動儲存間隔](#setautosaveinterval)|設置自動保存週期之間的時間(以毫秒為單位)。|
|[CData 修復處理程式::設定自動儲存路徑](#setautosavepath)|設定儲存自動儲存檔的目錄。|
|[CData 復原處理程式::設定重新啟動識別碼](#setrestartidentifier)|設定 這個實體的唯一重新啟動識別碼`CDataRecoveryHandler`。|
|[CData 修復處理程式::設定儲存文件資訊](#setsavedocumentinfoonidle)|設置`CDataRecoveryHandler`是否 在當前空閒週期內將打開的文檔資訊保存到 Windows 註冊表。|
|[CData 復原處理程式::設定關閉通過重新啟動管理員](#setshutdownbyrestartmanager)|設置應用程式的上一個退出是否由重新啟動管理器引起。|
|[CData 修復處理程式::更新文件資訊](#updatedocumentinfo)|更新文檔的信息,因為使用者保存了它。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|m_bRestoringPreviousOpenDocs|指示數據恢復處理程式是否重新打開以前打開的文檔。|
|m_bSaveDocumentInfoOnIdle|指示數據恢復處理程式是否自動儲存下一個空閒迴圈上的文檔。|
|m_bShutdownByRestartManager|指示重新啟動管理員是否導致應用程式退出。|
|m_dwRestartManagerSupportFlags|指示重新啟動管理員為應用程式提供的支持的標誌。|
|m_lstAutosavesToDelete|關閉原始文件時未刪除的自動儲存檔案的清單。 當應用程式退出時,重新啟動管理器將重試刪除檔。|
|m_mapDocNameToAutosaveName|文件名稱的映射到自動儲存的檔名。|
|m_mapDocNameToDocumentPtr|文件名稱的映射到[CDocument](../../mfc/reference/cdocument-class.md)指標。|
|m_mapDocNameToRestoreBool|文件名稱的映射到布林參數,指示是否還原自動儲存的文檔。|
|m_mapDocumentPtrToDocName|指向文檔名稱`CDocument`的指標的映射。|
|m_mapDocumentPtrToDocTitle|指向文檔標題`CDocument`的指標的映射。 這些標題用於保存檔。|
|m_nAutosaveInterval|自動保存之間的時間(以毫秒為單位)。|
|m_nTimerID|自動儲存計時器的標識符。|
|m_strAutosavePath|自動儲存的文件存儲的位置。|
|m_strRestartIdentifier|重新啟動管理員的 GUID 的字串表示形式。|

## <a name="remarks"></a>備註

重新啟動管理員使用`CDataRecoveryHandler`類跟蹤所有打開的文檔,並在必要時自動儲存它們。 要啟用自動儲存,請使用[CData 修復處理程式::設定文件資訊系統](#setsavedocumentinfoonidle)方法。 此方法指示`CDataRecoveryHandler`在下一個空閒迴圈上執行自動保存。 重新啟動管理員在`SetSaveDocumentInfoOnIdle``CDataRecoveryHandler`應執行自動儲存時呼叫。

類別的擁有方法都是虛擬`CDataRecoveryHandler`的 。 重寫此類中的方法以創建自己的自定義數據恢復處理程式。 除非創建自己的數據恢復處理程式或重新啟動管理器,否則不要實例化 CDataRecoveryHandler。 [CWinApp 類](../../mfc/reference/cwinapp-class.md)根據`CDataRecoveryHandler`需要創建 物件。

在使用`CDataRecoveryHandler`物件之前,必須調用[CDataRecoveryHandler:::初始化](#initialize)。

由於`CDataRecoveryHandler`類別與重新啟動管理員緊密連線`CDataRecoveryHandler`, 因此取決於全域`m_dwRestartManagerSupportFlags`參數 。 此參數確定重新啟動管理器具有哪些許可權,以及它如何與應用程式交互。 要將重新啟動管理器合併到現有應用程式中,您必須在主應用程式的建構`m_dwRestartManagerSupportFlags`函數中分配適當的值。 有關如何使用重新啟動管理員的詳細資訊,請參閱[如何:新增重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)。

## <a name="requirements"></a>需求

**標題:** afxdata 回復.h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a>CData 復原處理程式::自動儲存所有文件資訊

自動保存向`CDataRecoveryHandler`類註冊的每個檔。

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>傳回值

如果`CDataRecoveryHandler`保存了所有文檔,則為 TRUE;如果未保存任何文檔,則 FALSE。

### <a name="remarks"></a>備註

如果沒有必須保存的文檔,此方法將返回 TRUE。 如果檢索`CWinApp``CDocManager`或 應用程式生成錯誤,它還返回 TRUE 而不保存任何文檔。

要使用此方法,必須在`m_dwRestartManagerSupportFlags`中 設置AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART或AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL。 有關詳細資訊,請參閱[如何:新增重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)。

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a>CData 修復處理程式::自動儲存文件資訊

自動儲存指定的文檔。

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[在]要保存的`CDocument`指標。|
|*bReset 修改的標籤*|[在]TRUE 表示`CDataRecoveryHandler`要 修改的考慮*pDocument;* FALSE 表示框架認為*pDocument*未修改。 有關此標誌的效果的詳細資訊,請參閱備註部分。|

### <a name="return-value"></a>傳回值

如果設置了適當的標誌,並且*pDocument*`CDocument`是有效的 物件,則為 TRUE。

### <a name="remarks"></a>備註

每個`CDocument`物件都有一個標誌,指示自上次保存以來是否已更改。 使用[CDocument::修改](../../mfc/reference/cdocument-class.md#ismodified)以確定此標誌的狀態。 如果`CDocument`自上次保存以來未更改 ,`AutosaveDocumentInfo`請刪除該文檔的任何自動儲存檔。 如果文檔自上次保存以來已更改,則關閉文檔會提示使用者在關閉之前保存該文檔。

> [!NOTE]
> 使用*bReset 修改旗標*將文件的狀態更改為未修改可能會導致使用者丟失未儲存的資料。 如果框架認為文檔未修改,則關閉它不會提示使用者保存。

如果*pDocument*`CDocument`不是有效 物件,則此方法會向[ASSERT](diagnostic-services.md#assert)宏引發異常。

要使用此方法,必須在*m_dwRestartManagerSupportFlags*中設置AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART或AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL。

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a>C 資料復原處理程式::C資料復原處理程式

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
|*dwRestartManagerSupportFlags*|[在]指示支援重新啟動管理員的哪些選項。|
|*N 自動儲存間隔*|[在]自動保存之間的時間。 此參數以毫秒為單位。|

### <a name="remarks"></a>備註

當您使用 **「新專案」** 向`CDataRecoveryHandler`導時 ,MFC 框架會自動為應用程式創建一個物件。 除非要自定義數據恢復行為或重新啟動管理員,否則不應創建`CDataRecoveryHandler`物件。

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a>CData 修復處理程式::建立文件資訊

將文件添加到打開的文件清單中。

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[在]指向的`CDocument`指標。 此方法為此`CDocument`創建文檔資訊。|

### <a name="return-value"></a>傳回值

預設實現返回 TRUE。

### <a name="remarks"></a>備註

此方法在添加文檔之前檢查*pDocument*是否已在文件清單中。 如果*pDocument*已在清單中,則此方法將刪除與*pDocument*關聯的自動儲存檔。

要使用此方法,必須在*m_dwRestartManagerSupportFlags*中設置AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART或AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL。

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a>CData 復原處理程式::DeleteAll自動儲存檔案

刪除所有目前自動儲存的檔。

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>傳回值

預設實現始終返回 TRUE。

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a>CData 修復處理程式::Delete自動儲存檔案

刪除指定的自動儲存檔。

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*strAuto 儲存檔案*|[在]包含自動儲存的檔案名的字串。|

### <a name="return-value"></a>傳回值

預設實現始終返回 TRUE。

### <a name="remarks"></a>備註

如果此方法無法刪除自動儲存的檔案,它將檔案的名稱儲存在清單中。 的析構函數`CDataRecoveryHandler`嘗試刪除該列表中指定的每個自動儲存的檔。

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a>CData 修復處理程式::產生自動儲存檔案名

生成與提供的文件檔名關聯的自動儲存檔的名稱。

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>參數

*strDocument 名稱*<br/>
[在]包含文件名稱的字串。 `GenerateAutosaveFileName`使用此文件名稱生成相應的自動儲存檔名。

### <a name="return-value"></a>傳回值

從*strDocumentName*產生的自動儲存檔名。

### <a name="remarks"></a>備註

每個文檔名稱都有一個帶有自動儲存檔名的一對一映射。

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a>CData 修復處理程式::抓取自動儲存間隔

返回自動保存嘗試之間的間隔。

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>傳回值

自動保存嘗試之間的毫秒數。

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a>CData 修復處理程式:抓取自動儲存路徑

返回自動保存檔的路徑。

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>傳回值

自動儲存的文件存儲的位置。

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a>CData 修復處理程式:取得文件清單名稱

從`CDocument`物件檢索文檔名稱。

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[在]指向的`CDocument`指標。 `GetDocumentListName`從`CDocument`中 檢索文檔名稱。|

### <a name="return-value"></a>傳回值

*pDocument*中的文件名稱。

### <a name="remarks"></a>備註

使用`CDataRecoveryHandler`文件名稱作為*m_mapDocNameToAutosaveName、m_mapDocNameToDocumentPtr*和*m_mapDocNameToDocumentPtr**m_mapDocNameToRestoreBool*中的鍵。 這些參數允許`CDataRecoveryHandler`監視`CDocument`物件、自動儲存檔名和自動儲存設置。

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a>CData 修復處理程式::取得正常文件標題

檢索指定文件的正常標題。

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[在]指向的`CDocument`指標。|

### <a name="return-value"></a>傳回值

指定文件的正常標題。

### <a name="remarks"></a>備註

文件的正常標題通常是沒有路徑的文件的檔名。 這是「**保存為」** 對話框**的檔案名**欄位中的標題。

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a>CData 修復處理程式::取得復原文件標題

建立並返回恢復的文件的標題。

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>參數

*strDocumentTitle*<br/>
[在]文件的正常標題。

### <a name="return-value"></a>傳回值

恢復的文件標題。

### <a name="remarks"></a>備註

預設情況下,文件的恢復標題是附加 **[恢復]** 的正常標題。 當使用者查詢還原自動儲存的文檔時`CDataRecoveryHandler`, 將向使用者顯示恢復的標題。

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a>CData 復原處理程式::取得重新啟動識別碼

檢索應用程式的唯一重新啟動標識符。

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>傳回值

唯一的重新啟動標識碼。

### <a name="remarks"></a>備註

重新啟動標識符對於應用程式的每次執行都是唯一的。

在`CDataRecoveryHandler`註冊表中存儲有關當前打開的文檔的資訊。 當重新啟動管理員退出應用程式並重新啟動應用程式時,它將重新啟動識別碼提供到`CDataRecoveryHandler`。 `CDataRecoveryHandler`使用重新啟動識別碼檢索以前打開的文件的清單。 這使`CDataRecoveryHandler`可以嘗試查找和還原自動儲存的檔。

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a>CData 復原處理程式::取得儲存文件資訊在空閒

指示是否`CDataRecoveryHandler`對當前空閒環路執行自動保存。

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>傳回值

TRUE`CDataRecoveryHandler`表示 當前空閒環路上的自動保存;FALSE 表示它不。

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a>CData 復原處理程式::取得關閉通過重新啟動管理員

指示重新啟動管理員是否導致應用程式退出。

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示重新啟動管理器導致應用程式退出;FALSE 表示它沒有。

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a>CData 修復處理程式::初始化

初始化 `CDataRecoveryHandler`。

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>傳回值

如果初始化成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

初始化過程載入用於從註冊表儲存自動儲存檔的路徑。 如果`Initialize`方法找不到此目錄或路徑為 NULL,`Initialize`失敗並傳`FALSE`回 。

使用[CData 回復處理程式::設定自動儲存路徑](#setautosavepath),在應用程式初始化 後`CDataRecoveryHandler`改變自動儲存路徑 。

該方法`Initialize`還會啟動計時器來監視下一次自動保存時的情況。 使用[CData 回復處理程式::設定自動儲存間隔](#setautosaveinterval),在應用程式初始化 後改變自動`CDataRecoveryHandler`儲存間隔 。

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a>CData 修復處理程式::查詢回復自動儲存的文件

為使用者顯示自動儲存的每個文件的`CDataRecoveryHandler`對話框。 該對話框確定使用者是否要還原自動儲存的文檔。

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>備註

如果應用程式為 Unicode,則此方法向用戶顯示[CTaskDialog。](../../mfc/reference/ctaskdialog-class.md) 否則,框架將使用[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)查詢使用者。

從`QueryRestoreAutosavedDocuments`使用者收集所有回應後,它將資訊儲存在成員變數*m_mapDocNameToRestoreBool*。 此方法不還原自動保存的文檔。

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a>CData 修復處理程式::閱讀開啟文件清單

從註冊表載入打開的文件清單。

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>傳回值

TRUE`ReadOpenDocumentList`表示 從註冊表中載入了至少一個文檔的資訊;FALSE 表示未載入任何文件資訊。

### <a name="remarks"></a>備註

此函數從註冊表載入開啟的文件資訊,並將其儲存在成員變數*m_mapDocNameToAutosaveName*。

載入`ReadOpenDocumentList`所有資料後,它會從註冊表中刪除文檔資訊。

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a>CData 修復處理程式::刪除文件資訊

從打開的文件清單中刪除提供的文檔。

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[在]指向要刪除的文件的指標。|

### <a name="return-value"></a>傳回值

如果*pDocument*從清單中刪除,則為 TRUE;如果發生錯誤,則 FALSE。

### <a name="remarks"></a>備註

當使用者關閉文檔時,框架使用此方法將其從打開的文檔清單中刪除。

如果在`RemoveDocumentInfo`打開的文件清單中找不到*pDocument,* 則它不執行任何操作並返回 TRUE。

要使用此方法,必須在*m_dwRestartManagerSupportFlags*中設置AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a>CData 復原處理程式::重新開啟以前的文件

打開以前打開的文檔。

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>傳回值

如果至少打開一個文檔,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

此方法將打開以前打開的文檔的最新儲存。 如果未儲存或自動儲存文件,`ReopenPreviousDocuments`則基於該檔案類型的範本打開空白文檔。

要使用此方法,必須在*m_dwRestartManagerSupportFlags*中設置AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。 如果未設定此參數,`ReopenPreviousDocuments`則不執行任何操作並返回 FALSE。

如果以前打開的文檔清單中沒有儲存任何文`ReopenPreviousDocuments`檔, 則不執行任何操作並返回 FALSE。

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a>CData 修復處理程式::還原自動儲存的文件

根據使用者輸入還原自動保存的文檔。

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>傳回值

如果此方法成功還原文檔,則為 TRUE。

### <a name="remarks"></a>備註

此方法調用[CDataRecoveryHandler::查詢還原自動儲存的文檔](#queryrestoreautosaveddocuments),以確定使用者要還原的文檔。 如果使用者決定不還原自動儲存的文檔`RestoreAutosavedDocuments`, 請刪除自動儲存檔。 否則,`RestoreAutosavedDocuments`將打開的文檔替換為自動儲存的版本。

要使用此方法,必須在中`m_dwRestartManagerSupportFlags`設置AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES或AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES。

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a>CData 修復處理程式::儲存開啟文件清單

將目前打開的文件清單保存到 Windows 註冊表。

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>傳回值

如果沒有要保存的打開的文檔,或者它們已成功保存,則為 TRUE。 如果有要保存到註冊表的文檔,但由於發生錯誤而未保存文檔,則 FALSE。

### <a name="remarks"></a>備註

重新啟動管理員在應用程式`SaveOpenDocumentList`意外退出或退出升級時調用。 當應用程式重新啟動時,它使用[CDataRecoveryHandler::讀取 OpenDocumentList](#readopendocumentlist)檢索打開的文檔清單。

此方法僅保存打開的文檔清單。 方法[CDataRecoveryHandler::自動保存文檔資訊](#autosavedocumentinfo)負責保存文檔本身。

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a>CData 復原處理程式::設定自動儲存間隔

設置自動保存週期之間的時間(以毫秒為單位)。

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>參數

*N 自動儲存間隔*<br/>
[在]新的自動保存間隔(以毫秒為單位)。

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a>CData 修復處理程式::設定自動儲存路徑

設定儲存自動儲存檔的目錄。

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*strAutosavePath*|[在]儲存自動保存檔的路徑。|

### <a name="remarks"></a>備註

變更自動儲存目錄不會移動目前自動儲存的檔案。

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a>CData 復原處理程式::設定重新啟動識別碼

設定 這個實體的唯一重新啟動識別碼`CDataRecoveryHandler`。

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*strRestart識別碼*|[在]重新啟動管理員的唯一識別碼。|

### <a name="remarks"></a>備註

重新啟動管理員記錄有關註冊表中打開的文檔的資訊。 此資訊以唯一的重新啟動標識符作為密鑰存儲。 由於重新啟動標識碼對於應用程式的每個實體都是唯一的,因此應用程式的多個實例可能會意外退出,重新啟動管理器可以恢復每個實例。

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a>CData 修復處理程式::設定儲存文件資訊

設置`CDataRecoveryHandler`是否 在當前空閒週期內將打開的文檔資訊保存到 Windows 註冊表。

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*bSaveonidle*|[在]TRUE 以保存當前空閒週期中的文件資訊;FALSE 不執行保存。|

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a>CData 復原處理程式::設定關閉通過重新啟動管理員

設置應用程式的上一個退出是否由重新啟動管理器引起。

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*b 關閉重新啟動管理員*|[在]TRUE 指示重新啟動管理器導致應用程式退出;FALSE 以指示應用程式出於其他原因退出。|

### <a name="remarks"></a>備註

框架的行為方式因上一個退出是否意外或是否由重新啟動管理器啟動而不同。

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a>CData 修復處理程式::更新文件資訊

更新文檔的信息,因為使用者保存了它。

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pDocument*|[在]指向已保存文檔的指標。|

### <a name="return-value"></a>傳回值

如果此方法刪除了自動保存的文檔並更新了文檔資訊,則為 TRUE;如果發生錯誤,則 FALSE。

### <a name="remarks"></a>備註

當使用者保存文檔時,應用程式將刪除自動儲存的文件,因為它不再需要它。 `UpdateDocumentInfo`使用[CDataRecoveryHandler 移除自動儲存的檔案::刪除文件資訊](#removedocumentinfo)。 `UpdateDocumentInfo`然後將*pDocument*中的資訊添加到當前打開的文檔清單`RemoveDocumentInfo`中,因為刪除該資訊,但保存的文檔仍處於打開狀態。

要使用此方法,必須在*m_dwRestartManagerSupportFlags*中設置AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[如何：新增重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)
