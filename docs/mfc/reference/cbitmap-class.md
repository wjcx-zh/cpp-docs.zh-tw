---
title: CBitmap 類別
ms.date: 11/04/2016
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
ms.openlocfilehash: 7161a4cf4484b6cc9e76e6955de558ca6e9121ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418955"
---
# <a name="cbitmap-class"></a>CBitmap 類別

封裝 Windows 繪圖裝置介面 (GDI) 點陣圖，並提供操作點陣圖的成員函式。

## <a name="syntax"></a>語法

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CBitmap：： CBitmap](#cbitmap)|建構 `CBitmap` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBitmap：： CreateBitmap](#createbitmap)|使用具有指定寬度、高度和位模式的裝置相依記憶體點陣圖，初始化物件。|
|[CBitmap：： CreateBitmapIndirect](#createbitmapindirect)|使用在 `BITMAP` 結構中提供的寬度、高度和位模式（如果有指定的話），初始化具有點陣圖的物件。|
|[CBitmap：： CreateCompatibleBitmap](#createcompatiblebitmap)|使用點陣圖初始化物件，使其與指定的裝置相容。|
|[CBitmap：： CreateDiscardableBitmap](#creatediscardablebitmap)|使用與指定裝置相容的可捨棄點陣圖，初始化物件。|
|[CBitmap：： FromHandle](#fromhandle)|當給定 Windows `HBITMAP` 點陣圖的控制碼時，傳回 `CBitmap` 物件的指標。|
|[CBitmap：： GetBitmap](#getbitmap)|以點陣圖的相關資訊填入 `BITMAP` 結構。|
|[CBitmap：： GetBitmapBits](#getbitmapbits)|將指定點陣圖的位複製到指定的緩衝區。|
|[CBitmap：： GetBitmapDimension](#getbitmapdimension)|傳回點陣圖的寬度和高度。 高度和寬度假設先前已由[SetBitmapDimension](#setbitmapdimension)成員函式設定。|
|[CBitmap：： LoadBitmap](#loadbitmap)|從應用程式的可執行檔載入名為點陣圖資源，並將點陣圖附加至物件，以初始化物件。|
|[CBitmap：： LoadMappedBitmap](#loadmappedbitmap)|載入點陣圖，並將色彩對應至目前的系統色彩。|
|[CBitmap：： LoadOEMBitmap](#loadoembitmap)|藉由載入預先定義的 Windows 點陣圖並將點陣圖附加至物件，初始化物件。|
|[CBitmap：： SetBitmapBits](#setbitmapbits)|將點陣圖的位設定為指定的位值。|
|[CBitmap：： SetBitmapDimension](#setbitmapdimension)|將寬度和高度指派給以 0.1-毫米單位表示的點陣圖。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CBitmap：： operator HBITMAP](#operator_hbitmap)|傳回附加至 `CBitmap` 物件的 Windows 控制碼。|

## <a name="remarks"></a>備註

若要使用 `CBitmap` 物件，請建立物件，並使用其中一個初始化成員函式附加點陣圖控制碼，然後呼叫物件的成員函式。

如需使用 `CBitmap`等繪圖物件的詳細資訊，請參閱[繪圖物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cbitmap"></a>CBitmap：： CBitmap

建構 `CBitmap` 物件。

```
CBitmap();
```

### <a name="remarks"></a>備註

產生的物件必須使用其中一個初始化成員函式來初始化。

##  <a name="createbitmap"></a>CBitmap：： CreateBitmap

初始化具有指定寬度、高度和位元模式之因裝置而異的記憶體點陣圖。

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
指定點陣圖的寬度 (以像素為單位)。

*nHeight*<br/>
指定點陣圖的高度 (以像素為單位)。

*nPlanes*<br/>
指定點陣圖中色彩平面的數目。

*nBitcount*<br/>
指定每個顯示像素的色彩位元數目。

*lpBits*<br/>
指向位元組陣列，其中包含初始點陣圖位元值。 如果為 NULL，則不會初始化新的點陣圖。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

若為色彩點陣圖， *nPlanes*或*nBitcount*參數應該設定為1。 如果這兩個參數都設為 1， `CreateBitmap` 會建立單色點陣圖。

雖然您無法直接選取用於顯示裝置的點陣圖，但可以使用 [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) 選取一個點陣圖作為「記憶體裝置內容」的目前點陣圖，再使用 [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) 函式將該點陣圖複製到任何相容裝置內容。

當您完成使用 `CBitmap` 函式所建立的 `CreateBitmap` 物件時，請先選取點陣圖並移出裝置內容，再刪除 `CBitmap` 物件。

如需詳細資訊，請參閱 `BITMAP` 結構中 [`bmBits`] 欄位的描述。 [CBitmap::CreateBitmapIndirect](/windows/win32/api/wingdi/ns-wingdi-bitmap) 成員函式下提供 [BITMAP](#createbitmapindirect) 結構的說明。

##  <a name="createbitmapindirect"></a>CBitmap：： CreateBitmapIndirect

在*lpBitmap*所指向的結構中，初始化具有寬度、高度和位模式（如果有指定）的點陣圖。

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>參數

*lpBitmap*<br/>
指向包含點陣圖相關資訊的[點陣圖](/windows/win32/api/wingdi/ns-wingdi-bitmap)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

雖然無法直接選取顯示裝置的點陣圖，但可以使用[cdc：： SelectObject](../../mfc/reference/cdc-class.md#selectobject)將它選取為記憶體裝置內容的目前點陣圖，並使用[Cdc：： BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[cdc：： StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函式將它複製到任何相容的裝置內容。 （ [CDC：:P atblt](../../mfc/reference/cdc-class.md#patblt)函數可以將目前筆刷的點陣圖直接複製到顯示裝置內容）。

如果*lpBitmap*參數所指向的 `BITMAP` 結構已使用 `GetObject` 函數填入，則不會指定點陣圖的位，且點陣圖會解除初始化。 若要初始化點陣圖，應用程式可以使用[CDC：： BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits)這類函式，從 `CGdiObject::GetObject` 的第一個參數所識別的點陣圖，將位複製到 `CreateBitmapIndirect`所建立的點陣圖。

當您完成使用 `CreateBitmapIndirect` 函數所建立的 `CBitmap` 物件時，請先從裝置內容中選取點陣圖，然後刪除 `CBitmap` 物件。

##  <a name="createcompatiblebitmap"></a>CBitmap：： CreateCompatibleBitmap

初始化與*pDC*所指定裝置相容的點陣圖。

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指定裝置內容。

*nWidth*<br/>
指定點陣圖的寬度 (以像素為單位)。

*nHeight*<br/>
指定點陣圖的高度 (以像素為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖具有相同數目的色彩平面，或與指定的裝置內容具有相同的每圖元位格式。 您可以選取它做為任何記憶體裝置的目前點陣圖，其與*pDC*所指定的不同。

如果*pDC*是記憶體裝置內容，傳回的點陣圖與該裝置內容中目前選取的點陣圖具有相同的格式。 「記憶體裝置內容」是表示顯示介面的記憶體區塊。 它可以用來在將影像複製到相容裝置的實際顯示介面之前，先在記憶體中準備映射。

建立記憶體裝置內容時，GDI 會自動為其選取單色股票點陣圖。

因為彩色記憶體裝置內容可以選取彩色或單色點陣圖，所以 `CreateCompatibleBitmap` 函式所傳回之點陣圖的格式不一定是相同的;不過，nonmemory 裝置內容的相容點陣圖格式一律是裝置的格式。

當您完成使用 `CreateCompatibleBitmap` 函數所建立的 `CBitmap` 物件時，請先從裝置內容中選取點陣圖，然後刪除 `CBitmap` 物件。

##  <a name="creatediscardablebitmap"></a>CBitmap：： CreateDiscardableBitmap

初始化與*pDC*所識別的裝置內容相容的可捨棄點陣圖。

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指定裝置內容。

*nWidth*<br/>
指定點陣圖的寬度（以位為單位）。

*nHeight*<br/>
指定點陣圖的高度（以位為單位）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖具有相同數目的色彩平面，或與指定的裝置內容具有相同的每圖元位格式。 應用程式可以選取此點陣圖做為記憶體裝置的目前點陣圖，此為與*pDC*所指定的相容。

只有當應用程式尚未將此函式選取為顯示內容時，Windows 才能捨棄此功能所建立的點陣圖。 如果 Windows 在未選取的情況下捨棄點陣圖，而應用程式之後又嘗試選取它， [CDC：： SelectObject](../../mfc/reference/cdc-class.md#selectobject)函數會傳回 Null。

當您完成使用 `CreateDiscardableBitmap` 函數所建立的 `CBitmap` 物件時，請先從裝置內容中選取點陣圖，然後刪除 `CBitmap` 物件。

##  <a name="fromhandle"></a>CBitmap：： FromHandle

當指定 Windows GDI 點陣圖的控制碼時，傳回 `CBitmap` 物件的指標。

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
指定 Windows GDI 點陣圖。

### <a name="return-value"></a>傳回值

如果成功，則為 `CBitmap` 物件的指標;否則為 Null。

### <a name="remarks"></a>備註

如果 `CBitmap` 物件尚未附加至控制碼，則會建立並附加暫存 `CBitmap` 物件。 只有在下次應用程式的事件迴圈中有閒置時間時，才會將這個暫存 `CBitmap` 物件有效，此時所有的暫存繪圖物件都會被刪除。 另一個指出這種情況的方法是，暫存物件只在處理一個視窗訊息期間有效。

##  <a name="getbitmap"></a>CBitmap：： GetBitmap

抓取附加點陣圖的影像屬性。

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>參數

*pBitMap*<br/>
將會接收影像屬性之[點陣圖](/windows/win32/api/wingdi/ns-wingdi-bitmap)結構的指標。 此參數不得為 Null。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零;否則為0。

### <a name="remarks"></a>備註

##  <a name="getbitmapbits"></a>CBitmap：： GetBitmapBits

將附加點陣圖的位模式複製到指定的緩衝區。

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>參數

*dwCount*<br/>
要複製到緩衝區的位元組數目。

*lpBits*<br/>
將接收點陣圖之緩衝區的指標。

### <a name="return-value"></a>傳回值

如果方法成功，則複製到緩衝區的位元組數目;否則為0。

### <a name="remarks"></a>備註

請使用[CBitmap：： GetBitmap](#getbitmap)來判斷所需的緩衝區大小。

##  <a name="getbitmapdimension"></a>CBitmap：： GetBitmapDimension

傳回點陣圖的寬度和高度。

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>傳回值

點陣圖的寬度和高度，以 0.1-毫米單位來測量。 高度位於 `CSize` 物件的 `cy` 成員中，而寬度則位於 `cx` 成員中。 如果未使用 `SetBitmapDimension`設定點陣圖寬度和高度，則傳回值為0。

### <a name="remarks"></a>備註

高度和寬度會假設為先前使用[SetBitmapDimension](#setbitmapdimension)成員函式設定的。

##  <a name="loadbitmap"></a>CBitmap：： LoadBitmap

載入*lpszResourceName*所命名的點陣圖資源，或從應用程式的可執行檔中，由*NIDRESOURCE*中的識別碼所識別。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
指向以 null 終止的字串，其中包含點陣圖資源的名稱。

*nIDResource*<br/>
指定點陣圖資源的資源識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

載入的點陣圖會附加至 `CBitmap` 物件。

如果*lpszResourceName*所識別的點陣圖不存在，或沒有足夠的記憶體可載入點陣圖，則函式會傳回0。

您可以使用[CGdiObject：:D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)函式來刪除由 `LoadBitmap` 函數載入的點陣圖，否則 `CBitmap` 的析構函數將會為您刪除物件。

> [!CAUTION]
>  在您刪除物件之前，請確定它未選取到裝置內容中。

下列點陣圖已新增至 Windows 版本3.1 和更新版本：

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

在 Windows 3.0 版和更早版本的設備磁碟機中，找不到這些點陣圖。 如需完整的點陣圖清單和其外觀的顯示，請參閱 Windows SDK。

##  <a name="loadmappedbitmap"></a>CBitmap：： LoadMappedBitmap

呼叫這個成員函式以載入點陣圖，並將色彩對應至目前的系統色彩。

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>參數

*nIDBitmap*<br/>
點陣圖資源的識別碼。

*nFlags*<br/>
點陣圖的旗標。 可以是零或 CMB_MASKED。

*lpColorMap*<br/>
`COLORMAP` 結構的指標，其中包含對應點陣圖所需的色彩資訊。 如果此參數為 Null，則函式會使用預設色彩對應。

*nMapSize*<br/>
*LpColorMap*所指向的色彩對應數目。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

根據預設，`LoadMappedBitmap` 會對應按鈕圖像中常用的色彩。

如需建立對應點陣圖的詳細資訊，請參閱 Windows 函式[CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562)和 Windows SDK 中的[COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap)結構。

##  <a name="loadoembitmap"></a>CBitmap：： LoadOEMBitmap

載入 Windows 所使用的預先定義點陣圖。

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>參數

*nIDBitmap*<br/>
預先定義之 Windows 點陣圖的 ID 編號。 這些可能的值從 WINDOWS 列出。H

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

開頭為 OBM_OLD 的點陣圖名稱，代表3.0 之前的 Windows 版本所使用的點陣圖。

請注意，必須先定義常數 OEMRESOURCE，才能包含 WINDOWS。H，以便使用任何**OBM_** 常數。

##  <a name="operator_hbitmap"></a>CBitmap：： operator HBITMAP

使用這個運算子取得 `CBitmap` 物件的附加 Windows GDI 控制碼。

```
operator HBITMAP() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為 `CBitmap` 物件所表示之 Windows GDI 物件的控制碼;否則為 Null。

### <a name="remarks"></a>備註

這個運算子是一個轉型運算子，可支援直接使用 `HBITMAP` 物件。

如需使用繪圖物件的詳細資訊，請參閱 Windows SDK 中的[繪圖物件](/windows/win32/gdi/graphic-objects)。

##  <a name="setbitmapbits"></a>CBitmap：： SetBitmapBits

將點陣圖的位設定為*lpBits*所指定的位值。

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>參數

*dwCount*<br/>
指定*lpBits*所指向的位元組數目。

*lpBits*<br/>
指向包含要複製到 `CBitmap` 物件之圖元值的位元組陣列。 為了讓點陣圖能夠正確地轉譯其影像，應將值格式化，以符合建立 CBitmap 實例時所指定的高度、寬度和色彩深度值。 如需詳細資訊，請參閱[CBitmap：： CreateBitmap](#createbitmap)。

### <a name="return-value"></a>傳回值

用於設定點陣圖位的位元組數目;如果函數失敗，則為0。

##  <a name="setbitmapdimension"></a>CBitmap：： SetBitmapDimension

將寬度和高度指派給以 0.1-毫米單位表示的點陣圖。

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
指定點陣圖的寬度（以 0.1-毫米為單位）。

*nHeight*<br/>
指定點陣圖的高度（以 0.1-毫米為單位）。

### <a name="return-value"></a>傳回值

先前的點陣圖維度。 Height 位於 `CSize` 物件的 `cy` 成員變數中，而 width 是在 `cx` 成員變數中。

### <a name="remarks"></a>備註

除了在應用程式呼叫[GetBitmapDimension](#getbitmapdimension)成員函式時傳回它們以外，GDI 不會使用這些值。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
