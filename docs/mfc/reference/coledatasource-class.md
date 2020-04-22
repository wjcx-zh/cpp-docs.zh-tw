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
ms.openlocfilehash: 8746be43e3f2a31558904323392983b183d4f198
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753892"
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
|[COleData 來源:COleData 來源](#coledatasource)|建構 `COleDataSource` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleData 來源:快取資料](#cachedata)|使用`STGMEDIUM`結構以指定格式提供數據。|
|[COleData 來源:快取全球資料](#cacheglobaldata)|使用 HGLOBAL 以指定格式提供數據。|
|[COleData 來源::DelayRenderData](#delayrenderdata)|使用延遲呈現以指定格式提供數據。|
|[COleData 來源::DelayRender文件資料](#delayrenderfiledata)|在`CFile`指標中提供指定格式的數據。|
|[COleData 來源::DelaySetData](#delaysetdata)|呼叫`OnSetData`中 支援的每個格式。|
|[COleData 來源::DoDragDrop](#dodragdrop)|使用數據源執行拖放操作。|
|[COleData 來源::空](#empty)|清空數據`COleDataSource`物件。|
|[COleData 來源::Flush 剪板](#flushclipboard)|將所有數據渲染到剪貼簿。|
|[COleData 來源:取得剪貼簿擁有者](#getclipboardowner)|驗證放置在剪貼簿上的數據是否仍然存在。|
|[COleData 來源:在渲染資料上](#onrenderdata)|檢索數據作為延遲呈現的一部分。|
|[COleData 來源:在渲染檔案資料上](#onrenderfiledata)|將數據檢索到`CFile`作為延遲呈現的一部分。|
|[COleData 來源:在渲染全球資料上](#onrenderglobaldata)|將數據檢索到 HGLOBAL 中,作為延遲呈現的一部分。|
|[COleData 來源:OnSetData](#onsetdata)|調用以替換對象`COleDataSource`中 的數據。|
|[COleData 來源:設定剪貼簿](#setclipboard)|將`COleDataSource`物件放在剪貼板上。|

## <a name="remarks"></a>備註

您可以直接創建 OLE 資料來源。 或者[,COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem 類](../../mfc/reference/coleserveritem-class.md)創建`CopyToClipboard`OLE 資料來源以回應 它們`DoDragDrop`和成員函數。 有關簡要說明,請參閱[COleServer 專案:複製到剪貼簿](../../mfc/reference/coleserveritem-class.md#copytoclipboard)。 重寫客戶`OnGetClipboardData`端 項或伺服器項類的成員函數,以`CopyToClipboard`向`DoDragDrop`為或成員函數創建的 OLE 資料來源中的數據添加其他剪貼簿格式。

每當您想要為傳輸準備數據時,都應創建此類的物件,並使用最適合數據的方法填充數據。 將資料插入到數據源的方式受是立即提供(立即呈現)還是按需(延遲呈現)的直接影響。 對於透過傳遞要使用的剪貼簿格式(與可選[的 FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構)提供資料的每個剪貼簿格式,呼叫[DelayRenderData](#delayrenderdata)。

有關數據源和數據傳輸的詳細資訊,請參閱文章[「數據物件和數據來源 (OLE)」。。](../../mfc/data-objects-and-data-sources-ole.md) 此外,文章[剪貼簿主題](../../mfc/clipboard.md)描述了 OLE 剪貼簿機制。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a>COleData 來源:快取資料

呼叫此函數以指定在資料傳輸操作期間提供資料的格式。

```cpp
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
提供數據的剪貼簿格式。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*lpStg 中*<br/>
指向包含指定格式數據的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

*lpFormatEtc*<br/>
指向描述提供資料的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊,請提供此參數的值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="remarks"></a>備註

您必須提供數據,因為此函數使用即時呈現來提供數據。 數據將緩存到需要為止。

使用[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構提供數據。 如果提供的數據量足夠`CacheGlobalData`小,可以使用 HGLOBAL 高效地傳輸,則可以使用成員函數。

對`CacheData``ptd` *lpStgMedia*`lpFormatEtc`的成員和內容的調用後,由數據對象擁有,而不是由調用方擁有。

要使用延遲渲染,請致電[延遲渲染數據](#delayrenderdata)或[延遲呈現檔資料](#delayrenderfiledata)成員函數。 有關 MFC 處理的延遲呈現的詳細資訊,請參閱文章[「數據物件和數據來源:操作](../../mfc/data-objects-and-data-sources-manipulation.md)」。。

有關詳細資訊,請參閱 Windows SDK 中的[STG 中](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a>COleData 來源:快取全球資料

呼叫此函數以指定在資料傳輸操作期間提供資料的格式。

```cpp
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
提供數據的剪貼簿格式。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*hGlobal*<br/>
以指定的格式處理包含資料的全域記憶體區塊。

*lpFormatEtc*<br/>
指向描述提供資料的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊,請提供此參數的值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="remarks"></a>備註

此函數使用即時呈現提供數據,因此在調用 函數時必須提供數據;因此,在調用函數時,必須提供數據。數據被緩存,直到需要為止。 如果要提供大量`CacheData`數據,或者需要結構化存儲介質,請使用成員函數。

要使用延遲渲染,請致電[延遲渲染數據](#delayrenderdata)或[延遲呈現檔資料](#delayrenderfiledata)成員函數。 有關 MFC 處理的延遲呈現的詳細資訊,請參閱文章[「數據物件和數據來源:操作](../../mfc/data-objects-and-data-sources-manipulation.md)」。。

有關詳細資訊,請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a>COleData 來源:COleData 來源

建構 `COleDataSource` 物件。

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a>COleData 來源::DelayRenderData

呼叫此函數以指定在資料傳輸操作期間提供資料的格式。

```cpp
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
提供數據的剪貼簿格式。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*lpFormatEtc*<br/>
指向描述提供資料的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊,請提供此參數的值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="remarks"></a>備註

此函數使用延遲呈現提供數據,因此不會立即提供數據。 呼叫[OnRenderData](#onrenderdata)或[OnRenderGlobalData](#onrenderglobaldata)成員函數來請求數據。

如果不透過物件提供資料,`CFile`請使用此功能。 如果要通過`CFile`物件提供數據,請調用[DelayRenderFileData](#delayrenderfiledata)成員函數。 有關 MFC 處理的延遲呈現的詳細資訊,請參閱文章[「數據物件和數據來源:操作](../../mfc/data-objects-and-data-sources-manipulation.md)」。。

要使用即時呈現,請調用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成員函數。

有關詳細資訊,請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a>COleData 來源::DelayRender文件資料

呼叫此函數以指定在資料傳輸操作期間提供資料的格式。

```cpp
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
提供數據的剪貼簿格式。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*lpFormatEtc*<br/>
指向描述提供資料的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊,請提供此參數的值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="remarks"></a>備註

此函數使用延遲呈現提供數據,因此不會立即提供數據。 呼叫[OnRenderFileData](#onrenderfiledata)成員函數來請求數據。

如果要使用`CFile`物件來提供數據,請使用此功能。 如果不使用物件,`CFile`請呼叫[DelayRenderData](#delayrenderdata)成員函數。 有關 MFC 處理的延遲呈現的詳細資訊,請參閱文章[「數據物件和數據來源:操作](../../mfc/data-objects-and-data-sources-manipulation.md)」。。

要使用即時呈現,請調用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成員函數。

有關詳細資訊,請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a>COleData 來源::DelaySetData

呼叫此函數以支援更改數據來源的內容。

```cpp
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要放置資料的剪貼簿格式。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*lpFormatEtc*<br/>
指向描述要替換資料的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊,請提供此參數的值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="remarks"></a>備註

發生這種情況時,框架將調用[OnSetData。](#onsetdata) 只當框架從[COleServerItem 傳回資料來源時,才使用這個選項:getDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)。 如果未`DelaySetData`調用,則永遠不會調用`OnSetData`函數。 `DelaySetData`應針對您支援的每個剪貼簿`FORMATETC`或格式呼叫。

有關詳細資訊,請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a>COleData 來源::DoDragDrop

調用`DoDragDrop`成員函數以對此數據源執行拖放操作,通常在[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)處理程式中。

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>參數

*dwEffects*<br/>
在此數據源上允許的拖放操作。 可以是以下一種或多項:

- DROPEFFECT_COPY可以執行複製操作。

- DROPEFFECT_MOVE可以執行移動操作。

- DROPEFFECT_LINK 可以建立從刪除數據到原始數據的連結。

- DROPEFFECT_SCROLL指示可能發生拖動滾動操作。

*lpRect 開始拖動*<br/>
指向定義拖動實際開始位置的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。

*pDrop來源*<br/>
指向放置源。 如果 NULL,則將使用[COleDropSource](../../mfc/reference/coledropsource-class.md)的預設實現。

### <a name="return-value"></a>傳回值

拖放操作生成的拖放效果;否則,如果操作從未開始,則DROPEFFECT_NONE,因為使用者在離開提供的矩形之前釋放了滑鼠按鈕。

### <a name="remarks"></a>備註

拖放操作不會立即啟動。 它等待滑鼠游標離開*lpRectStartDrag 指定的*矩形或直到經過指定數量的毫秒。 如果*lpRectStartDrag*是 NULL,則矩形的大小為一個圖元。

延遲時間由註冊表鍵設置指定。 您可以通過調用[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint)來更改延遲時間。 如果不指定延遲時間,則使用預設值 200 毫秒。 拖動延遲時間儲存如下:

- Windows NT 拖動延遲時間存儲在HKEY_LOCAL_MACHINE_SOFTWARE_微軟\Windows_NT_當前版本\iniFile映射\win.ini_Windows_Dragdelay。

- Windows 3.x 拖動延遲時間存儲在 WIN 中。INI 檔,在 [Windows] 部分下。

- Windows 95/98 拖動延遲時間存儲在 WIN 的緩存版本中。Ini。

有關拖動延遲資訊如何存儲在註冊表或 中的詳細資訊。INI 檔案,請參閱 Windows SDK 中的[寫入設定檔字串](/windows/win32/api/winbase/nf-winbase-writeprofilestringw)。

有關詳細資訊,請參閱文章 OLE[拖放](../../mfc/drag-and-drop-ole.md)。

## <a name="coledatasourceempty"></a><a name="empty"></a>COleData 來源::空

調用此函數以清空數據`COleDataSource`物件。

```cpp
void Empty();
```

### <a name="remarks"></a>備註

快取和延遲渲染格式都將清空,以便可以重複使用。

有關詳細資訊,請參閱 Windows SDK 中的[發佈 StgMedia。](/windows/win32/api/ole2/nf-ole2-releasestgmedium)

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a>COleData 來源::Flush 剪板

渲染剪貼簿上的數據,然後允許您在應用程式關閉后粘貼剪貼簿中的數據。

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>備註

使用[SetClip 板](#setclipboard)將數據放在剪貼簿上。

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a>COleData 來源:取得剪貼簿擁有者

確定自上次調用[SetClipboard](#setclipboard)以來,剪貼簿上的數據是否已更改,如果是,則標識當前擁有者。

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>傳回值

如果剪貼簿上沒有任何內容或剪貼簿不是調用應用程式所有,則當前剪貼簿上的數據源或 NULL。

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a>COleData 來源:在渲染資料上

框架調用以檢索指定格式的數據。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構,指定請求資訊的格式。

*lpStg 中*<br/>
指向要返回數據的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是以前使用`COleDataSource`[延遲渲染數據](#delayrenderdata)或[延遲渲染文件](#delayrenderfiledata)成員函數放置在物件中的格式,用於延遲渲染。 如果提供的儲存媒體分別是檔或記憶體,則此函數的預設實現將調用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData。](#onrenderglobaldata) 如果未提供這兩種格式,則默認實現將返回 0,並且不執行任何操作。 有關 MFC 處理的延遲呈現的詳細資訊,請參閱文章[「數據物件和數據來源:操作](../../mfc/data-objects-and-data-sources-manipulation.md)」。。

如果*lpStg 中*-> *tymed* TYMED_NULL,`STGMEDIUM`則應按*lpFormatEtc->tymed*指定的分配和填充。 沒有未TYMED_NULL,`STGMEDIUM`則套用資料填滿 。

這是一個高級的可重寫。 重寫此函數以請求的格式和媒體提供資料。 根據數據的不同,您可能希望重寫此函數的其他版本之一。 如果資料較小且大小固定,請重寫`OnRenderGlobalData`。 如果資料位於檔案中,或大小可變,請重寫`OnRenderFileData`。

有關詳細資訊,請參閱[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構[、TYMED](/windows/win32/api/objidl/ne-objidl-tymed)枚舉類型和[IDataObject:取得](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的數據。

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a>COleData 來源:在渲染檔案資料上

當指定的儲存媒體是檔時,框架呼叫以指定格式檢索資料。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構,指定請求資訊的格式。

*pFile*<br/>
指向要呈現數據的[CFile](../../mfc/reference/cfile-class.md)物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是以前使用`COleDataSource`[DelayRenderData](#delayrenderdata)成員函數放置在物件中的格式,用於延遲渲染。 此函數的預設實現僅返回 FALSE。

這是一個高級的可重寫。 重寫此函數以請求的格式和媒體提供資料。 根據數據的不同,您可能希望重寫此函數的其他版本之一。 如果要處理多個儲存媒體,則重寫[OnRenderData](#onrenderdata)。 如果資料位於檔案中,或大小可變,請重寫`OnRenderFileData`。 有關 MFC 處理的延遲呈現的詳細資訊,請參閱文章[「數據物件和數據來源:操作](../../mfc/data-objects-and-data-sources-manipulation.md)」。。

有關詳細資訊,請參閱[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構和[IDataObject::獲取](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的數據。

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleData 來源:在渲染全球資料上

當指定的存儲媒體是全域記憶體時,框架調用以指定格式檢索資料。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構,指定請求資訊的格式。

*phGlobal*<br/>
指向要返回數據的全域記憶體的句柄。 如果尚未分配,則此參數可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是以前使用`COleDataSource`[DelayRenderData](#delayrenderdata)成員函數放置在物件中的格式,用於延遲渲染。 此函數的預設實現僅返回 FALSE。

如果*phGlobal*為 NULL,則應在 phGLOBAL 中分配並返回新的*HGLOBAL。* 否則 *,phGLOBAL*指定的 HGLOBAL 應填充數據。 放置在 HGLOBAL 中的數據量不得超過記憶體區塊的當前大小。 此外,塊無法重新分配到更大的大小。

這是一個高級的可重寫。 重寫此函數以請求的格式和媒體提供資料。 根據數據的不同,您可能希望重寫此函數的其他版本之一。 如果要處理多個儲存媒體,則重寫[OnRenderData](#onrenderdata)。 如果資料位於檔案中,或者大小可變,請覆[寫 OnRenderFileData](#onrenderfiledata)。 有關 MFC 處理的延遲呈現的詳細資訊,請參閱文章[「數據物件和數據來源:操作](../../mfc/data-objects-and-data-sources-manipulation.md)」。。

有關詳細資訊,請參閱[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構和[IDataObject::獲取](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的數據。

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a>COleData 來源:OnSetData

框架呼叫以指定格式設定或替換物件中`COleDataSource`的資料。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構,指定要替換數據的格式。

*lpStg 中*<br/>
指向包含將替換`COleDataSource`物件當前內容的數據的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

*b釋放*<br/>
指示誰在完成函數調用後擁有存儲介質的擁有權。 調用方決定由誰負責釋放代表存儲介質分配的資源。 調用方通過設置*bRelease*來進行此用。 如果*bRelease*是非零,數據源將取得擁有權,在它完成使用後釋放媒體。 當*bRelease*為 0 時,調用方將保留擁有權,數據源只能在呼叫期間使用存儲介質。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

數據源在成功獲取數據之前不會取得數據的擁有權。 也就是說,如果`OnSetData`返回 0,它不擁有擁有權。 如果數據源擁有擁有權,則通過調用[ReleaseStgMedia](/windows/win32/api/ole2/nf-ole2-releasestgmedium)函數釋放存儲介質。

預設實作不做任何動作。 重寫此函數以替換指定格式的數據。 這是一個高級的可重寫。

有關詳細資訊,請參閱[STGMEDIA](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構以及[發佈媒體](/windows/win32/api/ole2/nf-ole2-releasestgmedium)和[IDataObject:獲取 Windows](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) SDK 中的數據功能。

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a>COleData 來源:設定剪貼簿

呼叫以下函數的一後`COleDataSource`, 將物件中包含的資料放在剪貼簿上:[快取資料](#cachedata)、[快取全域資料](#cacheglobaldata),[延遲呈現資料](#delayrenderdata)或[延遲呈現檔案資料](#delayrenderfiledata)。

```cpp
void SetClipboard();
```

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject 類別](../../mfc/reference/coledataobject-class.md)
