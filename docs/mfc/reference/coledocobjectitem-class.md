---
title: COleDocObjectItem 類別
ms.date: 11/04/2016
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
ms.openlocfilehash: 454be491fe5875b1b1ac9b2b85fdebe2f1663ebc
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916970"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem 類別

實作主動式文件內含項目。

## <a name="syntax"></a>語法

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|`COleDocObject`結構專案。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|使用預設印表機設定來列印容器應用程式的檔。|
|[COleDocObjectItem::ExecCommand](#execcommand)|執行使用者指定的命令。|
|[COleDocObjectItem::GetActiveView](#getactiveview)|抓取檔的現用視圖。|
|[COleDocObjectItem::GetPageCount](#getpagecount)|抓取容器應用程式檔中的頁面數目。|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|準備容器應用程式的檔以進行列印。|
|[COleDocObjectItem::OnPrint](#onprint)|列印容器應用程式的檔。|
|[COleDocObjectItem::QueryCommand](#querycommand)|查詢使用者介面事件所產生之一或多個命令的狀態。|
|[COleDocObjectItem::Release](#release)|釋放與 OLE 連結專案的連接, 並在開啟時將它關閉。 不會損毀用戶端專案。|

## <a name="remarks"></a>備註

在 MFC 中, 使用中的檔案的處理方式類似于一般就地可編輯的內嵌, 但有下列差異:

- 衍生的類別仍會維護目前內嵌專案的清單; 不過, 這些專案可能是`COleDocObjectItem`衍生的專案。 `COleDocument`

- 當使用中的檔處於作用中狀態時, 它會在其就地作用中時, 佔用整個視圖的工作區。

- 活動文檔容器具有 [說明] 功能表的 [完全控制]。

- [說明] 功能表包含**作用**中檔容器和伺服器的功能表項目。

因為活動文檔容器擁有 [說明 ] 功能表, 所以容器會負責將伺服器 [說明] 功能表訊息轉送到伺服器。 這項整合是由`COleDocObjectItem`處理。

如需功能表合併和作用中檔啟用的詳細資訊, 請參閱[活動文檔](../../mfc/active-document-containment.md)內含專案的總覽。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>需求

**標頭:** afxole。h

##  <a name="coledocobjectitem"></a>COleDocObjectItem:: COleDocObjectItem

呼叫這個成員函式來初始化`COleDocObjectItem`物件。

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>參數

*pContainerDoc*<br/>
做為使用中`COleDocument`文檔容器之物件的指標。 這個參數必須是 Null, 才能啟用 IMPLEMENT_SERIALIZE。 通常會使用非 Null 的檔指標來構造 OLE 專案。

##  <a name="dodefaultprinting"></a>COleDocObjectItem::D oDefaultPrinting

由架構呼叫至使用預設設定的檔。

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pCaller*<br/>
傳送列印命令之[CView](../../mfc/reference/cview-class.md)物件的指標。

*pInfo*<br/>
描述要列印之作業的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件指標。

##  <a name="execcommand"></a>COleDocObjectItem:: ExecCommand

呼叫這個成員函式以執行使用者所指定的命令。

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>參數

*nCmdID*<br/>
要執行之命令的識別碼。 必須位於*pguidCmdGroup*所識別的群組中。

*nCmdExecOpt*<br/>
指定命令執行選項。 預設會將設定為執行命令, 而不提示使用者。 如需值清單, 請參閱[OLECMDEXECOPT](/windows/desktop/api/docobj/ne-docobj-olecmdexecopt) 。

*pguidCmdGroup*<br/>
命令群組的唯一識別碼。 根據預設, Null 會指定標準群組。 傳入*nCmdID*的命令必須屬於群組。

### <a name="return-value"></a>傳回值

如果成功, 則傳回 S_OK;否則, 會傳回下列其中一個錯誤碼。

|值|說明|
|-----------|-----------------|
|E_UNEXPECTED|發生未預期的錯誤。|
|E_FAIL|發生錯誤。|
|E_NOTIMPL|指出 MFC 本身應該嘗試轉譯和分派命令。|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*為非 Null, 但未指定可辨識的命令群組。|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*在群組 pGroup 中無法辨識為有效的命令。|
|OLECMDERR_DISABLED|*NCmdID*所識別的命令已停用, 無法執行。|
|OLECMDERR_NOHELP|呼叫者要求提供*nCmdID*所識別之命令的說明, 但沒有可用的說明。|
|OLECMDERR_CANCELLED|使用者已取消執行。|

### <a name="remarks"></a>備註

*PguidCmdGroup*和*nCmdID*參數會一起唯一識別要叫用的命令。 *NCmdExecOpt*參數會指定要採取的確切動作。

##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView

呼叫這個成員函式, 以取得目前使用`IOleDocumentView`中視圖之介面的指標。

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>傳回值

目前現用視圖之[IOleDocumentView](/windows/desktop/api/docobj/nn-docobj-ioledocumentview)介面的指標。 如果沒有目前的視圖, 它會傳回 Null。

### <a name="remarks"></a>備註

傳回`IOleDocumentView`的指標上的參考計數在此函式傳回之前不會遞增。

##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount

呼叫這個成員函式可抓取檔中的頁數。

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>參數

*pnFirstPage*<br/>
檔第一頁編號的指標。 可以是 Null, 表示呼叫端不需要此數位。

*pcPages*<br/>
檔中總頁數的指標。 可以是 Null, 表示呼叫端不需要此數位。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="onprepareprinting"></a>COleDocObjectItem:: OnPreparePrinting

此成員函式是由架構呼叫, 以準備要列印的檔。

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>參數

*pCaller*<br/>
傳送列印命令之[CView](../../mfc/reference/cview-class.md)物件的指標。

*pInfo*<br/>
描述要列印之作業的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件指標。

*bPrintAll*<br/>
指定是否要列印整份檔。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="onprint"></a>COleDocObjectItem:: OnPrint

架構會呼叫這個成員函式來列印檔案。

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>參數

*pCaller*<br/>
傳送列印命令之 CView 物件的指標。

*pInfo*<br/>
描述要列印之作業的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件指標。

*bPrintAll*<br/>
指定是否要列印整份檔。

##  <a name="querycommand"></a>COleDocObjectItem:: QueryCommand

查詢使用者介面事件所產生之一或多個命令的狀態。

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>參數

*nCmdID*<br/>
正在查詢之命令的識別碼。

*pdwStatus*<br/>
查詢結果所傳回之旗標的指標。 如需可能值的清單, 請參閱[OLECMDF](/windows/desktop/api/docobj/ne-docobj-olecmdf)。

*pCmdText*<br/>
[OLECMDTEXT](/windows/desktop/api/docobj/ns-docobj-olecmdtext)結構的指標, 會在其中傳回單一命令的名稱和狀態資訊。 可以是 Null, 表示呼叫端不需要此資訊。

*pguidCmdGroup*<br/>
命令群組的唯一識別碼;可以是 Null 以指定標準群組。

### <a name="return-value"></a>傳回值

如需傳回值的完整清單, 請參閱 Windows SDK 中的[IOleCommandTarget:: QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) 。

### <a name="remarks"></a>備註

此成員函式會模擬[IOleCommandTarget:: QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus)方法的功能, 如 Windows SDK 中所述。

##  <a name="release"></a>  COleDocObjectItem::Release

釋放與 OLE 連結專案的連接, 並在開啟時將它關閉。 不會損毀用戶端專案。

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>參數

*dwCloseOption*<br/>
旗標, 指定在何種情況下, 當 OLE 專案回到載入狀態時, 就會儲存該檔案。 如需可能值的清單, 請參閱[COleClientItem:: Close](../../mfc/reference/coleclientitem-class.md#close)。

### <a name="remarks"></a>備註

不會損毀用戶端專案。

## <a name="see-also"></a>另請參閱

[MFC 範例 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem 類別](../../mfc/reference/cdocobjectserveritem-class.md)
