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
ms.openlocfilehash: 1dc29a675f6ab3883683b3afae7e22e7ed0f1cc3
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504776"
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
|[CPalette::CPalette](#cpalette)|建構`CPalette`物件沒有附加的 Windows 調色盤。 您必須初始化`CPalette`物件與其中一個成員函式初始化才能使用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|取代項目中所識別的邏輯調色盤`CPalette`物件。 應用程式並沒有要更新其工作區中，因為 Windows 立即對應到系統調色盤的新項目。|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|建立 半色調調色盤的 裝置內容，並將它附加至`CPalette`物件。|
|[CPalette::CreatePalette](#createpalette)|建立 Windows 的色板，並將它附加至`CPalette`物件。|
|[CPalette::FromHandle](#fromhandle)|將指標傳回至`CPalette`物件控制代碼提供給 Windows 調色盤物件時。|
|[CPalette::GetEntryCount](#getentrycount)|擷取邏輯調色盤中的調色盤項目數目。|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|在最接近的色彩值的邏輯色板中傳回的項目索引。|
|[CPalette::GetPaletteEntries](#getpaletteentries)|擷取一組邏輯調色盤中的調色盤項目。|
|[CPalette::ResizePalette](#resizepalette)|變更所指定的邏輯色板的大小`CPalette`物件，以指定的項目數目。|
|[CPalette::SetPaletteEntries](#setpaletteentries)|設定邏輯調色盤中的項目範圍中的 RGB 色彩值和旗標。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPalette::operator HPALETTE](#operator_hpalette)|傳回 HPALETTE 附加至`CPalette`。|

## <a name="remarks"></a>備註

調色盤提供色彩輸出裝置 （例如顯示裝置） 和應用程式之間的介面。 介面可讓應用程式以充分利用輸出裝置的色彩功能而不會嚴重妨礙其他應用程式所顯示的色彩。 Windows 會使用應用程式的邏輯調色盤 （所需的色彩的清單） 和系統調色盤 （會定義可用的色彩），以判斷所使用的色彩。

A`CPalette`物件提供成員函式物件所操作的調色盤參考。 建構`CPalette`物件，並使用其成員函式，來建立實際的調色盤，圖形裝置介面 (GDI) 物件，並操作其項目和其他屬性。

如需有關使用`CPalette`，請參閱 <<c2> [ 圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="animatepalette"></a>  CPalette::AnimatePalette

取代附加至邏輯調色盤中的項目`CPalette`物件。

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要建立動畫的調色盤中的第一個項目。

*nNumEntries*<br/>
要建立動畫的調色盤中指定的項目數。

*lpPaletteColors*<br/>
指向陣列的第一個成員[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))結構，以取代所識別的調色盤項目*nStartIndex*並*nNumEntries*。

### <a name="remarks"></a>備註

當應用程式呼叫`AnimatePalette`，它並沒有要更新其工作區中，因為 Windows 立即對應到系統調色盤的新項目。

`AnimatePalette`函式只會變更 PC_RESERVED 旗標設定在對應的項目`palPaletteEntry`隸屬[LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette)結構附加至`CPalette`物件。 LOGPALETTE Windows SDK 中針對此結構的詳細資訊，請參閱。

##  <a name="cpalette"></a>  CPalette::CPalette

建構 `CPalette` 物件。

```
CPalette();
```

### <a name="remarks"></a>備註

物件會有任何附加的調色盤，直到您呼叫`CreatePalette`將其中一個。

##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette

建立裝置內容半色調調色盤。

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
識別裝置內容。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

當裝置內容的縮放模式設為 半色調，應用程式應該建立半色調調色盤。 傳回邏輯半色調調色盤[CreateHalftonePalette](/windows/desktop/api/wingdi/nf-wingdi-createhalftonepalette)成員函式應該再選取和裝置內容，然後才到實現[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)或[Stretchdibits 做](/windows/desktop/api/wingdi/nf-wingdi-stretchdibits)呼叫函式。

請參閱 Windows SDK，如需詳細資訊，關於`CreateHalftonePalette`和`StretchDIBits`。

##  <a name="createpalette"></a>  CPalette::CreatePalette

初始化`CPalette`藉由建立 Windows 邏輯色板，並附加到物件`CPalette`物件。

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>參數

*lpLogPalette*<br/>
指向[LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette)結構，其中包含邏輯調色盤色彩的相關資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

請參閱 Windows SDK，如需詳細資訊，關於`LOGPALETTE`結構。

##  <a name="fromhandle"></a>  CPalette::FromHandle

將指標傳回至`CPalette`物件控制代碼提供給 Windows 調色盤物件時。

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>參數

*hPalette*<br/>
Windows GDI 調色盤控制代碼。

### <a name="return-value"></a>傳回值

指標`CPalette`如果成功，否則為 NULL 的物件。

### <a name="remarks"></a>備註

如果`CPalette`物件尚未附加至 Windows 調色盤，暫存`CPalette`建立物件並將其連結。 此暫存`CPalette`物件是否有效，直到下一次應用程式在其事件迴圈中有閒置的時間，在那所有暫存的圖形物件，會刪除只。 換句話說，暫存物件只在一個視窗訊息的處理期間有效。

##  <a name="getentrycount"></a>  CPalette::GetEntryCount

呼叫此成員函式，來擷取指定的邏輯調色盤中的項目數。

```
int GetEntryCount();
```

### <a name="return-value"></a>傳回值

在邏輯調色盤中的項目數。

##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex

在最接近指定的色彩值的邏輯色板中傳回的項目索引。

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>參數

*crColor*<br/>
指定要比對的色彩。

### <a name="return-value"></a>傳回值

邏輯調色盤中的項目索引。 項目會包含最幾乎符合指定的色彩的色彩。

##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries

擷取一組邏輯調色盤中的調色盤項目。

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要擷取邏輯調色盤中的第一個項目。

*nNumEntries*<br/>
要擷取邏輯調色盤中指定的項目數。

*lpPaletteColors*<br/>
指向陣列[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))資料結構，以接收調色盤項目。 陣列必須包含數至少與所指定的資料結構*nNumEntries*。

### <a name="return-value"></a>傳回值

擷取邏輯色板; 中的項目數目0，表示失敗的函式。

##  <a name="operator_hpalette"></a>  CPalette::operator HPALETTE

使用這個運算子來取得附加的 Windows GDI 控制代碼的`CPalette`物件。

```
operator HPALETTE() const;
```

### <a name="return-value"></a>傳回值

如果成功，Windows GDI 物件的控制代碼所表示`CPalette`物件; 否則為 NULL。

### <a name="remarks"></a>備註

這位操作員便轉型運算子，可支援直接使用 HPALETTE 物件。

如需有關如何使用 圖形物件的詳細資訊，請參閱[圖形物件](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

##  <a name="resizepalette"></a>  CPalette::ResizePalette

變更附加至邏輯色板的大小`CPalette`物件所指定項目數*nNumEntries*。

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>參數

*nNumEntries*<br/>
已調整大小之後，請在調色盤中指定的項目數。

### <a name="return-value"></a>傳回值

非零值，如果已成功調整調色盤;否則為 0。

### <a name="remarks"></a>備註

如果應用程式呼叫`ResizePalette`以減少大小的調色盤，剩餘的已調整大小的調色盤中的項目不會變更。 如果應用程式呼叫`ResizePalette`放大調色盤，其他的調色盤項目設為黑色 （紅色、 綠色和藍色值均為 0），以及所有其他項目的旗標會設為 0。

如需有關 Windows API `ResizePalette`，請參閱 < [ResizePalette](/windows/desktop/api/wingdi/nf-wingdi-resizepalette) Windows SDK 中。

##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries

設定邏輯調色盤中的項目範圍中的 RGB 色彩值和旗標。

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要設定的邏輯調色盤中的第一個項目。

*nNumEntries*<br/>
若要設定邏輯調色盤中指定的項目數。

*lpPaletteColors*<br/>
指向陣列[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))資料結構，以接收調色盤項目。 陣列必須包含數至少與所指定的資料結構*nNumEntries*。

### <a name="return-value"></a>傳回值

設定邏輯調色盤; 中的項目數目0，表示失敗的函式。

### <a name="remarks"></a>備註

當應用程式呼叫時，如果要邏輯的調色盤選取放入裝置內容`SetPaletteEntries`，變更將不會生效，直到應用程式會呼叫[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)。

如需詳細資訊，請參閱 < [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[MFC 範例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
