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
ms.openlocfilehash: 83cd125fa7ab64aa39c606bc048022400d158e72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374767"
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
|[CPalette:CPalette](#cpalette)|構造沒有附加`CPalette`的 Windows 調色板的物件。 必須先使用初始化成員`CPalette`函數之一初始化物件,然後才能使用它。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPalette:動畫調色板](#animatepalette)|替換物件標識的邏輯調色板中的`CPalette`條目。 應用程式不必更新其工作區,因為 Windows 會立即將新條目映射到系統調色板中。|
|[CPalette::建立半色調調色板](#createhalftonepalette)|為設備上下文創建半色調調色板並將其附加到`CPalette`物件。|
|[CPalette::建立調色板](#createpalette)|創建 Windows 調色板並將其`CPalette`附加到 物件。|
|[CPalette:從手柄](#fromhandle)|當為 Windows`CPalette`調色板物件的句柄時,返回指向物件的指標。|
|[CPalette:抓取入口計數](#getentrycount)|檢索邏輯調色板中的調色板條目數。|
|[CPalette:取得最接近的調色板索引](#getnearestpaletteindex)|返回邏輯調色板中最匹配顏色值的條目的索引。|
|[CPalette:抓取調色盤](#getpaletteentries)|檢索邏輯調色板中的一系列調色板條目。|
|[CPalette:調整調色盤大小](#resizepalette)|將`CPalette`物件指定的邏輯調色板的大小更改為指定的條目數。|
|[CPalette::設定調色板](#setpaletteentries)|在邏輯調色板中的一系列條目中設置 RGB 顏色值和標誌。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPalette::操作員 HPALETTE](#operator_hpalette)|返回附加到的`CPalette`HPALETTE。|

## <a name="remarks"></a>備註

調色板提供應用程式和顏色輸出設備(如顯示設備)之間的介面。 該介面允許應用程式充分利用輸出設備的顏色功能,而不會嚴重干擾其他應用程式顯示的顏色。 Windows 使用應用程式的邏輯調色板(所需顏色的清單)和系統調色板(定義可用顏色)來確定使用的顏色。

物件`CPalette`提供用於操作物件引用的調色板的成員函數。 建構`CPalette`物件並使用其成員函數創建實際調色板、圖形設備介面 (GDI) 物件,並操作其條目和其他屬性。

有關`CPalette`使用的詳細資訊,請參考[圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cpaletteanimatepalette"></a><a name="animatepalette"></a>CPalette:動畫調色板

替換附加到`CPalette`物件的邏輯調色板中的條目。

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要進行動畫處理的調色板中的第一個條目。

*nNum項目*<br/>
指定要進行動畫處理的調色板中的條目數。

*lpPalette 顏色*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))結構陣列的第一個成員,以替換*nStartIndex*和*nNumentry*標識的調色板條目。

### <a name="remarks"></a>備註

當應用程式調用`AnimatePalette`時,它不必更新其工作區,因為 Windows 會立即將新條目映射到系統調色板中。

該`AnimatePalette`函數將僅更改附加到物件的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)結構的`CPalette`相應`palPaletteEntry`成員中設置PC_RESERVED標誌的條目。 有關此結構的詳細資訊,請參閱 Windows SDK 中的 LOGPALETTE。

## <a name="cpalettecpalette"></a><a name="cpalette"></a>CPalette:CPalette

建構 `CPalette` 物件。

```
CPalette();
```

### <a name="remarks"></a>備註

在調用`CreatePalette`附加一個調色板之前,該對象沒有附加的調色板。

## <a name="cpalettecreatehalftonepalette"></a><a name="createhalftonepalette"></a>CPalette::建立半色調調色板

為設備上下文創建半色調調色板。

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
標識設備上下文。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

當設備上下文的拉伸模式設置為 HALFTONE 時,應用程式應創建半色調調色板。 然後,在調用[CDC:::拉伸Blt](../../mfc/reference/cdc-class.md#stretchblt)或[拉伸DIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits)函數之前,應選擇[CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette)成員函數返回的邏輯半色調調色板並將其實現到設備上下文中。

有關`CreateHalftonePalette``StretchDIBits`和 的詳細資訊,請參閱 Windows SDK。

## <a name="cpalettecreatepalette"></a><a name="createpalette"></a>CPalette::建立調色板

通過創建 Windows`CPalette`邏輯調色板並將其附加到`CPalette`物件來 初始化物件。

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>參數

*lpLogPalette*<br/>
指向包含邏輯調色板中顏色資訊的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

有關結構的詳細資訊,`LOGPALETTE`請參閱 Windows SDK。

## <a name="cpalettefromhandle"></a><a name="fromhandle"></a>CPalette:從手柄

當為 Windows`CPalette`調色板物件的句柄時,返回指向物件的指標。

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>參數

*hPalette*<br/>
Windows GDI 調色板的句柄。

### <a name="return-value"></a>傳回值

指向`CPalette`物件的指標(如果成功);如果成功,則指向物件。否則 NULL。

### <a name="remarks"></a>備註

如果物件`CPalette`尚未附加到 Windows 調色板,則創建`CPalette`並附加臨時 物件。 此臨時`CPalette`物件僅在下次應用程式在其事件迴圈中有空閑時間之前有效,此時將刪除所有臨時圖形物件。 換句話說,臨時物件僅在處理一個視窗消息期間有效。

## <a name="cpalettegetentrycount"></a><a name="getentrycount"></a>CPalette:抓取入口計數

調用此成員函數以檢索給定邏輯調色板中的條目數。

```
int GetEntryCount();
```

### <a name="return-value"></a>傳回值

邏輯調色板中的條目數。

## <a name="cpalettegetnearestpaletteindex"></a><a name="getnearestpaletteindex"></a>CPalette:取得最接近的調色板索引

返回邏輯調色板中最與指定顏色值匹配的條目的索引。

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>參數

*crColor*<br/>
指定要匹配的顏色。

### <a name="return-value"></a>傳回值

邏輯調色板中條目的索引。 該項目包含最接近與指定顏色匹配的顏色。

## <a name="cpalettegetpaletteentries"></a><a name="getpaletteentries"></a>CPalette:抓取調色盤

檢索邏輯調色板中的一系列調色板條目。

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要檢索的邏輯調色板中的第一個條目。

*nNum項目*<br/>
指定要檢索的邏輯調色板中的條目數。

*lpPalette 顏色*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))資料結構陣列以接收調色板條目。 陣列必須包含至少與*nNumentries*指定的相同數量的數據結構。

### <a name="return-value"></a>傳回值

從邏輯調色板檢索的條目數;如果函數失敗,為 0。

## <a name="cpaletteoperator-hpalette"></a><a name="operator_hpalette"></a>CPalette::操作員 HPALETTE

使用此運算元獲取`CPalette`物件的附加 Windows GDI 句柄。

```
operator HPALETTE() const;
```

### <a name="return-value"></a>傳回值

如果成功,則對物件表示的 Windows`CPalette`GDI 物件的句柄;如果成功,則對物件表示的 Windows GDI 物件的句柄。否則 NULL。

### <a name="remarks"></a>備註

此運算子是強制轉換運算符,支援直接使用 HPALETTE 物件。

有關使用圖形物件的詳細資訊,請參閱 Windows SDK 中的[「圖形物件](/windows/win32/gdi/graphic-objects)」一文。

## <a name="cpaletteresizepalette"></a><a name="resizepalette"></a>CPalette:調整調色盤大小

將附加到`CPalette`物件的邏輯調色板的大小更改為*nNumentries*指定的條目數。

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>參數

*nNum項目*<br/>
指定調色板調整大小後條目數。

### <a name="return-value"></a>傳回值

如果調色板成功調整大小,則非零;否則 0。

### <a name="remarks"></a>備註

如果應用程式調用`ResizePalette`以減小調色板的大小,則調整大小的調色板中剩餘的條目將保持不變。 如果應用程式調用`ResizePalette`以放大調色板,則其他調色板項目設置為黑色(紅色、綠色和藍色值為 0),所有附加條目的標誌設置為 0。

有關 Windows`ResizePalette`API 的詳細資訊,請參閱在 Windows SDK 中[調整調色板的大小](/windows/win32/api/wingdi/nf-wingdi-resizepalette)。

## <a name="cpalettesetpaletteentries"></a><a name="setpaletteentries"></a>CPalette::設定調色板

在邏輯調色板中的一系列條目中設置 RGB 顏色值和標誌。

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>參數

*nStartIndex*<br/>
指定要設置的邏輯調色板中的第一個條目。

*nNum項目*<br/>
指定要設置的邏輯調色板中的條目數。

*lpPalette 顏色*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))資料結構陣列以接收調色板條目。 陣列必須包含至少與*nNumentries*指定的相同數量的數據結構。

### <a name="return-value"></a>傳回值

邏輯調色板中設置的條目數;如果函數失敗,為 0。

### <a name="remarks"></a>備註

如果在應用程式調用`SetPaletteEntries`時將邏輯調色板選擇到設備上下文中,則在應用程式調用[CDC:::實現調色板](../../mfc/reference/cdc-class.md#realizepalette)之前,更改不會生效。

有關詳細資訊,請參閱 Windows SDK 中的[PALETTEENTRY。](/previous-versions/dd162769\(v=vs.85\))

## <a name="see-also"></a>另請參閱

[MFC 樣品 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPalette:抓取調色盤](#getpaletteentries)<br/>
[CPalette::設定調色板](#setpaletteentries)
