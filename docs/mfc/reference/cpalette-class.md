---
title: CPalette 類別
ms.date: 11/04/2016
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
ms.openlocfilehash: 27f4f14c9e93091728e256c890dcffee26a43de4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855454"
---
# <a name="cpalette-class"></a>CPalette 類別

封裝 Windows 調色盤。

## <a name="syntax"></a>語法

```
class CPalette : public CGdiObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPalette：： CPalette](#cpalette)|使用未附加的 Windows 調色板來建立 `CPalette` 物件。 您必須先使用其中一個初始化成員函式來初始化 `CPalette` 物件，才能使用它。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPalette：： AnimatePalette](#animatepalette)|取代 `CPalette` 物件所識別之邏輯調色板中的專案。 應用程式不需要更新其工作區，因為 Windows 會立即將新專案對應到系統元件。|
|[CPalette：： CreateHalftonePalette](#createhalftonepalette)|建立裝置內容的半色調色板，並將其附加至 `CPalette` 物件。|
|[CPalette：： CreatePalette](#createpalette)|建立 Windows 調色板，並將其附加至 `CPalette` 物件。|
|[CPalette：： FromHandle](#fromhandle)|當指定 Windows 調色板物件的控制碼時，傳回 `CPalette` 物件的指標。|
|[CPalette：： GetEntryCount](#getentrycount)|抓取邏輯調色板中的調色板專案數目。|
|[CPalette：： GetNearestPaletteIndex](#getnearestpaletteindex)|傳回邏輯調色板中，最接近色彩值的專案索引。|
|[CPalette：： GetPaletteEntries](#getpaletteentries)|抓取邏輯調色板中的一系列調色板專案。|
|[CPalette：： ResizePalette](#resizepalette)|將 `CPalette` 物件所指定的邏輯調色板大小變更為指定的專案數。|
|[CPalette：： SetPaletteEntries](#setpaletteentries)|設定邏輯調色板中某個專案範圍內的 RGB 色彩值和旗標。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPalette：： operator HPALETTE](#operator_hpalette)|傳回附加至 `CPalette`的 HPALETTE。|

## <a name="remarks"></a>備註

[調色板] 提供應用程式與色彩輸出裝置（例如顯示裝置）之間的介面。 介面可讓應用程式充分利用輸出裝置的色彩功能，而不會嚴重干擾其他應用程式所顯示的色彩。 Windows 會使用應用程式的邏輯調色板（所需色彩的清單）和系統調色板（定義可用的色彩）來決定所使用的色彩。

`CPalette` 物件提供成員函式，用於操作物件所參考的調色板。 建立 `CPalette` 物件，並使用其成員函式來建立實際的色板、圖形裝置介面（GDI）物件，以及操作其專案和其他屬性。

如需使用 `CPalette`的詳細資訊，請參閱[繪圖物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="animatepalette"></a>CPalette：： AnimatePalette

取代邏輯調色板中附加至 `CPalette` 物件的專案。

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要製作動畫之調色板中的第一個專案。

*nNumEntries*<br/>
指定要製作動畫之調色板中的專案數。

*lpPaletteColors*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))結構陣列的第一個成員，以取代*nStartIndex*和*nNumEntries*所識別的調色板專案。

### <a name="remarks"></a>備註

當應用程式呼叫 `AnimatePalette`時，並不需要更新其工作區，因為 Windows 會立即將新專案對應到系統元件。

`AnimatePalette` 函式只會在附加至 `CPalette` 物件之[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)結構的對應 `palPaletteEntry` 成員中，變更已設定 PC_RESERVED 旗標的專案。 如需此結構的詳細資訊，請參閱 Windows SDK 中的 LOGPALETTE。

##  <a name="cpalette"></a>CPalette：： CPalette

建構 `CPalette` 物件。

```
CPalette();
```

### <a name="remarks"></a>備註

物件沒有附加的調色板，直到您呼叫 `CreatePalette` 以附加一個。

##  <a name="createhalftonepalette"></a>CPalette：： CreateHalftonePalette

建立裝置內容的半色調調色板。

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
識別裝置內容。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

當裝置內容的 [延展] 模式設定為 [半色調] 時，應用程式應該建立半色調色板。 接著，您應該選取[CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette)成員函式所傳回的邏輯半色調調色板，並在呼叫[CDC：： StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)或[StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits)函式之前，將其實現到裝置內容中。

如需 `CreateHalftonePalette` 和 `StretchDIBits`的詳細資訊，請參閱 Windows SDK。

##  <a name="createpalette"></a>CPalette：： CreatePalette

藉由建立 Windows 邏輯色調色板並將它附加至 `CPalette` 物件，初始化 `CPalette` 物件。

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>參數

*lpLogPalette*<br/>
指向[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)結構，其中包含邏輯調色板中色彩的相關資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如需 `LOGPALETTE` 結構的詳細資訊，請參閱 Windows SDK。

##  <a name="fromhandle"></a>CPalette：： FromHandle

當指定 Windows 調色板物件的控制碼時，傳回 `CPalette` 物件的指標。

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>參數

*hPalette*<br/>
Windows GDI 調色板的控制碼。

### <a name="return-value"></a>傳回值

如果成功，則為 `CPalette` 物件的指標;否則為 Null。

### <a name="remarks"></a>備註

如果 `CPalette` 物件尚未附加至 Windows 元件，則會建立並附加暫存 `CPalette` 物件。 只有在下次應用程式的事件迴圈中有閒置時間時，才會將這個暫存 `CPalette` 物件有效，此時所有的暫存繪圖物件都會被刪除。 換句話說，暫存物件只在處理一個視窗訊息期間有效。

##  <a name="getentrycount"></a>CPalette：： GetEntryCount

呼叫這個成員函式可抓取指定之邏輯調色板中的專案數。

```
int GetEntryCount();
```

### <a name="return-value"></a>傳回值

邏輯調色板中的專案數。

##  <a name="getnearestpaletteindex"></a>CPalette：： GetNearestPaletteIndex

傳回邏輯調色板中，最符合指定之色彩值的專案索引。

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>參數

*crColor*<br/>
指定要比對的色彩。

### <a name="return-value"></a>傳回值

邏輯調色板中專案的索引。 專案包含幾乎符合指定之色彩的色彩。

##  <a name="getpaletteentries"></a>CPalette：： GetPaletteEntries

抓取邏輯調色板中的一系列調色板專案。

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要抓取之邏輯調色板中的第一個專案。

*nNumEntries*<br/>
指定要抓取之邏輯調色板中的專案數。

*lpPaletteColors*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))資料結構的陣列，以接收調色板專案。 陣列至少必須包含*nNumEntries*所指定的多個資料結構。

### <a name="return-value"></a>傳回值

從邏輯調色板抓取的專案數;如果函數失敗，則為0。

##  <a name="operator_hpalette"></a>CPalette：： operator HPALETTE

使用這個運算子取得 `CPalette` 物件的附加 Windows GDI 控制碼。

```
operator HPALETTE() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為 `CPalette` 物件所表示之 Windows GDI 物件的控制碼;否則為 Null。

### <a name="remarks"></a>備註

這個運算子是一個轉型運算子，可支援直接使用 HPALETTE 物件。

如需使用繪圖物件的詳細資訊，請參閱 Windows SDK 中的[繪圖物件](/windows/win32/gdi/graphic-objects)一文。

##  <a name="resizepalette"></a>CPalette：： ResizePalette

將附加至 `CPalette` 物件的邏輯調色板大小變更為*nNumEntries*所指定的專案數。

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>參數

*nNumEntries*<br/>
指定在調色板中調整大小後的專案數。

### <a name="return-value"></a>傳回值

如果調色板已成功調整大小，則為非零;否則為0。

### <a name="remarks"></a>備註

如果應用程式呼叫 `ResizePalette` 以減少調色板的大小，則已調整大小之調色板中剩餘的專案會保持不變。 如果應用程式呼叫 `ResizePalette` 來放大調色板，則額外的調色板專案會設定為黑色（紅色、綠色和藍色值全都是0），而所有其他專案的旗標會設定為0。

如需 Windows API `ResizePalette`的詳細資訊，請參閱 Windows SDK 中的[ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) 。

##  <a name="setpaletteentries"></a>CPalette：： SetPaletteEntries

設定邏輯調色板中某個專案範圍內的 RGB 色彩值和旗標。

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要設定之邏輯調色板中的第一個專案。

*nNumEntries*<br/>
指定要設定之邏輯調色板中的專案數。

*lpPaletteColors*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))資料結構的陣列，以接收調色板專案。 陣列至少必須包含*nNumEntries*所指定的多個資料結構。

### <a name="return-value"></a>傳回值

邏輯調色板中設定的專案數;如果函數失敗，則為0。

### <a name="remarks"></a>備註

如果在應用程式呼叫 `SetPaletteEntries`時，將邏輯調色板選取至裝置內容，則在應用程式呼叫[CDC：： RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)之前，變更將不會生效。

如需詳細資訊，請參閱 Windows SDK 中的[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) 。

## <a name="see-also"></a>另請參閱

[MFC 範例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPalette：： GetPaletteEntries](#getpaletteentries)<br/>
[CPalette：： SetPaletteEntries](#setpaletteentries)
