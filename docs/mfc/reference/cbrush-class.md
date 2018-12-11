---
title: CBrush 類別
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: dbc5e36fdf613f1db2818ac6193709829e3bd001
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178703"
---
# <a name="cbrush-class"></a>CBrush 類別

封裝 Windows 繪圖裝置介面 (GDI) 筆刷。

## <a name="syntax"></a>語法

```
class CBrush : public CGdiObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|建構 `CBrush` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|初始化使用樣式、 色彩和模式中指定的筆刷[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)結構。|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|使用筆刷，初始化與裝置獨立點陣圖 (DIB) 所指定的模式。|
|[CBrush::CreateHatchBrush](#createhatchbrush)|初始化使用指定的影線的圖樣和色彩的筆刷。|
|[CBrush::CreatePatternBrush](#createpatternbrush)|使用筆刷，初始化指定點陣圖的模式。|
|[CBrush::CreateSolidBrush](#createsolidbrush)|初始化具有指定的單色筆刷。|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|會建立為預設系統色彩的筆刷。|
|[CBrush::FromHandle](#fromhandle)|將指標傳回至`CBrush`物件時控制代碼給 Windows`HBRUSH`物件。|
|[CBrush::GetLogBrush](#getlogbrush)|取得[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)結構。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CBrush::operator HBRUSH](#operator_hbrush)|傳回附加至的 Windows 控制代碼`CBrush`物件。|

## <a name="remarks"></a>備註

若要使用`CBrush`物件，建構`CBrush`物件，並將它傳遞給任何`CDC`需要筆刷的成員函式。

影線，或以月份為模式，可以是純色，筆刷。

如需詳細資訊`CBrush`，請參閱 <<c2> [ 圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cbrush"></a>  CBrush::CBrush

建構 `CBrush` 物件。

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>參數

*crColor*<br/>
指定的 RGB 色彩的筆刷的前景色彩。 如果影線筆刷，這個參數會指定影線色彩。

*nIndex*<br/>
指定的筆刷的影線樣式。 它可以是下列值之一：

- 45 度 HS_BDIAGONAL 向下串聯 （由左到右）

- HS_CROSS 水平及垂直有斜紋

- HS_DIAGCROSS Crosshatch 45 度

- 向上 HS_FDIAGONAL 規劃 （由左到右） 45 度

- HS_HORIZONTAL 水平影線

- HS_VERTICAL 垂直影線

*pBitmap*<br/>
指向`CBitmap`物件，指定與筆刷會繪製的點陣圖。

### <a name="remarks"></a>備註

`CBrush` 有四個多載的建構函式。不使用引數的建構函式會建構未初始化`CBrush`必須先初始化才能使用它的物件。

如果您使用建構函式沒有引數時，您必須初始化產生`CBrush`物件[createsolidbrush 以](#createsolidbrush)， [CreateHatchBrush](#createhatchbrush)， [CreateBrushIndirect](#createbrushindirect)， [CreatePatternBrush](#createpatternbrush)，或[CreateDIBPatternBrush](#createdibpatternbrush)。 如果您使用其中一個引數的建構函式，則沒有進一步初始化不需要。 如果發生錯誤，而不使用引數的建構函式一定會成功，則引數的建構函式會擲回例外狀況。

使用單一建構函式[COLORREF](/windows/desktop/gdi/colorref)參數建構具有指定的色彩的實心筆刷。 色彩指定 RGB 值，而且可以 RGB 巨集，在 WINDOWS 中建構。H.

具有兩個參數的建構函式會建構規劃筆刷。 *NIndex*參數指定的索引影線圖樣。 *CrColor*參數指定的色彩。

具有建構函式`CBitmap`參數建構圖樣筆刷。 參數會識別點陣圖。 假設都由使用點陣圖[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)。 點陣圖，以填滿模式中使用的最小大小是 8 x 8 像素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect

初始化使用樣式、 色彩和模式中指定的筆刷[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)結構。

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>參數

*lpLogBrush*<br/>
指向[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)包含筆刷的相關資訊的結構。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

筆刷接著可以選取作為目前的筆刷，為任何裝置內容。

使用 1 個平面 （每像素 1 位元） 的單色點陣圖建立筆刷會使用目前的文字和背景色彩繪製。 由位元設為 0 的像素為單位將會以目前的文字色彩繪製。 由位元設為 1 的像素為單位將會以目前的背景色彩繪製。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush

使用筆刷，初始化指定與裝置獨立點陣圖 (DIB) 的模式。

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>參數

*hPackedDIB*<br/>
識別包含封裝的裝置獨立點陣圖 (DIB) 的全域記憶體物件。

*nUsage*<br/>
指定是否`bmiColors[]`的欄位[BITMAPINFO](/windows/desktop/api/wingdi/ns-wingdi-tagbitmapinfo)資料結構 （的 「 封裝 DIB 」 的一部分） 包含明確的 RGB 值或索引的目前具現化的邏輯調色盤。 參數必須是下列值之一：

- DIB_PAL_COLORS color 資料表所組成的 16 位元索引陣列。

- DIB_RGB_COLORS 色彩表包含常值的 RGB 值。

*lpPackedDIB*<br/>
指向包含壓縮 DIB`BITMAPINFO`後面緊跟著定義點陣圖的像素的位元組陣列的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

筆刷接著可以選取任何支援點陣作業的裝置內容。

在處理 DIB 的方式，不同的兩個版本：

- 在第一個版本中，若要取得的控制代碼 DIB 您呼叫 Windows`GlobalAlloc`函式來配置全域記憶體區塊，並接著填入封裝 DIB 中的記憶體。

- 在第二個版本中，不需要呼叫`GlobalAlloc`壓縮 DIB 配置記憶體。

包含封裝的 DIB`BITMAPINFO`後面緊跟著定義點陣圖的像素的位元組陣列的資料結構。 點陣圖做為填滿模式應該是 8 x 8 像素。 如果點陣圖是較大，Windows 就會建立使用對應的前 8 的資料列和像素點陣圖左上角的 8 個資料行的位元的填滿模式。

當應用程式放入單色裝置內容中，選取兩個色彩 DIB 圖樣筆刷時，Windows 就會忽略 DIB 內指定的色彩，並改為顯示 使用目前的文字和背景色彩的裝置內容的圖樣筆刷。 使用的文字色彩顯示對應到 DIB （位於 DIB 色彩表中的位移 0） 的第一個色彩的像素為單位。 使用背景色彩來顯示對應到 （位移 1，色彩表中） 的第二個色彩的像素為單位。

如需使用下列 Windows 功能的資訊，請參閱 Windows SDK:

- [CreateDIBPatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrush) (此函式只為了針對 3.0 之前的 Windows 版本所撰寫的應用程式相容性; 使用`CreateDIBPatternBrushPt`函式。)

- [CreateDIBPatternBrushPt](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrushpt) （以 Win32 為基礎的應用程式應該使用此函式）。

- [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush

初始化使用指定的影線的圖樣和色彩的筆刷。

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定的筆刷的影線樣式。 它可以是下列值之一：

- 45 度 HS_BDIAGONAL 向下串聯 （由左到右）

- HS_CROSS 水平及垂直有斜紋

- HS_DIAGCROSS Crosshatch 45 度

- 向上 HS_FDIAGONAL 規劃 （由左到右） 45 度

- HS_HORIZONTAL 水平影線

- HS_VERTICAL 垂直影線

*crColor*<br/>
指定前景色彩的筆刷為 RGB 色彩 （影線色彩）。 請參閱[COLORREF](/windows/desktop/gdi/colorref) Windows sdk for 的詳細資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

筆刷接著可以選取作為目前的筆刷，為任何裝置內容。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush

使用筆刷，初始化指定點陣圖的模式。

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>參數

*pBitmap*<br/>
識別點陣圖。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

筆刷接著可以選取任何支援點陣作業的裝置內容。 所識別的點陣圖*pBitmap*通常會使用初始化[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函式。

點陣圖做為填滿模式應該是 8 x 8 像素。 如果點陣圖是較大，則 Windows 只會使用對應前 8 個資料列和資料行的點陣圖左上角的像素的位元。

可以刪除圖樣筆刷，而不會影響相關聯的點陣圖。 這表示點陣圖可用來建立任意數目的圖樣筆刷。

使用目前的文字和背景色彩繪製使用單色點陣圖 （1 色彩平面，每像素 1 位元） 建立筆刷。 以目前的文字色彩繪製像素為單位，由位元設為 0。 以目前的背景色彩繪製像素為單位，由位元設為 1。

如需有關使用資訊[CreatePatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createpatternbrush)，Windows 函式中，請參閱 Windows SDK。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush

初始化具有指定的單色筆刷。

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>參數

*crColor*<br/>
A [COLORREF](/windows/desktop/gdi/colorref)結構，指定的筆刷色彩。 色彩指定 RGB 值，而且可以 RGB 巨集，在 WINDOWS 中建構。H.

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

筆刷接著可以選取作為目前的筆刷，為任何裝置內容。

當應用程式已完成使用所建立的筆刷`CreateSolidBrush`，它應該選取從裝置內容的筆刷。

### <a name="example"></a>範例

  範例，請參閱[CBrush::CBrush](#cbrush)。

##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush

初始化筆刷色彩。

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定的色彩索引。 這個值會對應到用來繪製的其中一個 21 視窗元素的色彩。 請參閱[GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor)值清單的 Windows SDK 中。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

筆刷接著可以選取作為目前的筆刷，為任何裝置內容。

當應用程式已完成使用所建立的筆刷`CreateSysColorBrush`，它應該選取從裝置內容的筆刷。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>  CBrush::FromHandle

將指標傳回至`CBrush`物件給 Windows 控制代碼時[HBRUSH](#operator_hbrush)物件。

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>參數

*hBrush*<br/>
Windows GDI 筆刷的控制代碼。

### <a name="return-value"></a>傳回值

指標`CBrush`如果成功，否則為 NULL 的物件。

### <a name="remarks"></a>備註

如果`CBrush`物件尚未附加至控制代碼，暫存`CBrush`建立物件並將其連結。 此暫存`CBrush`物件是否有效，只會保存在應用程式必須在其事件迴圈中的閒置時間的下一次。 在此期間，會刪除所有暫存的圖形物件。 換句話說，暫存物件只在一個視窗訊息的處理期間有效。

如需使用 圖形物件的詳細資訊，請參閱 <<c0> [ 圖形物件](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CBrush::CBrush](#cbrush)。

##  <a name="getlogbrush"></a>  CBrush::GetLogBrush

呼叫此成員函式，以取得`LOGBRUSH`結構。

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>參數

*pLogBrush*<br/>
指向[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)包含筆刷的相關資訊的結構。

### <a name="return-value"></a>傳回值

如果此函數成功，並*pLogBrush*是有效的指標，傳回的值是儲存至緩衝區的位元組數目。

如果函式成功，並*pLogBrush*是 NULL，則傳回值是保留資訊的函式所需的位元組數目會儲存到緩衝區。

如果函式失敗，傳回的值為 0。

### <a name="remarks"></a>備註

`LOGBRUSH`結構會定義樣式、 色彩和筆刷的模式。

例如，呼叫`GetLogBrush`以符合特定的色彩或圖樣的點陣圖。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>  CBrush::operator HBRUSH

使用這個運算子來取得附加的 Windows GDI 控制代碼的`CBrush`物件。

```
operator HBRUSH() const;
```

### <a name="return-value"></a>傳回值

如果成功，Windows GDI 物件的控制代碼所表示`CBrush`物件; 否則為 NULL。

### <a name="remarks"></a>備註

這位操作員便轉型運算子，可支援直接使用 HBRUSH 物件。

如需使用 圖形物件的詳細資訊，請參閱 <<c0> [ 圖形物件](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 PROPDLG](../../visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 類別](../../mfc/reference/cbitmap-class.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)
