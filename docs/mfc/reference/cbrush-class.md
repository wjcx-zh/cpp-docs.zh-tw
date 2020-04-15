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
ms.openlocfilehash: 15132bb5497886638edfe431ae769dd446785df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352484"
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
|[畫筆::CBrush](#cbrush)|建構 `CBrush` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[畫筆::創建畫筆間接](#createbrushindirect)|使用[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構中指定的樣式、顏色和圖案初始化畫筆。|
|[筆刷:建立 DIB 模式筆刷](#createdibpatternbrush)|使用與設備無關的點陣圖 (DIB) 指定的模式初始化畫筆。|
|[筆刷::建立陰影畫筆](#createhatchbrush)|使用指定的陰影圖案和顏色初始化畫筆。|
|[筆刷:建立模式筆刷](#createpatternbrush)|使用點陣圖指定的模式初始化畫筆。|
|[畫筆::創建實心筆](#createsolidbrush)|使用指定的純色初始化畫筆。|
|[畫筆::建立Sys顏色筆刷](#createsyscolorbrush)|創建預設系統顏色的畫筆。|
|[畫筆::從手柄](#fromhandle)|為`HBRUSH`Windows`CBrush`物件 指定句柄時,傳回指向物件的指標。|
|[筆刷::取得紀錄筆刷](#getlogbrush)|獲取[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[畫筆::操作員 HBRUSH](#operator_hbrush)|返回附加到`CBrush`物件的 Windows 句柄。|

## <a name="remarks"></a>備註

要使用`CBrush`物件,建構`CBrush`物件 並將其傳遞給需要畫筆`CDC`的任何 成員函數。

畫筆可以是實心的、陰影的或圖案的。

有關 的詳細`CBrush`資訊 ,請參閱[圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cbrushcbrush"></a><a name="cbrush"></a>畫筆::CBrush

建構 `CBrush` 物件。

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>參數

*crColor*<br/>
將筆刷的前景顏色指定為 RGB 顏色。 如果填充畫筆,此參數指定陰影的顏色。

*nIndex*<br/>
指定畫筆的填充樣式。 它可以是以下任一值:

- HS_BDIAGONAL在 45 度下向下艙口(從左到右)

- HS_CROSS水平和垂直剖面

- HS_DIAGCROSS十字哈奇在 45 度

- HS_FDIAGONAL向上艙口(從左到右)在 45 度

- HS_HORIZONTAL水平艙口

- HS_VERTICAL垂直艙口

*pBitmap*<br/>
指向指定畫筆`CBitmap`繪製的點陣圖的物件。

### <a name="remarks"></a>備註

`CBrush`有四個重載構造函數。沒有參數的構造函數構造了一個未初始化`CBrush`的物件,該物件必須先初始化才能使用。

如果使用沒有參數的建構函數,`CBrush`則必須使用[CreateSolidBrush、CreateHatchBrush、](#createsolidbrush)[創建Brush間接](#createbrushindirect),[創建模式畫筆](#createpatternbrush)或[創建DIBPatternBrush](#createdibpatternbrush)來初始化生成的物件。 [CreateHatchBrush](#createhatchbrush) 如果使用一個採用參數的構造函數,則無需進一步初始化。 如果遇到錯誤,具有參數的構造函數可以引發異常,而沒有參數的構造函數將始終成功。

具有單個[COLORREF](/windows/win32/gdi/colorref)參數的建構函數建構具有指定顏色的實體畫筆。 顏色指定 RGB 值,可以使用 WINDOWS 中的 RGB 宏構造。H。

具有兩個參數的構造函數構造一個剖面線畫筆。 *nIndex*參數指定陰影模式的索引。 *crColor*參數指定顏色。

具有參數的`CBitmap`構造函數構造了模式畫筆。 參數標識位圖。 假定位圖是通過使用[CBitmap::createBitmap、CBitmap:create](../../mfc/reference/cbitmap-class.md#createbitmap)間接映射[、CBitmap:::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)或[CBitmap::創建相容位圖](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)創建的。 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect) 在填充圖案中使用的位圖的最小大小為 8 像素 x 8 圖元。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

## <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>畫筆::創建畫筆間接

使用[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構中指定的樣式、顏色和圖案初始化畫筆。

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>參數

*lpLogBrush*<br/>
指向包含有關畫筆資訊的[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

隨後,可以選擇畫筆作為任何設備上下文的當前畫筆。

使用單色(1 平面,每圖元 1 位)位圖創建的畫筆使用當前文本和背景顏色繪製。 由位設置為 0 表示的圖元將用當前文字顏色繪製。 由設置為 1 的位錶示的圖元將繪製為當前背景顏色。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

## <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>筆刷:建立 DIB 模式筆刷

使用與設備無關的點陣圖 (DIB) 指定的模式初始化畫筆。

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>參數

*h包裝DIB*<br/>
標識包含打包的設備無關位圖 (DIB) 的全域記憶體物件。

*n 使用*<br/>
指定`bmiColors[]`[BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo)資料結構的欄位(「打包 DIB」的一部分)是否包含顯式 RGB 值或索引到當前已實現的邏輯調色板中。 參數必須是以下值之一:

- DIB_PAL_COLORS 顏色表由16位索引組成的陣列組成。

- DIB_RGB_COLORS 顏色表包含文字 RGB 值。

*lpPackedDIB*<br/>
指向由`BITMAPINFO`結構組成的打包 DIB,緊接著是定義位圖圖元的位元組。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隨後,可以為支援柵格操作的任何設備上下文選擇畫筆。

這兩個版本在處理 DIB 時有所不同:

- 在第一個版本中,要獲取 DIB 的句柄,請`GlobalAlloc`調用 Windows 函數來分配全域記憶體區塊,然後用打包的 DIB 填充記憶體。

- 在第二個版本中,無需調用`GlobalAlloc`為打包的 DIB 分配記憶體。

打包的 DIB`BITMAPINFO`由一個數據結構組成,緊接定義位圖圖元的位元組。 用作填充圖案的位圖應為 8 圖元 x 8 圖元。 如果位圖較大,Windows 僅使用與位圖左上角的前 8 行和 8 列像素對應的位創建填充模式。

當應用程式在單色設備上下文中選擇雙色 DIB 圖案畫筆時,Windows 會忽略 DIB 中指定的顏色,而是使用設備上下文的當前文本和背景顏色顯示圖案畫筆。 使用文字顏色顯示映射到 DIB 的第一種顏色(DIB 顏色表中的偏移 0)的圖元。 使用背景顏色顯示映射到第二種顏色的圖元(在顏色表中的偏移量 1)。

有關使用以下 Windows 功能的資訊,請參閱 Windows SDK:

- [CreateDIBPatternBrush(](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush)此函數僅用於與為 3.0 早於 Windows 版本編寫的應用程式相`CreateDIBPatternBrushPt`容而提供;使用 該函數。

- [創建 DIBPatternBrushPt(](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt)此功能應用於基於 Win32 的應用程式。

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

## <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>筆刷::建立陰影畫筆

使用指定的陰影圖案和顏色初始化畫筆。

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定畫筆的填充樣式。 它可以是以下任一值:

- HS_BDIAGONAL在 45 度下向下艙口(從左到右)

- HS_CROSS水平和垂直剖面

- HS_DIAGCROSS十字哈奇在 45 度

- HS_FDIAGONAL向上艙口(從左到右)在 45 度

- HS_HORIZONTAL水平艙口

- HS_VERTICAL垂直艙口

*crColor*<br/>
將筆刷的前景顏色指定為 RGB 顏色(陰影的顏色)。 有關詳細資訊,請參閱 Windows SDK 中的[COLORREF。](/windows/win32/gdi/colorref)

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隨後,可以選擇畫筆作為任何設備上下文的當前畫筆。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

## <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>筆刷:建立模式筆刷

使用點陣圖指定的模式初始化畫筆。

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>參數

*pBitmap*<br/>
標識位圖。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隨後,可以為支援柵格操作的任何設備上下文選擇畫筆。 *pBitmap*識別的點陣圖通常使用[CBitmap:createBitmap、CBitmap:create](../../mfc/reference/cbitmap-class.md#createbitmap)間接[、CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)或[CBitmap:create 相容位圖](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函數進行初始化。 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)

用作填充圖案的位圖應為 8 圖元 x 8 圖元。 如果位圖較大,Windows 將僅使用與位圖左上角的前 8 行和圖元列對應的位。

可以刪除模式畫筆,而不會影響關聯的位圖。 這意味著位圖可用於創建任意數量的模式畫筆。

使用單色位圖(1 色平面,每圖元 1 位)創建的畫筆使用當前文本和背景顏色繪製。 由設置為 0 的位錶示的圖元使用當前文字顏色繪製。 由設置為 1 的位錶示的圖元使用當前背景顏色繪製。

有關使用[創建模式畫筆](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)(Windows 函數)的資訊,請參閱 Windows SDK。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

## <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>畫筆::創建實心筆

使用指定的純色初始化畫筆。

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>參數

*crColor*<br/>
指定筆顏色的[COLORREF](/windows/win32/gdi/colorref)結構。 顏色指定 RGB 值,可以使用 WINDOWS 中的 RGB 宏構造。H。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隨後,可以選擇畫筆作為任何設備上下文的當前畫筆。

當應用程式使用 創建`CreateSolidBrush`的畫筆完成時,它應從設備上下文中選擇畫筆。

### <a name="example"></a>範例

  請參閱[CBrush 的範例:CBrush](#cbrush)。

## <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>畫筆::建立Sys顏色筆刷

初始化畫筆顏色。

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定顏色索引。 此值對應於用於繪製 21 個視窗元素之一的顏色。 有關值清單,請參閱 Windows SDK 中的[GetSysColor。](/windows/win32/api/winuser/nf-winuser-getsyscolor)

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隨後,可以選擇畫筆作為任何設備上下文的當前畫筆。

當應用程式使用 創建`CreateSysColorBrush`的畫筆完成時,它應從設備上下文中選擇畫筆。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

## <a name="cbrushfromhandle"></a><a name="fromhandle"></a>畫筆::從手柄

當為 Windows `CBrush` [HBRUSH](#operator_hbrush)物件的句柄指定時,返回指向物件的指標。

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>參數

*hBrush*<br/>
處理到 Windows GDI 畫筆。

### <a name="return-value"></a>傳回值

指向`CBrush`物件的指標(如果成功);如果成功,則指向物件。否則 NULL。

### <a name="remarks"></a>備註

如果物件`CBrush`尚未附加到句柄,則創建並附加`CBrush`臨時 物件。 此臨時`CBrush`物件僅在下次應用程式在其事件迴圈中有空閑時間之前才有效。 此時,將刪除所有臨時圖形物件。 換句話說,臨時物件僅在處理一個視窗消息期間有效。

有關使用圖形物件的詳細資訊,請參閱 Windows SDK 中的[圖形物件](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>範例

  請參閱[CBrush 的範例:CBrush](#cbrush)。

## <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a>筆刷::取得紀錄筆刷

調用此成員函數以檢索`LOGBRUSH`結構。

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>參數

*pLogBrush*<br/>
指向包含有關畫筆資訊的[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構。

### <a name="return-value"></a>傳回值

如果函數成功,並且*pLogBrush*是有效的指標,則返回值是存儲在緩衝區中的位元組數。

如果函數成功,並且*pLogBrush*為 NULL,則返回值是保存函數將存儲到緩衝區中的資訊所需的位元組數。

如果函數失敗,則返回值為 0。

### <a name="remarks"></a>備註

結構`LOGBRUSH`定義畫筆的風格、顏色和圖案。

例如,調用`GetLogBrush`以匹配位圖的特定顏色或模式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

## <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>畫筆::操作員 HBRUSH

使用此運算元獲取`CBrush`物件的附加 Windows GDI 句柄。

```
operator HBRUSH() const;
```

### <a name="return-value"></a>傳回值

如果成功,則對物件表示的 Windows`CBrush`GDI 物件的句柄;如果成功,則對物件表示的 Windows GDI 物件的句柄。否則 NULL。

### <a name="remarks"></a>備註

此運算子是強制轉換運算符,支援直接使用 HBRUSH 物件。

有關使用圖形物件的詳細資訊,請參閱 Windows SDK 中的[圖形物件](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 類別](../../mfc/reference/cbitmap-class.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)
