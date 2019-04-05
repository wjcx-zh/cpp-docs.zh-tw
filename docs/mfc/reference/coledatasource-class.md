---
title: COleDataSource 類別
ms.date: 11/04/2016
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
ms.openlocfilehash: 37de6fd74f1e9210dcd9b9a356719436814c0c7f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776826"
---
# <a name="coledatasource-class"></a>COleDataSource 類別

做為快取，應用程式在此放置資料，以便在資料傳輸作業 (例如剪貼簿或拖放作業) 期間提供。

## <a name="syntax"></a>語法

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDataSource::COleDataSource](#coledatasource)|建構 `COleDataSource` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDataSource::CacheData](#cachedata)|提供資料中指定的格式，使用`STGMEDIUM`結構。|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|使用指定的格式使用 HGLOBAL 的供應項目資料。|
|[COleDataSource::DelayRenderData](#delayrenderdata)|提供使用延遲的呈現格式指定的資料。|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|提供在指定之格式的資料`CFile`指標。|
|[COleDataSource::DelaySetData](#delaysetdata)|針對每一種支援的格式呼叫`OnSetData`。|
|[COleDataSource::DoDragDrop](#dodragdrop)|執行與資料來源的拖放作業。|
|[COleDataSource::Empty](#empty)|清空`COleDataSource`資料的物件。|
|[COleDataSource::FlushClipboard](#flushclipboard)|將所有的資料呈現到剪貼簿。|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|確認置於 剪貼簿的資料還在那裡。|
|[COleDataSource::OnRenderData](#onrenderdata)|擷取資料做為延遲轉譯的一部分。|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|擷取資料到`CFile`延遲轉譯的一部分。|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|擷取資料到 HGLOBAL 延遲轉譯的一部分。|
|[COleDataSource::OnSetData](#onsetdata)|呼叫以取代中的資料`COleDataSource`物件。|
|[COleDataSource::SetClipboard](#setclipboard)|上的芳鄰`COleDataSource`剪貼簿上的物件。|

## <a name="remarks"></a>備註

您可以直接建立 OLE 資料來源。 或者， [COleClientItem](../../mfc/reference/coleclientitem-class.md)並[COleServerItem](../../mfc/reference/coleserveritem-class.md)類別建立 OLE 資料來源，以回應其`CopyToClipboard`和`DoDragDrop`成員函式。 請參閱[COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard)的簡短描述。 覆寫`OnGetClipboardData`針對建立其他的剪貼簿格式加入 OLE 資料來源中您用戶端項目或伺服器項目類別成員函式`CopyToClipboard`或`DoDragDrop`成員函式。

每當您想要準備傳輸的資料，您應該建立這個類別的物件，並填入資料，可使用最適當的方法，為您的資料。 它會插入至資料來源的方式直接受到是否會提供的資料立即 （立即轉譯） 或隨選 （延遲轉譯）。 每個剪貼簿格式，您會在此提供藉由傳遞要使用的剪貼簿格式的資料 (和選擇性[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構)，呼叫[DelayRenderData](#delayrenderdata)。

如需有關資料來源和資料傳輸的詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。 此外，發行項[剪貼簿主題](../../mfc/clipboard.md)描述 OLE 剪貼簿機制。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="cachedata"></a>  COleDataSource::CacheData

呼叫此函式來指定的格式，在其中的資料期間提供的資料傳輸作業。

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要提供資料的剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)結構，其中包含指定之格式的資料。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構描述以提供資料格式。 如果您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果它是 NULL 時，會使用中的其他欄位的預設值`FORMATETC`結構。

### <a name="remarks"></a>備註

您必須先提供資料，因為此函式所提供的是它使用直接轉譯。 資料會快取，直到需要為止。

提供使用資料[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)結構。 您也可以使用`CacheGlobalData`成員函式，如果您提供的資料量是夠小，無法有效率地使用 HGLOBAL 傳送。

在呼叫之後`CacheData``ptd`隸屬`lpFormatEtc`的內容*lpStgMedium*資料物件，不是由呼叫者所擁有。

若要使用延遲的轉譯，呼叫[DelayRenderData](#delayrenderdata)或是[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為已處理的 MFC，請參閱文章[資料物件和資料來源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊，請參閱 < [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)並[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的結構。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData

呼叫此函式來指定的格式，在其中的資料期間提供的資料傳輸作業。

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要提供資料的剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*hGlobal*<br/>
包含指定的格式資料的全域記憶體區塊的控制代碼。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構描述以提供資料格式。 如果您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果它是 NULL 時，會使用中的其他欄位的預設值`FORMATETC`結構。

### <a name="remarks"></a>備註

此函式會提供使用立即呈現，因此呼叫函式; 時，您必須提供資料的資料資料會快取，直到需要為止。 使用`CacheData`成員函式，如果您提供的大量資料，或如果您需要的結構化儲存體。

若要使用延遲的轉譯，呼叫[DelayRenderData](#delayrenderdata)或是[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為已處理的 MFC，請參閱文章[資料物件和資料來源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊，請參閱 < [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的結構。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="coledatasource"></a>  COleDataSource::COleDataSource

建構 `COleDataSource` 物件。

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData

呼叫此函式來指定的格式，在其中的資料期間提供的資料傳輸作業。

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要提供資料的剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構描述以提供資料格式。 如果您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果它是 NULL 時，會使用中的其他欄位的預設值`FORMATETC`結構。

### <a name="remarks"></a>備註

此函式會提供使用延遲的轉譯，因此不會立即提供的資料的資料。 [OnRenderData](#onrenderdata)或是[OnRenderGlobalData](#onrenderglobaldata)成員函式呼叫來要求資料。

如果您不打算提供您的資料，透過使用此函式`CFile`物件。 如果您要提供的資料，透過`CFile`物件，請呼叫[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為已處理的 MFC，請參閱文章[資料物件和資料來源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

若要使用立即呈現，呼叫[CacheData](#cachedata)或是[CacheGlobalData](#cacheglobaldata)成員函式。

如需詳細資訊，請參閱 < [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的結構。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData

呼叫此函式來指定的格式，在其中的資料期間提供的資料傳輸作業。

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要提供資料的剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構描述以提供資料格式。 如果您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果它是 NULL 時，會使用中的其他欄位的預設值`FORMATETC`結構。

### <a name="remarks"></a>備註

此函式會提供使用延遲的轉譯，因此不會立即提供的資料的資料。 [OnRenderFileData](#onrenderfiledata)成員函式呼叫來要求資料。

使用此函式，如果您要使用`CFile`來提供資料的物件。 如果您不打算使用`CFile`物件，請呼叫[DelayRenderData](#delayrenderdata)成員函式。 如需有關延遲轉譯為已處理的 MFC，請參閱文章[資料物件和資料來源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

若要使用立即呈現，呼叫[CacheData](#cachedata)或是[CacheGlobalData](#cacheglobaldata)成員函式。

如需詳細資訊，請參閱 < [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的結構。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData

呼叫此函式來支援變更資料來源的內容。

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要放置資料的剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構描述資料是要被取代的格式。 如果您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果它是 NULL 時，會使用中的其他欄位的預設值`FORMATETC`結構。

### <a name="remarks"></a>備註

[OnSetData](#onsetdata)會在發生此情況時由架構呼叫。 架構傳回的資料來源時，只會使用這[COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)。 如果`DelaySetData`未呼叫您`OnSetData`絕不會呼叫函式。 `DelaySetData` 應該針對每個剪貼簿呼叫或`FORMATETC`您支援的格式。

如需詳細資訊，請參閱 < [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的結構。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="dodragdrop"></a>  COleDataSource::DoDragDrop

呼叫`DoDragDrop`成員函式來執行拖放作業的此資料來源，通常[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)處理常式。

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>參數

*dwEffects*<br/>
拖放作業允許此資料來源。 可以是下列其中一個或多個項目：

- DROPEFFECT_COPY 無法執行複製作業。

- 無法執行 DROPEFFECT_MOVE 的移動作業。

- 卸除的資料從原始資料的 DROPEFFECT_LINK 的連結，所以無法建立。

- DROPEFFECT_SCROLL 表示可能發生拖曳捲軸作業。

*lpRectStartDrag*<br/>
定義實際開始拖曳的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。

*pDropSource*<br/>
要卸除來源點。 如果 NULL 則預設實作[COleDropSource](../../mfc/reference/coledropsource-class.md)將使用。

### <a name="return-value"></a>傳回值

卸除拖放作業中，所產生的效果否則 DROPEFFECT_NONE 如果永遠不會在作業開始，因為使用者放開滑鼠按鈕才會離開提供的矩形。

### <a name="remarks"></a>備註

拖放作業不會立即啟動。 它會等到滑鼠游標離開所指定的矩形*lpRectStartDrag*或直到經過指定的毫秒數。 如果*lpRectStartDrag*是 NULL 時，矩形的大小為一個像素。

登錄機碼設定所指定的延遲時間。 您可以變更的延遲時間，藉由呼叫[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或是[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果您未指定延遲時間，則會使用預設值是 200 毫秒。 拖曳延遲時間會儲存，如下所示：

- Windows NT 拖曳延遲時間會儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。

- Windows 3.x 拖曳延遲時間會儲存在獲得。INI 檔案，底下的 [Windows} 一節。

- Windows 95/98 拖曳延遲時間會儲存在成交的快取版本。INI。

如需有關如何將拖曳的延遲資訊會儲存在登錄或。INI 檔案，請參閱[WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) Windows SDK 中。

如需詳細資訊，請參閱文章[將拖放：實作置放來源](../../mfc/drag-and-drop-implementing-a-drop-source.md)。

##  <a name="empty"></a>  COleDataSource::Empty

呼叫此函式以空白`COleDataSource`資料的物件。

```
void Empty();
```

### <a name="remarks"></a>備註

同時快取，延遲轉譯格式會清空，以便之後可以重複使用。

如需詳細資訊，請參閱 < [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) Windows SDK 中。

##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard

將剪貼簿，並接著可讓您貼上剪貼簿的資料之後您的應用程式關閉, 的資料呈現。

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>備註

使用[SetClipboard](#setclipboard)將資料放在剪貼簿上。

##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner

判斷 剪貼簿上的資料是否已變更之後[SetClipboard](#setclipboard)一次呼叫，若是如此，識別目前的擁有者。

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>傳回值

資料來源目前在剪貼簿，或為 NULL 如果剪貼簿上沒有任何，或如果 [剪貼簿] 不屬於所呼叫的應用程式。

##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData

由架構呼叫以擷取指定格式的資料。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，指定用來要求資訊的格式。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)資料所要傳回的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)或是[DelayRenderFileData](#delayrenderfiledata)延遲轉譯的成員函式。 此函式的預設實作會呼叫[OnRenderFileData](#onrenderfiledata)或是[OnRenderGlobalData](#onrenderglobaldata)如果提供的儲存體中的檔案或記憶體，分別為。 如果任一種格式提供，然後的預設實作會傳回 0 並不執行任何動作。 如需有關延遲轉譯為已處理的 MFC，請參閱文章[資料物件和資料來源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如果*lpStgMedium*-> *tymed*是 TYMED_NULL，`STGMEDIUM`應該配置及所指定的填滿*lpFormatEtc]-> [tymed*。 如果不是 TYMED_NULL，`STGMEDIUM`應填入的資料的位置。

這是一種進階可覆寫。 覆寫此函式可提供您要求的格式和媒體中的資料。 根據您的資料，您可能想要改為覆寫這個函式的其他版本的其中一個。 如果您的資料是小型且固定的大小，會覆寫`OnRenderGlobalData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。

如需詳細資訊，請參閱 < [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)並[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構[TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed)列舉型別和[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)在 Windows SDK 中。

##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData

由架構呼叫以擷取指定之格式的資料，當指定的存放媒體檔案。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，指定用來要求資訊的格式。

*pFile*<br/>
指向[CFile](../../mfc/reference/cfile-class.md)所在的資料是要轉譯的物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回 FALSE。

這是一種進階可覆寫。 覆寫此函式可提供您要求的格式和媒體中的資料。 根據您的資料，您可能想要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存體媒體時，會覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。 如需有關延遲轉譯為已處理的 MFC，請參閱文章[資料物件和資料來源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊，請參閱 < [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構並[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) Windows SDK 中。

##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData

由架構呼叫以指定的存放媒體是全域記憶體時，擷取指定之格式的資料。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，指定用來要求資訊的格式。

*phGlobal*<br/>
指向要傳回之資料的全域記憶體控制代碼。 如果其中有尚未配置，這個參數可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回 FALSE。

如果*phGlobal*是 NULL，則應該配置並傳回新 HGLOBAL *phGlobal*。 HGLOBAL 所指定的否則為*phGlobal*應該填入資料。 資料放在 HGLOBAL 數量不得超過目前的記憶體區塊大小。 此外，無法重新配置較大的區塊。

這是一種進階可覆寫。 覆寫此函式可提供您要求的格式和媒體中的資料。 根據您的資料，您可能想要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存體媒體時，會覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。 如需有關延遲轉譯為已處理的 MFC，請參閱文章[資料物件和資料來源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊，請參閱 < [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構並[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) Windows SDK 中。

##  <a name="onsetdata"></a>  COleDataSource::OnSetData

由架構呼叫以設定或取代中的資料`COleDataSource`中指定的格式物件。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，指定取代資料的格式。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)結構，其中包含的資料，將會取代目前的內容`COleDataSource`物件。

*bRelease*<br/>
表示誰完成函式呼叫之後儲存媒體的擁有權。 呼叫端將決定誰負責釋放配置的存放媒體代表的資源。 呼叫端會藉由設定*bRelease*。 如果*bRelease*為非零值，資料來源取得擁有權，使用它完成時釋放媒體。 當*bRelease*為 0，呼叫端保留擁有權，且資料來源可以使用儲存媒體，只能針對呼叫的持續時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

資料來源不會計資料的擁有權，直到它成功取得它。 也就是說，它不會擁有權如果`OnSetData`會傳回 0。 如果資料來源會取得擁有權，它會藉由呼叫釋放儲存媒體[ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium)函式。

預設實作不做任何動作。 覆寫這個函式來取代指定之格式的資料。 這是一種進階可覆寫。

如需詳細資訊，請參閱[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)並[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構並[ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium)並[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的函式。

##  <a name="setclipboard"></a>  COleDataSource::SetClipboard

將所包含的資料`COleDataSource`之後呼叫下列函式的其中一個剪貼簿上的物件：[CacheData](#cachedata)， [CacheGlobalData](#cacheglobaldata)， [DelayRenderData](#delayrenderdata)，或[DelayRenderFileData](#delayrenderfiledata)。

```
void SetClipboard();
```

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject 類別](../../mfc/reference/coledataobject-class.md)
