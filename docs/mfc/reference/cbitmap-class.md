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
ms.openlocfilehash: adb2a461de5e82fa76ce0ed9961d970f46dbe26a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834982"
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
|[CBitmap：： CreateBitmapIndirect](#createbitmapindirect)|使用具有寬度、高度和位模式的點陣圖，初始化物件 (如果在結構中指定) 指定的話 `BITMAP` 。|
|[CBitmap：： CreateCompatibleBitmap](#createcompatiblebitmap)|使用點陣圖初始化物件，使其與指定的裝置相容。|
|[CBitmap：： CreateDiscardableBitmap](#creatediscardablebitmap)|使用與指定裝置相容的 discardable 點陣圖，初始化物件。|
|[CBitmap：： FromHandle](#fromhandle)|`CBitmap`當提供 Windows 點陣圖的控制碼時，傳回物件的指標 `HBITMAP` 。|
|[CBitmap：： GetBitmap](#getbitmap)|`BITMAP`以點陣圖的相關資訊填入結構。|
|[CBitmap：： GetBitmapBits](#getbitmapbits)|將指定點陣圖的位複製到指定的緩衝區。|
|[CBitmap：： GetBitmapDimension](#getbitmapdimension)|傳回點陣圖的寬度和高度。 [SetBitmapDimension](#setbitmapdimension)成員函式先前已設定高度和寬度。|
|[CBitmap：： LoadBitmap](#loadbitmap)|從應用程式的可執行檔載入命名點陣圖資源，並將點陣圖附加至物件，以初始化物件。|
|[CBitmap：： LoadMappedBitmap](#loadmappedbitmap)|載入點陣圖，並將色彩對應到目前的系統色彩。|
|[CBitmap：： LoadOEMBitmap](#loadoembitmap)|載入預先定義的 Windows 點陣圖，並將點陣圖附加至物件，以初始化物件。|
|[CBitmap：： SetBitmapBits](#setbitmapbits)|將點陣圖的位設定為指定的位值。|
|[CBitmap：： SetBitmapDimension](#setbitmapdimension)|以 0.1-毫米單位將寬度和高度指派給點陣圖。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CBitmap：： operator HBITMAP](#operator_hbitmap)|傳回附加至物件的 Windows 控制碼 `CBitmap` 。|

## <a name="remarks"></a>備註

若要使用 `CBitmap` 物件，請建立物件，並使用其中一個初始化成員函式來附加點陣圖控制碼，然後呼叫物件的成員函式。

如需使用繪圖物件（例如）的詳細資訊 `CBitmap` ，請參閱 [繪圖物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a> CBitmap：： CBitmap

建構 `CBitmap` 物件。

```
CBitmap();
```

### <a name="remarks"></a>備註

產生的物件必須使用其中一個初始化成員函式來初始化。

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a> CBitmap：： CreateBitmap

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

如果是色彩點陣圖，則應該將 *nPlanes* 或 *nBitcount* 參數設定為1。 如果這兩個參數都設為 1， `CreateBitmap` 會建立單色點陣圖。

雖然您無法直接選取用於顯示裝置的點陣圖，但可以使用 [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) 選取一個點陣圖作為「記憶體裝置內容」的目前點陣圖，再使用 [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) 函式將該點陣圖複製到任何相容裝置內容。

當您完成使用 `CBitmap` 函式所建立的 `CreateBitmap` 物件時，請先選取點陣圖並移出裝置內容，再刪除 `CBitmap` 物件。

如需詳細資訊，請參閱 `bmBits` 結構中欄位的描述 `BITMAP` 。 [CBitmap::CreateBitmapIndirect](/windows/win32/api/wingdi/ns-wingdi-bitmap) 成員函式下提供 [BITMAP](#createbitmapindirect) 結構的說明。

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a> CBitmap：： CreateBitmapIndirect

在 *lpBitmap*所指向的結構中指定) ，初始化具有寬度、高度和位模式 (的點陣圖。

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>參數

*lpBitmap*<br/>
指向包含點陣圖相關資訊的 [點陣圖](/windows/win32/api/wingdi/ns-wingdi-bitmap) 結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

雖然無法直接選取顯示裝置的點陣圖，但可以使用 [cdc：： SelectObject](../../mfc/reference/cdc-class.md#selectobject) 將其選取為記憶體裝置內容的目前點陣圖，並使用 [Cdc：： BitBlt](../../mfc/reference/cdc-class.md#bitblt) 或 [cdc：： StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) 函式複製到任何相容的裝置內容。  ([CDC：:P atblt](../../mfc/reference/cdc-class.md#patblt) 函數可以將目前筆刷的點陣圖直接複製到顯示裝置內容。 ) 

如果使用函式 `BITMAP` 填入 *lpBitmap* 參數所指向的結構 `GetObject` ，則不會指定點陣圖的位，也不會初始化點陣圖。 若要初始化點陣圖，應用程式可以使用 [CDC：： BitBlt](../../mfc/reference/cdc-class.md#bitblt) 或 [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) 這類函數，將的第一個參數所識別的點陣圖中的位複製 `CGdiObject::GetObject` 到所建立的點陣圖 `CreateBitmapIndirect` 。

當您使用函式 `CBitmap` 建立的物件完成時 `CreateBitmapIndirect` ，請先從裝置內容中選取點陣圖，然後刪除 `CBitmap` 物件。

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a> CBitmap：： CreateCompatibleBitmap

初始化與 *pDC*指定的裝置相容的點陣圖。

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
指定裝置內容。

*nWidth*<br/>
指定點陣圖的寬度 (以像素為單位)。

*nHeight*<br/>
指定點陣圖的高度 (以像素為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖具有相同數目的色彩平面或與指定裝置內容相同的每一像素位元數。 您可以將它選取為與 *pDC*所指定之任何記憶體裝置相容的目前點陣圖。

如果 *pDC* 是記憶體裝置內容，傳回的點陣圖會與該裝置內容中目前選取的點陣圖具有相同的格式。 「記憶體裝置內容」是一種記憶體區塊，代表顯示介面。 在將影像複製到相容裝置的實際顯示介面之前，它可以用來準備記憶體中的影像。

建立記憶體裝置內容時，GDI 會自動為其選取單色股票點陣圖。

由於彩色記憶體裝置內容可以選取色彩或單色點陣圖，因此函式所傳回的點陣圖格式 `CreateCompatibleBitmap` 不一定相同; 不過，nonmemory 裝置內容的相容點陣圖格式一律會採用裝置的格式。

當您使用函式 `CBitmap` 建立的物件完成時 `CreateCompatibleBitmap` ，請先從裝置內容中選取點陣圖，然後刪除 `CBitmap` 物件。

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a> CBitmap：： CreateDiscardableBitmap

初始化與 *pDC*識別的裝置內容相容的 discardable 點陣圖。

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
指定裝置內容。

*nWidth*<br/>
指定點陣圖的 (寬度，以位) 。

*nHeight*<br/>
指定點陣圖的位) 高度 (。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖具有相同數目的色彩平面或與指定裝置內容相同的每一像素位元數。 應用程式可以選取此點陣圖做為與 *pDC*所指定之記憶體裝置相容的目前點陣圖。

只有當應用程式未將其選取為顯示內容時，Windows 才能捨棄此函式所建立的點陣圖。 如果 Windows 在未選取時捨棄點陣圖，而應用程式稍後嘗試選取它， [CDC：： SelectObject](../../mfc/reference/cdc-class.md#selectobject) 函數將會傳回 Null。

當您使用函式 `CBitmap` 建立的物件完成時 `CreateDiscardableBitmap` ，請先從裝置內容中選取點陣圖，然後刪除 `CBitmap` 物件。

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a> CBitmap：： FromHandle

`CBitmap`當提供 WINDOWS GDI 點陣圖的控制碼時，傳回物件的指標。

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
指定 Windows GDI 點陣圖。

### <a name="return-value"></a>傳回值

`CBitmap`如果成功，則為物件的指標; 否則為 Null。

### <a name="remarks"></a>備註

如果 `CBitmap` 物件尚未附加至控制碼， `CBitmap` 就會建立並附加暫存物件。 這個暫存 `CBitmap` 物件只有在下一次應用程式的事件迴圈中有閒置時間時才有效，此時會刪除所有的臨時繪圖物件。 另一種說法是，暫存物件只有在處理一個視窗訊息時才有效。

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a> CBitmap：： GetBitmap

抓取附加點陣圖的影像屬性。

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>參數

*pBitMap*<br/>
將接收影像屬性之 [點陣圖](/windows/win32/api/wingdi/ns-wingdi-bitmap) 結構的指標。 此參數不得為 Null。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零;否則為0。

### <a name="remarks"></a>備註

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a> CBitmap：： GetBitmapBits

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

使用 [CBitmap：： GetBitmap](#getbitmap) 來判斷所需的緩衝區大小。

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a> CBitmap：： GetBitmapDimension

傳回點陣圖的寬度和高度。

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>傳回值

點陣圖的寬度和高度，以 0.1-毫米單位表示。 高度位於 `cy` 物件的成員中 `CSize` ，而寬度則位於 `cx` 成員中。 如果未使用設定點陣圖寬度和高度 `SetBitmapDimension` ，則傳回值為0。

### <a name="remarks"></a>備註

先前使用 [SetBitmapDimension](#setbitmapdimension) 成員函式設定了高度和寬度。

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a> CBitmap：： LoadBitmap

載入以 *lpszResourceName* 命名的點陣圖資源，或由應用程式可執行檔的 *NIDRESOURCE* 中的識別碼編號識別。

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

如果 *lpszResourceName* 所識別的點陣圖不存在，或者沒有足夠的記憶體可載入點陣圖，則函式會傳回0。

您可以使用 [CGdiObject：:D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) 函數來刪除函式載入的點陣圖 `LoadBitmap` ，否則，此 `CBitmap` 函式會為您刪除物件。

> [!CAUTION]
> 刪除物件之前，請確定未選取該物件到裝置內容中。

下列點陣圖已新增至 Windows 3.1 版和更新版本：

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

在 Windows 3.0 版及更早版本的設備磁碟機中找不到這些點陣圖。 如需點陣圖的完整清單以及其外觀的顯示，請參閱 Windows SDK。

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a> CBitmap：： LoadMappedBitmap

呼叫此成員函式以載入點陣圖，並將色彩對應到目前的系統色彩。

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
`COLORMAP`結構的指標，其中包含對應點陣圖所需的色彩資訊。 如果此參數為 Null，則函式會使用預設的色彩對應。

*nMapSize*<br/>
*LpColorMap*所指向的色彩對應數目。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

依預設， `LoadMappedBitmap` 會對應按鈕圖像中常用的色彩。

如需建立對應點陣圖的詳細資訊，請參閱 Windows SDK 中的 Windows 函式 [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) 和 [COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap) 結構。

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a> CBitmap：： LoadOEMBitmap

載入 Windows 所使用的預先定義點陣圖。

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>參數

*nIDBitmap*<br/>
預先定義之 Windows 點陣圖的識別碼。 以下是 WINDOWS 所列的可能值。H：

:::row:::
   :::column span="":::
      OBM_BTNCORNERS \
      OBM_BTSIZE \
      OBM_CHECK \
      OBM_CHECKBOXES \
      OBM_CLOSE \
      OBM_COMBO \
      OBM_DNARROW \
      OBM_DNARROWD \
      OBM_DNARROWI \
      OBM_LFARROW \
      OBM_LFARROWD \
      OBM_LFARROWI
   :::column-end:::
   :::column span="":::
      OBM_MNARROW \
      OBM_OLD_CLOSE \
      OBM_OLD_DNARROW \
      OBM_OLD_LFARROW \
      OBM_OLD_REDUCE \
      OBM_OLD_RESTORE \
      OBM_OLD_RGARROW \
      OBM_OLD_UPARROW \
      OBM_OLD_ZOOM \
      OBM_REDUCE \
      OBM_REDUCED
   :::column-end:::
   :::column span="":::
      OBM_RESTORE \
      OBM_RESTORED \
      OBM_RGARROW \
      OBM_RGARROWD \
      OBM_RGARROWI \
      OBM_SIZE \
      OBM_UPARROW \
      OBM_UPARROW \
      OBM_UPARROWD \
      OBM_ZOOM \
      OBM_ZOOMD
   :::column-end:::
:::row-end:::

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

以 OBM_OLD 開頭的點陣圖名稱代表3.0 之前的 Windows 版本所使用的點陣圖。

請注意，必須先定義常數 OEMRESOURCE，然後再包含 WINDOWS。H，以便使用任何 **OBM_** 常數。

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a> CBitmap：： operator HBITMAP

使用這個運算子來取得附加的物件 Windows GDI 控制碼 `CBitmap` 。

```
operator HBITMAP() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為物件所代表之 Windows GDI 物件的控制碼 `CBitmap` ; 否則為 Null。

### <a name="remarks"></a>備註

這個運算子是轉換運算子，可支援直接使用 `HBITMAP` 物件。

如需使用繪圖物件的詳細資訊，請參閱 Windows SDK 中的 [繪圖物件](/windows/win32/gdi/graphic-objects) 。

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a> CBitmap：： SetBitmapBits

將點陣圖的位設定為 *lpBits*所指定的位值。

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>參數

*dwCount*<br/>
指定 *lpBits*所指向的位元組數目。

*lpBits*<br/>
指向位元組陣列，其中包含要複製到物件的圖元值 `CBitmap` 。 為了讓點陣圖能夠正確地轉譯其影像，應該將值格式化，以符合建立 CBitmap 實例時所指定的高度、寬度和色彩深度值。 如需詳細資訊，請參閱 [CBitmap：： CreateBitmap](#createbitmap)。

### <a name="return-value"></a>傳回值

用來設定點陣圖位的位元組數目;如果函式失敗，則為0。

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a> CBitmap：： SetBitmapDimension

以 0.1-毫米單位將寬度和高度指派給點陣圖。

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
以 0.1-毫米單位) 指定點陣圖 (的寬度。

*nHeight*<br/>
以 0.1-毫米單位) 指定點陣圖 (的高度。

### <a name="return-value"></a>傳回值

上一個點陣圖維度。 高度位於物件的 `cy` 成員變數中 `CSize` ，而寬度則位於 `cx` 成員變數中。

### <a name="remarks"></a>備註

除非應用程式呼叫 [GetBitmapDimension](#getbitmapdimension) 成員函式，否則 GDI 不會使用這些值。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
