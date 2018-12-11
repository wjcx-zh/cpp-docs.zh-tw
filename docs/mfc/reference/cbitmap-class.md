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
ms.openlocfilehash: 6722011bf343a391fcc7180558eead5c039afc59
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178170"
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
|[CBitmap::CBitmap](#cbitmap)|建構 `CBitmap` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBitmap::CreateBitmap](#createbitmap)|初始化具有指定的寬度、 高度和位元模式的裝置而異的記憶體點陣圖物件。|
|[Createbitmapindirect](#createbitmapindirect)|初始化物件的點陣圖寬度、 高度和位元模式 （如果已指定） 列入`BITMAP`結構。|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|初始化與點陣圖物件，使其與指定的裝置相容。|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|初始化具有指定裝置相容的可捨棄點陣圖物件。|
|[CBitmap::FromHandle](#fromhandle)|將指標傳回至`CBitmap`物件時控制代碼給 Windows`HBITMAP`點陣圖。|
|[CBitmap::GetBitmap](#getbitmap)|填滿`BITMAP`點陣圖的相關資訊的結構。|
|[CBitmap::GetBitmapBits](#getbitmapbits)|將指定的點陣圖的位元複製到指定的緩衝區。|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|傳回點陣圖的高度與寬度。 高度和寬度會假設已設定先前[SetBitmapDimension](#setbitmapdimension)成員函式。|
|[Cbitmap:: Loadbitmap](#loadbitmap)|從應用程式的可執行檔載入具名的點陣圖資源，並附加至物件的點陣圖，初始化物件。|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|載入點陣圖，並將對應至目前的系統色彩的色彩。|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|藉由載入預先定義的 Windows 點陣圖和附加至物件的點陣圖，初始化物件。|
|[CBitmap::SetBitmapBits](#setbitmapbits)|將點陣圖的位元設定為指定的位元值。|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|指派為點陣圖，以 0.1 公釐為單位的寬度和高度。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CBitmap::operator HBITMAP](#operator_hbitmap)|傳回附加至的 Windows 控制代碼`CBitmap`物件。|

## <a name="remarks"></a>備註

若要使用`CBitmap`物件建構物件、 將點陣圖控制代碼附加至其中一個成員函式初始化，它，然後呼叫物件的成員函式。

如需有關使用圖形的物件，例如`CBitmap`，請參閱 <<c2> [ 圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cbitmap"></a>  CBitmap::CBitmap

建構 `CBitmap` 物件。

```
CBitmap();
```

### <a name="remarks"></a>備註

產生的物件必須初始化使用其中一個成員函式初始化。

##  <a name="createbitmap"></a>  CBitmap::CreateBitmap

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
指向位元組陣列，其中包含初始點陣圖位元值。 如果它是 NULL，新的點陣圖未初始化。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

若是彩色點陣圖，任一*nPlanes*或是*nBitcount*參數應設為 1。 如果這兩個參數都設為 1， `CreateBitmap` 會建立單色點陣圖。

雖然您無法直接選取用於顯示裝置的點陣圖，但可以使用 [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) 選取一個點陣圖作為「記憶體裝置內容」的目前點陣圖，再使用 [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) 函式將該點陣圖複製到任何相容裝置內容。

當您完成使用 `CBitmap` 函式所建立的 `CreateBitmap` 物件時，請先選取點陣圖並移出裝置內容，再刪除 `CBitmap` 物件。

如需詳細資訊，請參閱說明`bmBits`欄位中`BITMAP`結構。 [CBitmap::CreateBitmapIndirect](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap) 成員函式下提供 [BITMAP](#createbitmapindirect) 結構的說明。

##  <a name="createbitmapindirect"></a>  Createbitmapindirect

初始化具有寬度、 高度和位元模式 （如果已指定） 中所指向的結構指定的點陣圖*lpBitmap*。

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>參數

*lpBitmap*<br/>
指向[點陣圖](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap)包含點陣圖的相關資訊的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

雖然您無法直接選取點陣圖，顯示裝置，也可以選取作為記憶體裝置內容的目前點陣圖使用[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)並複製到任何相容裝置內容中，使用[Cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)或是[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函式。 ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt)函式可以將目前的筆刷的點陣圖複製直接到顯示裝置內容。)

如果`BITMAP`結構所指*lpBitmap*參數填入使用`GetObject`函式未指定點陣圖的位元和點陣圖未初始化。 若要初始化的點陣圖，應用程式可以使用函式這類[cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits)複製點陣圖的第一個參數所識別的 bits`CGdiObject::GetObject`為所建立的點陣圖`CreateBitmapIndirect`.

當您完成使用`CBitmap`物件以建立`CreateBitmapIndirect`函式，請先選取點陣圖並移出裝置內容，然後刪除`CBitmap`物件。

##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap

初始化與所指定的裝置相容的點陣圖*pDC*。

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指定的裝置內容。

*nWidth*<br/>
指定點陣圖的寬度 (以像素為單位)。

*nHeight*<br/>
指定點陣圖的高度 (以像素為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖有相同數目的色彩平面或相同的每個像素的位元格式，為指定的裝置內容。 適用於所指定的任何記憶體裝置的目前點陣圖當做*pDC*。

如果*pDC*是記憶體裝置內容，傳回的點陣圖具有相同的格式，為目前所選的點陣圖，在該裝置內容中。 「 記憶體裝置內容 」 是記憶體的表示顯示表面區塊。 它可以用來準備在記憶體中的映像，再將它們複製到相容的裝置的實際顯示表面。

建立記憶體裝置內容時，GDI 就會自動為它選取單色的內建點陣圖。

由於色彩記憶體裝置內容中可以有色彩或選取的單色點陣圖，所傳回的點陣圖格式`CreateCompatibleBitmap`函式不一定相同; 不過，nonmemory 裝置內容的相容點陣圖的格式一律會處於裝置的格式。

當您完成使用`CBitmap`物件以建立`CreateCompatibleBitmap`函式，請先選取點陣圖並移出裝置內容，然後刪除`CBitmap`物件。

##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap

初始化與所識別的裝置內容相容的可捨棄點陣圖*pDC*。

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
指定點陣圖的寬度 （以位元為單位）。

*nHeight*<br/>
指定點陣圖的高度 （以位元為單位）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖有相同數目的色彩平面或相同的每個像素的位元格式，為指定的裝置內容。 應用程式可以選取此點陣圖，作為適用於所指定的記憶體裝置的目前點陣圖*pDC*。

Windows 可以捨棄應用程式尚未選取成顯示內容時，才，此函式所建立的點陣圖。 如果未選取，並加以選取，嘗試更新版本的應用程式時，Windows 會捨棄點陣圖[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)函式會傳回 NULL。

當您完成使用`CBitmap`物件以建立`CreateDiscardableBitmap`函式，請先選取點陣圖並移出裝置內容，然後刪除`CBitmap`物件。

##  <a name="fromhandle"></a>  CBitmap::FromHandle

將指標傳回至`CBitmap`物件給 Windows GDI 點陣圖控制代碼時。

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
指定 Windows GDI 點陣圖。

### <a name="return-value"></a>傳回值

指標`CBitmap`如果成功，否則為 NULL 的物件。

### <a name="remarks"></a>備註

如果`CBitmap`物件尚未附加至控制代碼，暫存`CBitmap`建立物件並將其連結。 此暫存`CBitmap`物件是否有效，直到下一次應用程式在其事件迴圈中有閒置的時間，在那所有暫存的圖形物件，會刪除只。 另一種說法是，此暫存物件的一個視窗訊息處理期間才有效。

##  <a name="getbitmap"></a>  CBitmap::GetBitmap

擷取附加的點陣圖影像屬性。

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>參數

*pBitMap*<br/>
指標[點陣圖](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap)會收到的映像屬性的結構。 這個參數必須不是 NULL。

### <a name="return-value"></a>傳回值

如果方法成功，為非零否則為 0。

### <a name="remarks"></a>備註

##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits

將附加的點陣圖的位元模式複製到指定的緩衝區。

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>參數

*dwCount*<br/>
要複製到緩衝區的位元組數目。

*lpBits*<br/>
將會收到點陣圖的緩衝區指標。

### <a name="return-value"></a>傳回值

如果方法成功; 複製到緩衝區的位元組數目否則為 0。

### <a name="remarks"></a>備註

使用[CBitmap::GetBitmap](#getbitmap)來決定所需的緩衝區大小。

##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension

傳回點陣圖的高度與寬度。

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>傳回值

寬度和高度的點陣圖，以 0.1 公釐為單位。 高度處於`cy`隸屬`CSize`中的物件，而寬度是`cx`成員。 如果點陣圖的寬度和高度沒有已設定使用`SetBitmapDimension`，傳回的值為 0。

### <a name="remarks"></a>備註

高度和寬度會假設已使用先前設定[SetBitmapDimension](#setbitmapdimension)成員函式。

##  <a name="loadbitmap"></a>  Cbitmap:: Loadbitmap

載入所命名的點陣圖資源*lpszResourceName*或識別中的 ID 編號*nIDResource*從應用程式的可執行檔。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
指向以 null 結束的字串，其中包含點陣圖資源的名稱。

*nIDResource*<br/>
指定點陣圖資源的資源識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

載入的點陣圖會附加至`CBitmap`物件。

如果所識別的點陣圖*lpszResourceName*不存在或沒有記憶體不足，無法載入點陣圖，如果函式會傳回 0。

您可以使用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)函式來刪除點陣圖載入`LoadBitmap`函式，或`CBitmap`解構函式會為您刪除物件。

> [!CAUTION]
>  刪除物件之前，請確定未選取放入裝置內容中。

3.1 和更新版本的 Windows 版本已新增下列點陣圖：

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

這些點陣圖會中找不到的 Windows 版本的裝置驅動程式 3.0 版和更早版本。 點陣圖與顯示其外觀的完整清單，請參閱 Windows SDK。

##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap

呼叫此成員函式來載入點陣圖，並將對應為目前的系統色彩的色彩。

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
點陣圖旗標。 可以是零或 CMB_MASKED。

*lpColorMap*<br/>
指標`COLORMAP`結構，其中包含對應的點陣圖所需的色彩資訊。 如果此參數為 NULL，則此函數會使用預設的色彩對應。

*nMapSize*<br/>
所指向的色彩對應數目*lpColorMap*。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

根據預設，`LoadMappedBitmap`將對應常用於按鈕圖像 （glyph） 的色彩。

如需建立對應的點陣圖的資訊，請參閱 Windows 函式[CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562)並[COLORMAP](/windows/desktop/api/commctrl/ns-commctrl-_colormap) Windows SDK 中的結構。

##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap

載入 Windows 所使用的預先定義的點陣圖。

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>參數

*nIDBitmap*<br/>
預先定義的 Windows 點陣圖的 ID 編號。 下面會列出可能的值，從 WINDOWS。H:

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

點陣圖名稱開頭為 OBM_OLD 代表 3.0 之前的 Windows 版本中所使用的點陣圖。

請注意，必須包含 WINDOWS 之前定義常數 OEMRESOURCE。若要使用的任何 H **OBM_** 常數。

##  <a name="operator_hbitmap"></a>  CBitmap::operator HBITMAP

使用這個運算子來取得附加的 Windows GDI 控制代碼的`CBitmap`物件。

```
operator HBITMAP() const;
```

### <a name="return-value"></a>傳回值

如果成功，Windows GDI 物件的控制代碼所表示`CBitmap`物件; 否則為 NULL。

### <a name="remarks"></a>備註

這位操作員便轉型運算子，可支援直接使用`HBITMAP`物件。

如需使用 圖形物件的詳細資訊，請參閱 <<c0> [ 圖形物件](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits

設定所指定的位元值的位元點陣圖*lpBits*。

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>參數

*dwCount*<br/>
指定所指向的位元組數目*lpBits*。

*lpBits*<br/>
指向包含要複製到像素值的位元組陣列`CBitmap`物件。 為了要能夠正確地呈現其影像點陣圖，值應格式化為符合已建立 CBitmap 執行個體時所指定的高度、 寬度和色彩深度值。 如需詳細資訊，請參閱 < [CBitmap::CreateBitmap](#createbitmap)。

### <a name="return-value"></a>傳回值

中的點陣圖位元; 設定所使用的位元組數目0，表示函式失敗。

##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension

指派為點陣圖，以 0.1 公釐為單位的寬度和高度。

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
指定的寬度 （以 0.1 公釐為單位） 的點陣圖。

*nHeight*<br/>
指定的高度 （單位為 0.1 公釐） 的點陣圖。

### <a name="return-value"></a>傳回值

前一個點陣圖的尺寸。 高度處於`cy`成員變數`CSize`物件，且寬度為`cx`成員變數。

### <a name="remarks"></a>備註

GDI 中不會使用這些值，但若要傳回其應用程式呼叫時[GetBitmapDimension](#getbitmapdimension)成員函式。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

