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
ms.openlocfilehash: a99d8c8022d23f627320b66c3f376be803c9c839
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876044"
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
|[CBrush：： CBrush](#cbrush)|建構 `CBrush` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBrush：： CreateBrushIndirect](#createbrushindirect)|使用[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構中指定的樣式、色彩和模式，初始化筆刷。|
|[CBrush：： CreateDIBPatternBrush](#createdibpatternbrush)|使用與裝置無關的點陣圖（DIB）所指定的模式，初始化筆刷。|
|[CBrush：： CreateHatchBrush](#createhatchbrush)|使用指定的影線圖樣和色彩，初始化筆刷。|
|[CBrush：： CreatePatternBrush](#createpatternbrush)|使用點陣圖所指定的模式，初始化筆刷。|
|[CBrush：： CreateSolidBrush](#createsolidbrush)|使用指定的純色，初始化筆刷。|
|[CBrush：： CreateSysColorBrush](#createsyscolorbrush)|建立預設系統色彩的筆刷。|
|[CBrush：： FromHandle](#fromhandle)|當給定 Windows `HBRUSH` 物件的控制碼時，傳回 `CBrush` 物件的指標。|
|[CBrush：： GetLogBrush](#getlogbrush)|取得[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CBrush：： operator HBRUSH](#operator_hbrush)|傳回附加至 `CBrush` 物件的 Windows 控制碼。|

## <a name="remarks"></a>備註

若要使用 `CBrush` 物件，請建立 `CBrush` 物件，並將它傳遞至任何需要筆刷的 `CDC` 成員函式。

筆刷可以是實線、影線或圖案。

如需 `CBrush`的詳細資訊，請參閱[繪圖物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cbrush"></a>CBrush：： CBrush

建構 `CBrush` 物件。

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>參數

*crColor*<br/>
將筆刷的前景色彩指定為 RGB 色彩。 如果筆刷是影線，此參數會指定影線的色彩。

*nIndex*<br/>
指定筆刷的影線類型。 它可以是下列任何一個值：

- HS_BDIAGONAL 向下影線（由左至右）45度

- HS_CROSS 水準和垂直交叉線

- 以45度 HS_DIAGCROSS 交叉線

- HS_FDIAGONAL 在45度的向上影線（由左到右）

- HS_HORIZONTAL 水準影線

- HS_VERTICAL 垂直影線

*pBitmap*<br/>
指向指定筆刷繪製之點陣圖的 `CBitmap` 物件。

### <a name="remarks"></a>備註

`CBrush` 有四個多載的函式。不含引數的函式會建立未初始化的 `CBrush` 物件，必須先初始化才能使用。

如果您使用不含引數的函式，則必須使用[CreateSolidBrush](#createsolidbrush)、 [CreateHatchBrush](#createhatchbrush)、 [CreateBrushIndirect](#createbrushindirect)、 [CreatePatternBrush](#createpatternbrush)或[CreateDIBPatternBrush](#createdibpatternbrush)來初始化產生的 `CBrush` 物件。 如果您使用其中一個接受引數的函式，則不需要進一步的初始化。 如果遇到錯誤，含有引數的函式可能會擲回例外狀況，而不含引數的函式一律會成功。

具有單一[COLORREF](/windows/win32/gdi/colorref)參數的函式會使用指定的色彩來建立實心筆刷。 色彩會指定 RGB 值，而且可以使用 WINDOWS 中的 RGB 宏來加以建立。H.

具有兩個參數的函式會構造影線筆刷。 *NIndex*參數會指定影線圖樣的索引。 *CrColor*參數會指定色彩。

具有 `CBitmap` 參數的處理函式會結構化已建立圖案的筆刷。 參數會識別點陣圖。 此點陣圖假設已使用[CBitmap：： CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)、 [CBitmap：： CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)、 [CBitmap：： LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)或[CBitmap：： CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)來建立。 在填滿模式中使用的點陣圖大小下限為8圖元 x 8 圖元。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>CBrush：： CreateBrushIndirect

使用在[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構中指定的樣式、色彩和模式，初始化筆刷。

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>參數

*lpLogBrush*<br/>
指向包含筆刷相關資訊的[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

然後，可以將筆刷選取為任何裝置內容的目前筆刷。

使用單色（1個平面，每圖元1位）點陣圖建立的筆刷會使用目前的文字和背景色彩繪製。 設定為0的位所代表的圖元會以目前的文字色彩繪製。 設定為1的位所代表的圖元會以目前的背景色彩繪製。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>CBrush：： CreateDIBPatternBrush

使用與裝置無關的點陣圖（DIB）所指定的模式，初始化筆刷。

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
識別全域記憶體物件，其中包含已封裝的裝置獨立點陣圖（DIB）。

*nUsage*<br/>
指定[BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo)資料結構（屬於「已封裝的 DIB」）的 `bmiColors[]` 欄位是否包含明確的 RGB 值或索引到目前已實現的邏輯調色板。 參數必須為下列其中一個值：

- DIB_PAL_COLORS 色彩表是由16位索引的陣列所組成。

- DIB_RGB_COLORS color 資料表包含文字 RGB 值。

*lpPackedDIB*<br/>
指向包含 `BITMAPINFO` 結構的已封裝 DIB，後面緊接著定義點陣圖圖元的位元組陣列。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

接著，可以針對任何支援點陣作業的裝置內容選取筆刷。

這兩個版本與您處理 DIB 的方式不同：

- 在第一個版本中，若要取得 DIB 的控制碼，您可以呼叫 Windows `GlobalAlloc` 函式來配置全域記憶體的區塊，然後使用封裝的 DIB 填滿記憶體。

- 在第二個版本中，不需要呼叫 `GlobalAlloc` 來配置封裝 DIB 的記憶體。

封裝的 DIB 包含一個 `BITMAPINFO` 的資料結構，後面緊接著定義點陣圖圖元的位元組陣列。 當做填滿模式使用的點陣圖應為8圖元 x 8 圖元。 如果點陣圖較大，Windows 只會使用對應到前8個數據列的位，以及點陣圖左上角的8個圖元資料行，來建立填滿模式。

當應用程式在單色裝置內容中選取雙色 DIB 模式筆刷時，Windows 會忽略 DIB 中指定的色彩，而改為使用裝置內容目前的文字和背景色彩來顯示圖樣筆刷。 DIB 的對應圖元（在 DIB 色彩表中的位移0）會使用文字色彩來顯示。 對應至第二個色彩的圖元（在色彩資料表中的位移1）會使用背景色彩來顯示。

如需使用下列 Windows 功能的相關資訊，請參閱 Windows SDK：

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) （這項功能只是為了與針對3.0 之前的 Windows 版本所撰寫的應用程式相容，請使用 `CreateDIBPatternBrushPt` 函式）。

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) （此函式應用於以 Win32 為基礎的應用程式）。

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>CBrush：： CreateHatchBrush

使用指定的影線圖樣和色彩，初始化筆刷。

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定筆刷的影線類型。 它可以是下列任何一個值：

- HS_BDIAGONAL 向下影線（由左至右）45度

- HS_CROSS 水準和垂直交叉線

- 以45度 HS_DIAGCROSS 交叉線

- HS_FDIAGONAL 在45度的向上影線（由左到右）

- HS_HORIZONTAL 水準影線

- HS_VERTICAL 垂直影線

*crColor*<br/>
以 RGB 色彩（影線的色彩）指定筆刷的前景色彩。 如需詳細資訊，請參閱 Windows SDK 中的[COLORREF](/windows/win32/gdi/colorref) 。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

然後，可以將筆刷選取為任何裝置內容的目前筆刷。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>CBrush：： CreatePatternBrush

使用點陣圖所指定的模式，初始化筆刷。

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>參數

*pBitmap*<br/>
識別點陣圖。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

接著，可以針對任何支援點陣作業的裝置內容選取筆刷。 *PBitmap*所識別的點陣圖通常會使用[CBitmap：： CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)、 [CBitmap：： CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)、 [CBitmap：： LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)或[CBitmap：： CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函數來初始化。

當做填滿模式使用的點陣圖應為8圖元 x 8 圖元。 如果點陣圖變大，Windows 只會使用對應到點陣圖左上角的前8個數據列和圖元資料行的位。

您可以刪除模式筆刷，而不會影響相關聯的點陣圖。 這表示點陣圖可以用來建立任意數目的模式筆刷。

使用單色點陣圖建立的筆刷（1色平面，每圖元1位）是使用目前的文字和背景色彩繪製。 設定為0的位所代表的圖元會以目前的文字色彩繪製。 以目前的背景色彩繪製位設定為1的圖元。

如需使用[CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)（Windows 函式）的詳細資訊，請參閱 Windows SDK。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>CBrush：： CreateSolidBrush

使用指定的純色，初始化筆刷。

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>參數

*crColor*<br/>
指定筆刷色彩的[COLORREF](/windows/win32/gdi/colorref)結構。 色彩會指定 RGB 值，而且可以使用 WINDOWS 中的 RGB 宏來加以建立。H.

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

然後，可以將筆刷選取為任何裝置內容的目前筆刷。

當應用程式使用 `CreateSolidBrush`建立的筆刷完成時，應該選取裝置內容中的筆刷。

### <a name="example"></a>範例

  請參閱[CBrush：： CBrush](#cbrush)的範例。

##  <a name="createsyscolorbrush"></a>CBrush：： CreateSysColorBrush

初始化筆刷色彩。

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定色彩索引。 這個值會對應到用來繪製21個視窗元素之一的色彩。 如需值清單，請參閱 Windows SDK 中的[GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) 。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

然後，可以將筆刷選取為任何裝置內容的目前筆刷。

當應用程式使用 `CreateSysColorBrush`建立的筆刷完成時，應該選取裝置內容中的筆刷。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>CBrush：： FromHandle

當給定 Windows [HBRUSH](#operator_hbrush)物件的控制碼時，傳回 `CBrush` 物件的指標。

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>參數

*hBrush*<br/>
Windows GDI 筆刷的控制碼。

### <a name="return-value"></a>傳回值

如果成功，則為 `CBrush` 物件的指標;否則為 Null。

### <a name="remarks"></a>備註

如果 `CBrush` 物件尚未附加至控制碼，則會建立並附加暫存 `CBrush` 物件。 只有在下次應用程式的事件迴圈中有閒置時間時，這個暫存 `CBrush` 物件才有效。 此時，會刪除所有的暫存繪圖物件。 換句話說，暫存物件只在處理一個視窗訊息期間有效。

如需使用繪圖物件的詳細資訊，請參閱 Windows SDK 中的[繪圖物件](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>範例

  請參閱[CBrush：： CBrush](#cbrush)的範例。

##  <a name="getlogbrush"></a>CBrush：： GetLogBrush

呼叫這個成員函式，以取得 `LOGBRUSH` 結構。

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>參數

*pLogBrush*<br/>
指向包含筆刷相關資訊的[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構。

### <a name="return-value"></a>傳回值

如果函式成功，且*pLogBrush*是有效的指標，則傳回值會是儲存在緩衝區中的位元組數目。

如果函式成功，且*pLogBrush*為 Null，則傳回值會是保存函式儲存在緩衝區中的資訊所需的位元組數目。

如果函式失敗，則傳回值為0。

### <a name="remarks"></a>備註

`LOGBRUSH` 結構會定義筆刷的樣式、色彩和圖樣。

例如，呼叫 `GetLogBrush` 以符合點陣圖的特定色彩或模式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>CBrush：： operator HBRUSH

使用這個運算子取得 `CBrush` 物件的附加 Windows GDI 控制碼。

```
operator HBRUSH() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為 `CBrush` 物件所表示之 Windows GDI 物件的控制碼;否則為 Null。

### <a name="remarks"></a>備註

這個運算子是一個轉型運算子，可支援直接使用 HBRUSH 物件。

如需使用繪圖物件的詳細資訊，請參閱 Windows SDK 中的[繪圖物件](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 類別](../../mfc/reference/cbitmap-class.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)
