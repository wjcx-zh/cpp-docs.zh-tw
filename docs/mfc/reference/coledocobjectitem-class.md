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
ms.openlocfilehash: a696226185dd99b9e277e74d92cbe15c95cc900a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375044"
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
|[COleDoc 物件項目:COleDoc 物件專案](#coledocobjectitem)|建構項`COleDocObject`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDocObject 專案::D預設列印](#dodefaultprinting)|使用預設印表機設置列印容器應用程式的文檔。|
|[COleDocObject 專案::執行命令](#execcommand)|執行使用者指定的命令。|
|[COleDoc 物件項目:取得活動檢視](#getactiveview)|檢索文件的活動視圖。|
|[COleDoc 物件項目:取得頁面計數](#getpagecount)|檢索容器應用程式文件中的頁數。|
|[COleDocObject 專案::準備列印](#onprepareprinting)|準備容器應用程式的文檔以進行列印。|
|[COleDocObject 專案::在列印上](#onprint)|列印容器應用程式的文檔。|
|[COleDoc 物件項目:查詢命令](#querycommand)|查詢使用者介面事件所產生之一或多個命令的狀態。|
|[COleDocObject專案::發佈](#release)|釋放與 OLE 連結項的連接,並在打開時關閉它。 不銷毀用戶端項。|

## <a name="remarks"></a>備註

在 MFC 中,Active 文件的處理方式類似於常規的、就地可編輯的嵌入,並具有以下差異:

- 派生`COleDocument`類仍維護當前嵌入項的清單;但是,派生類仍保留當前嵌入的項的清單。但是,這些專案可能是`COleDocObjectItem`派生項。

- 當活動文檔處於活動狀態時,當它就地處於活動狀態時,它將佔據視圖的整個工作區。

- 活動文件容器可完全控制 **「幫助」** 選單。

- **「使用**選單包含活動文件容器和伺服器的功能表項。

由於 Active 文件容器擁有 **「説明**」功能表,因此該容器負責將伺服器**幫助**功能表訊息轉發到伺服器。 此整合的由`COleDocObjectItem`處理 。

有關功能表合併和活動文件啟動的詳細資訊,請參閱[活動文檔包含](../../mfc/active-document-containment.md)概述。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a>COleDoc 物件項目:COleDoc 物件專案

調用此成員函數以初始化`COleDocObjectItem`物件。

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>參數

*p 集裝箱檔案*<br/>
指向充當活動檔`COleDocument`容器的物件的指標。 此參數必須為 NULL 才能啟用IMPLEMENT_SERIALIZE。 通常,OLE 項使用非 NULL 文件指標建構。

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a>COleDocObject 專案::D預設列印

框架使用預設設置調用文檔。

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pCaller*<br/>
指向發送列印命令的[CView](../../mfc/reference/cview-class.md)物件的指標。

*pInfo*<br/>
指向描述要列印的作業的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件的指標。

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a>COleDocObject 專案::執行命令

呼叫此成員函數以執行使用者指定的命令。

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>參數

*nCmdID*<br/>
要執行的命令的標識碼。 必須位於*pguidCmdGroup*標識的組中。

*nCmdExecOpt*<br/>
指定命令執行選項。 默認情況下,設置為在不提示用戶的情況下執行命令。 有關值清單,請參閱[OLECMDEXECOPT。](/windows/win32/api/docobj/ne-docobj-olecmdexecopt)

*普吉德集團*<br/>
命令組的唯一標識碼。 預設情況下,NULL,它指定標準組。 *在 nCmdID*中傳遞的命令必須屬於該組。

### <a name="return-value"></a>傳回值

如果成功,返回S_OK;否則,返回以下錯誤代碼之一。

|值|描述|
|-----------|-----------------|
|E_UNEXPECTED|發生未預期的錯誤。|
|E_FAIL|發生錯誤。|
|E_NOTIMPL|指示 MFC 本身應嘗試轉換和調度命令。|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*是非 NULL,但不指定已識別的命令組。|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*未在組 pGroup 中識別為有效命令。|
|OLECMDERR_DISABLED|*nCmdID*識別的命令已禁用,無法執行。|
|OLECMDERR_NOHELP|呼叫者請求對*nCmdID*標識的命令尋求説明,但沒有可用的説明。|
|OLECMDERR_CANCELLED|使用者取消了執行。|

### <a name="remarks"></a>備註

*pguidCmdGroup*和*nCmdID*參數一起唯一標識要呼叫的命令。 *nCmdExecOpt 參數*指定要執行的確切操作。

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a>COleDoc 物件項目:取得活動檢視

呼叫此成員函數以獲取指向當前活動檢視`IOleDocumentView`介面的指標。

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>傳回值

指向當前活動檢視的[IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview)介面的指標。 如果沒有當前檢視,它將返回 NULL。

### <a name="remarks"></a>備註

返回的`IOleDocumentView`指標上的引用計數不會遞增,然後再由此函數返回它。

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a>COleDoc 物件項目:取得頁面計數

呼叫此成員函數以檢索文件中的頁數。

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>參數

*pnFirstPage*<br/>
指向文檔第一頁編號的指標。 可以是 NULL,表示呼叫方不需要此號碼。

*pcPages*<br/>
指向文檔中頁總數的指標。 可以是 NULL,表示呼叫方不需要此號碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a>COleDocObject 專案::準備列印

框架調用此成員函數以準備用於列印的文檔。

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>參數

*pCaller*<br/>
指向發送列印命令的[CView](../../mfc/reference/cview-class.md)物件的指標。

*pInfo*<br/>
指向描述要列印的作業的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件的指標。

*bPrintAll*<br/>
指定是否列印整個文檔。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a>COleDocObject 專案::在列印上

框架調用此成員函數以列印文檔。

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>參數

*pCaller*<br/>
指向發送列印命令的 CView 物件的指標。

*pInfo*<br/>
指向描述要列印的作業的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件的指標。

*bPrintAll*<br/>
指定是否列印整個文檔。

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a>COleDoc 物件項目:查詢命令

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
要查詢的命令的標識碼。

*pdw狀態*<br/>
作為查詢的結果返回指向標誌的指標。 有關可能值的清單,請參閱[OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf)。

*pCmdText*<br/>
指向[OLECMDTEXT](/windows/win32/api/docobj/ns-docobj-olecmdtext)結構的指標,在該結構中返回單個命令的名稱和狀態資訊。 可以為 NULL 以指示呼叫方不需要此資訊。

*普吉德集團*<br/>
命令組的唯一標識碼;可以為 NULL 指定標準群組。

### <a name="return-value"></a>傳回值

有關返回值的完整清單,請參閱[IOleCommandTarget::Windows](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) SDK 中的查詢狀態。

### <a name="remarks"></a>備註

此成員函數類比[IOleCommandTarget::查詢狀態](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus)方法的功能,如 Windows SDK 中所述。

## <a name="coledocobjectitemrelease"></a><a name="release"></a>COleDocObject專案::發佈

釋放與 OLE 連結項的連接,並在打開時關閉它。 不銷毀用戶端項。

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>參數

*dwCloseOption*<br/>
標記指定在哪些情況下,當 OLE 項返回到載入狀態時,它保存它。 有關可能值的清單,請參閱[COleClientItemItem:: 關閉](../../mfc/reference/coleclientitem-class.md#close)。

### <a name="remarks"></a>備註

不銷毀用戶端項。

## <a name="see-also"></a>另請參閱

[MFC 樣品 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem 類別](../../mfc/reference/cdocobjectserveritem-class.md)
