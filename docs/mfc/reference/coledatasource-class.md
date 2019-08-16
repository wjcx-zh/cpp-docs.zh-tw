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
ms.openlocfilehash: 5e6b49edfedc8e7311e9ecc21ca065ad99c15c62
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504135"
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
|[COleDataSource::CacheData](#cachedata)|使用`STGMEDIUM`結構, 以指定的格式提供資料。|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|使用 HGLOBAL, 以指定的格式提供資料。|
|[COleDataSource::DelayRenderData](#delayrenderdata)|使用延遲轉譯, 以指定的格式提供資料。|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|在`CFile`指標中以指定的格式提供資料。|
|[COleDataSource::DelaySetData](#delaysetdata)|針對中`OnSetData`支援的每種格式呼叫。|
|[COleDataSource::DoDragDrop](#dodragdrop)|使用資料來源執行拖放作業。|
|[COleDataSource::Empty](#empty)|清空資料`COleDataSource`的物件。|
|[COleDataSource::FlushClipboard](#flushclipboard)|將所有資料轉譯至剪貼簿。|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|確認放在剪貼簿上的資料仍然存在。|
|[COleDataSource::OnRenderData](#onrenderdata)|將資料當做延遲轉譯的一部分來抓取。|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|將`CFile`資料當做延遲轉譯的一部分, 抓取到。|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|將資料當做延遲轉譯的一部分, 捕獲到 HGLOBAL 中。|
|[COleDataSource::OnSetData](#onsetdata)|呼叫以取代`COleDataSource`物件中的資料。|
|[COleDataSource::SetClipboard](#setclipboard)|`COleDataSource`將物件放在剪貼簿上。|

## <a name="remarks"></a>備註

您可以直接建立 OLE 資料來源。 或者, [COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)類別會建立 OLE 資料來源, 以回應其`CopyToClipboard`和`DoDragDrop`成員函式。 如需簡短描述, 請參閱[COleServerItem:: CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) 。 覆寫`OnGetClipboardData`用戶端專案或伺服器專案類別的成員函式, 將其他剪貼簿格式加入為`CopyToClipboard`或`DoDragDrop`成員函式所建立之 OLE 資料來源中的資料。

每當您想要準備傳輸的資料時, 您應該建立此類別的物件, 並使用您的資料最適當的方法來填入資料。 插入資料來源的方式會直接受到資料是否立即提供 (立即轉譯) 或隨選 (延遲轉譯) 所影響。 針對您藉由傳遞要使用的剪貼簿格式 (和選擇性的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構) 來提供資料的每個剪貼簿格式, 請呼叫[DelayRenderData](#delayrenderdata)。

如需有關資料來源和資料傳輸的詳細資訊, 請參閱[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)一文。 此外, 文章剪貼簿[主題](../../mfc/clipboard.md)也會描述 OLE 剪貼簿機制。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>需求

**標頭:** afxole。h

##  <a name="cachedata"></a>COleDataSource:: CacheData

呼叫此函式可指定資料傳輸作業期間提供資料的格式。

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要在其中提供資料的剪貼簿格式。 這個參數可以是預先定義的剪貼簿格式之一, 或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium)結構, 其中包含指定格式的資料。

*lpFormatEtc*<br/>
指向描述要提供資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊, 請提供此參數的值。 如果是 Null, 則會將預設值用於`FORMATETC`結構中的其他欄位。

### <a name="remarks"></a>備註

您必須提供資料, 因為此函式會使用立即呈現來提供它。 資料會在需要之前快取。

使用[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium)結構來提供資料。 如果您所提供的`CacheGlobalData`資料量夠小, 可使用 HGLOBAL 有效率地傳輸, 您也可以使用成員函式。

`CacheData`當的`ptd`成員呼叫和 lpStgMedium 的內容是由資料物件所擁有, 而不是由呼叫端所擁有`lpFormatEtc` 。

若要使用延遲轉譯, 請呼叫[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需 MFC 所處理之延遲轉譯的詳細資訊, 請參閱[資料物件和資料來源一文:操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊, 請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

如需詳細資訊, 請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="cacheglobaldata"></a>COleDataSource:: CacheGlobalData

呼叫此函式可指定資料傳輸作業期間提供資料的格式。

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要在其中提供資料的剪貼簿格式。 這個參數可以是預先定義的剪貼簿格式之一, 或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*hGlobal*<br/>
全域記憶體區塊的控制碼, 其中包含指定格式的資料。

*lpFormatEtc*<br/>
指向描述要提供資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊, 請提供此參數的值。 如果是 Null, 則會將預設值用於`FORMATETC`結構中的其他欄位。

### <a name="remarks"></a>備註

此函式會使用立即轉譯來提供資料, 因此您必須在呼叫函數時提供資料。資料會在需要之前快取。 如果您要提供大量的資料, 或如果您需要結構化的儲存媒體, 請使用成員函式。`CacheData`

若要使用延遲轉譯, 請呼叫[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需 MFC 所處理之延遲轉譯的詳細資訊, 請參閱[資料物件和資料來源一文:操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊, 請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

如需詳細資訊, 請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="coledatasource"></a>COleDataSource:: COleDataSource

建構 `COleDataSource` 物件。

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>COleDataSource::D elayRenderData

呼叫此函式可指定資料傳輸作業期間提供資料的格式。

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要在其中提供資料的剪貼簿格式。 這個參數可以是預先定義的剪貼簿格式之一, 或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpFormatEtc*<br/>
指向描述要提供資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊, 請提供此參數的值。 如果是 Null, 則會將預設值用於`FORMATETC`結構中的其他欄位。

### <a name="remarks"></a>備註

此函式會使用延遲呈現來提供資料, 因此不會立即提供資料。 呼叫[OnRenderData](#onrenderdata)或[OnRenderGlobalData](#onrenderglobaldata)成員函式以要求資料。

如果您不打算透過`CFile`物件提供您的資料, 請使用此函數。 如果您要透過`CFile`物件提供資料, 請呼叫[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需 MFC 所處理之延遲轉譯的詳細資訊, 請參閱[資料物件和資料來源一文:操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

若要使用立即呈現, 請呼叫[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成員函式。

如需詳細資訊, 請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

如需詳細資訊, 請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="delayrenderfiledata"></a>COleDataSource::D elayRenderFileData

呼叫此函式可指定資料傳輸作業期間提供資料的格式。

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要在其中提供資料的剪貼簿格式。 這個參數可以是預先定義的剪貼簿格式之一, 或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpFormatEtc*<br/>
指向描述要提供資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊, 請提供此參數的值。 如果是 Null, 則會將預設值用於`FORMATETC`結構中的其他欄位。

### <a name="remarks"></a>備註

此函式會使用延遲呈現來提供資料, 因此不會立即提供資料。 呼叫[OnRenderFileData](#onrenderfiledata)成員函式以要求資料。

如果您要使用`CFile`物件來提供資料, 請使用此函數。 如果您不打算使用`CFile`物件, 請呼叫[DelayRenderData](#delayrenderdata)成員函式。 如需 MFC 所處理之延遲轉譯的詳細資訊, 請參閱[資料物件和資料來源一文:操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

若要使用立即呈現, 請呼叫[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成員函式。

如需詳細資訊, 請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

如需詳細資訊, 請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="delaysetdata"></a>COleDataSource::D elaySetData

呼叫此函式可支援變更資料來源的內容。

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要在其中放置資料的剪貼簿格式。 這個參數可以是預先定義的剪貼簿格式之一, 或是原生 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數所傳回的值。

*lpFormatEtc*<br/>
指向描述要取代資料之格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果您想要指定超出*cfFormat*所指定剪貼簿格式的其他格式資訊, 請提供此參數的值。 如果是 Null, 則會將預設值用於`FORMATETC`結構中的其他欄位。

### <a name="remarks"></a>備註

當發生這種情況時, 架構會呼叫[OnSetData](#onsetdata) 。 只有當架構從[COleServerItem:: GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)傳回資料來源時, 才會使用這個。 如果`DelaySetData`未呼叫, 將永遠`OnSetData`不會呼叫您的函式。 `DelaySetData`應該針對您支援的每個`FORMATETC`剪貼簿或格式進行呼叫。

如需詳細資訊, 請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

如需詳細資訊, 請參閱 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="dodragdrop"></a>COleDataSource::D oDragDrop

呼叫成員函式, 為此資料來源執行拖放作業, 通常是在[CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)處理常式中。 `DoDragDrop`

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>參數

*dwEffects*<br/>
此資料來源上允許的拖放作業。 可以是下列一或多個:

- DROPEFFECT_COPY 可以執行複製作業。

- DROPEFFECT_MOVE 可以執行移動作業。

- DROPEFFECT_LINK 從已卸載的資料到原始資料的連結可能會建立。

- DROPEFFECT_SCROLL 表示可能發生拖曳捲軸操作。

*lpRectStartDrag*<br/>
定義拖曳實際開始位置之矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。

*pDropSource*<br/>
指向拖放來源。 如果是 Null, 則會使用[COleDropSource](../../mfc/reference/coledropsource-class.md)的預設執行。

### <a name="return-value"></a>傳回值

拖放作業所產生的捨棄效果;否則 DROPEFFECT_NONE 作業永遠不會開始, 因為使用者會在離開提供的矩形之前放開滑鼠按鍵。

### <a name="remarks"></a>備註

拖放作業不會立即啟動。 它會等到滑鼠游標離開*lpRectStartDrag*所指定的矩形, 或直到經過指定的毫秒數為止。 如果*lpRectStartDrag*為 Null, 則矩形的大小為一個圖元。

延遲時間是由登錄機碼設定所指定。 您可以藉由呼叫[CWinApp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[CWinApp:: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint)來變更延遲時間。 如果您未指定延遲時間, 則會使用預設值200毫秒。 拖曳延遲時間的儲存方式如下:

- Windows NT 拖曳延遲時間儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay. 中

- Windows 3.x 拖曳延遲時間會儲存在 WIN 中。INI 檔案, 位於 [Windows}] 區段底下。

- Windows 95/98 拖曳延遲時間會儲存在 WIN 的快取版本中.INI.

如需如何將拖曳延遲資訊儲存在登錄或中的詳細資訊。INI 檔, 請參閱 Windows SDK 中的[WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) 。

如需詳細資訊, 請參閱[拖放的文章:執行 Drop Source](../../mfc/drag-and-drop-implementing-a-drop-source.md)。

##  <a name="empty"></a>COleDataSource:: Empty

呼叫此函式可清空`COleDataSource`資料物件。

```
void Empty();
```

### <a name="remarks"></a>備註

快取和延遲轉譯格式都會清空, 因此可以重複使用。

如需詳細資訊, 請參閱 Windows SDK 中的[ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 。

##  <a name="flushclipboard"></a>COleDataSource:: FlushClipboard

呈現剪貼簿上的資料, 然後讓您在應用程式關閉後, 從剪貼簿貼上資料。

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>備註

使用[SetClipboard](#setclipboard)將資料放在剪貼簿上。

##  <a name="getclipboardowner"></a>COleDataSource:: GetClipboardOwner

判斷在上次呼叫[SetClipboard](#setclipboard)之後, 剪貼簿上的資料是否已變更, 如果是的話, 則會識別目前的擁有者。

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>傳回值

目前在剪貼簿上的資料來源, 如果剪貼簿上沒有任何內容, 或沒有呼叫應用程式所擁有的剪貼簿, 則為 Null。

##  <a name="onrenderdata"></a>COleDataSource:: OnRenderData

由架構呼叫, 以取得指定格式的資料。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構, 指定要求資訊的格式。

*lpStgMedium*<br/>
指向要傳回資料的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是先前`COleDataSource`使用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成員函式來呈現延遲轉譯的物件。 如果提供的儲存媒體分別是檔案或記憶體, 此函式的預設執行將會呼叫[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata) 。 如果這兩種格式都未提供, 則預設的執行會傳回 0, 而且不會執行任何動作。 如需 MFC 所處理之延遲轉譯的詳細資訊, 請參閱[資料物件和資料來源一文:操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如果*lpStgMedium* ->  *tymed*是 TYMED_Null, 則`STGMEDIUM`應該配置並填入*lpFormatEtc-> tymed*所指定的。 如果不是 TYMED_Null, `STGMEDIUM`就應該使用資料來填入。

這是一個先進的可覆寫。 覆寫此函式, 以要求的格式和媒體提供資料。 根據您的資料而定, 您可能會想要改為覆寫此函式的其中一個其他版本。 如果您的資料大小很小且固定, 請`OnRenderGlobalData`覆寫。 如果您的資料位於檔案中, 或屬於變數大小, 請覆`OnRenderFileData`寫。

如需詳細資訊, 請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構、 [TYMED](/windows/win32/api/objidl/ne-objidl-tymed)列舉類型和[IDataObject::](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)

##  <a name="onrenderfiledata"></a>COleDataSource:: OnRenderFileData

由架構呼叫, 以在指定的儲存媒體為檔案時, 以指定的格式抓取資料。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構, 指定要求資訊的格式。

*pFile*<br/>
指向要在其中呈現資料的[CFile](../../mfc/reference/cfile-class.md)物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是先前`COleDataSource`使用[DelayRenderData](#delayrenderdata)成員函式來呈現延遲轉譯的物件。 此函式的預設實作用只會傳回 FALSE。

這是一個先進的可覆寫。 覆寫此函式, 以要求的格式和媒體提供資料。 根據您的資料而定, 您可能會想要改為覆寫此函式的其中一個其他版本。 如果您想要處理多個儲存媒體, 請覆寫[OnRenderData](#onrenderdata)。 如果您的資料位於檔案中, 或屬於變數大小, 請覆`OnRenderFileData`寫。 如需 MFC 所處理之延遲轉譯的詳細資訊, 請參閱[資料物件和資料來源一文:操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊, 請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構和[IDataObject:: 操作](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)。

##  <a name="onrenderglobaldata"></a>COleDataSource:: OnRenderGlobalData

由架構呼叫, 以在指定的儲存媒體為全域記憶體時, 以指定的格式抓取資料。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構, 指定要求資訊的格式。

*phGlobal*<br/>
指向要傳回資料之全域記憶體的控制碼。 如果尚未配置, 則此參數可以是 Null。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是先前`COleDataSource`使用[DelayRenderData](#delayrenderdata)成員函式來呈現延遲轉譯的物件。 此函式的預設實作用只會傳回 FALSE。

如果*phGlobal*為 Null, 則應該在*phGlobal*中配置並傳回新的 HGLOBAL。 否則, *phGlobal*所指定的 HGLOBAL 應該填入資料。 放在 HGLOBAL 中的資料量不得超過記憶體區塊的目前大小。 此外, 區塊也無法重新配置為較大的大小。

這是一個先進的可覆寫。 覆寫此函式, 以要求的格式和媒體提供資料。 根據您的資料而定, 您可能會想要改為覆寫此函式的其中一個其他版本。 如果您想要處理多個儲存媒體, 請覆寫[OnRenderData](#onrenderdata)。 如果您的資料位於檔案中, 或屬於變數大小, 請覆寫[OnRenderFileData](#onrenderfiledata)。 如需 MFC 所處理之延遲轉譯的詳細資訊, 請參閱[資料物件和資料來源一文:操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊, 請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構和[IDataObject:: 操作](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)。

##  <a name="onsetdata"></a>COleDataSource:: OnSetData

由架構呼叫, 以指定的格式來設定或取代`COleDataSource`物件中的資料。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構, 指定要在其中取代資料的格式。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium)結構, 其中包含將會取代`COleDataSource`物件目前內容的資料。

*bRelease*<br/>
指出在完成函數呼叫之後, 誰擁有儲存媒體的擁有權。 呼叫者會決定誰負責釋放代表儲存媒體所配置的資源。 呼叫者會藉由設定*bRelease*來執行這項工作。 如果*bRelease*為非零值, 則資料來源會取得擁有權, 並在完成使用時釋放媒體。 當*bRelease*為0時, 呼叫端會保留擁有權, 而且資料來源只能在呼叫期間使用儲存媒體。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

資料來源不會取得資料的擁有權, 直到它成功取得為止。 也就是說, 如果`OnSetData`傳回 0, 則不會取得擁有權。 如果資料來源取得擁有權, 它會藉由呼叫[ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium)函數來釋放儲存媒體。

預設實作不做任何動作。 覆寫此函式以取代指定之格式的資料。 這是一個先進的可覆寫。

如需詳細資訊, 請參閱[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構和 Windows SDK 中的[ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium)和[IDataObject::](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)程式函數。

##  <a name="setclipboard"></a>COleDataSource:: SetClipboard

呼叫下列其中一個函數之後`COleDataSource` , 將包含在物件中的資料放在剪貼簿上:[CacheData](#cachedata)、 [CacheGlobalData](#cacheglobaldata)、 [DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)。

```
void SetClipboard();
```

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject 類別](../../mfc/reference/coledataobject-class.md)
