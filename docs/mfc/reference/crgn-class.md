---
title: CRgn 類別
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: 72ab4027880285a3c4cd24d586e163e1e01b98f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368298"
---
# <a name="crgn-class"></a>CRgn 類別

封裝 Windows 繪圖裝置介面 (GDI) 區域。

## <a name="syntax"></a>語法

```
class CRgn : public CGdiObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRgn:CRgn](#crgn)|建構 `CRgn` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRgn::聯合Rgn](#combinergn)|設置`CRgn`物件,使其等效於兩個`CRgn`指定 對象的聯合。|
|[CRgn::複製Rgn](#copyrgn)|設置`CRgn`物件,使其是`CRgn`指定 物件的副本。|
|[CRgn::創造橢圓形](#createellipticrgn)|使用橢圓區域`CRgn`初始化物件。|
|[CRgn::創造橢圓形間接](#createellipticrgnindirect)|初始化具有由`CRgn` [RECT](/windows/win32/api/windef/ns-windef-rect)結構定義的橢圓區域的物件。|
|[CRgn::從資料建立](#createfromdata)|從給定區域創建區域和轉換數據。|
|[CRgn::從路徑建立](#createfrompath)|從所選到給定設備上下文的路徑創建區域。|
|[CRgn::創造波隆龍](#createpolygonrgn)|使用多邊形區域`CRgn`初始化物件。 如有必要,系統通過繪製從最後一個頂點到第一個頂點的線自動關閉面。|
|[CRgn::創造多聚貢](#createpolypolygonrgn)|初始化`CRgn`物件,其區域由一系列閉合多邊形組成。 多邊形可能不交,也可能重疊。|
|[CRgn::建立RectRgn](#createrectrgn)|使用矩形區域初始`CRgn`化物件。|
|[CRgn::創建rectRgn間接](#createrectrgnindirect)|初始化具有由`CRgn` [RECT](/windows/win32/api/windef/ns-windef-rect)分Truture 定義的矩形區域的物件。|
|[CRgn::建立圓形雷茨爾格](#createroundrectrgn)|使用圓角的`CRgn`矩形區域初始化物件。|
|[CRgn::平等Rgn](#equalrgn)|檢查兩`CRgn`個對象以確定它們是否等效。|
|[CRgn::從手柄](#fromhandle)|當為 Windows`CRgn`區域指定句柄時,返回指向物件的指標。|
|[CRgn:取得區域資料](#getregiondata)|使用描述給定區域的數據填充指定的緩衝區。|
|[CRgn::GetRgnBox](#getrgnbox)|檢索`CRgn`物件邊界矩形的座標。|
|[CRgn::偏移Rgn](#offsetrgn)|按指定的`CRgn`偏移量移動物件。|
|[CRgn::Ptin區域](#ptinregion)|確定指定點是否位於該區域中。|
|[CRgn::Rectin 區域](#rectinregion)|確定指定矩形的任何部分是否位於區域的邊界內。|
|[CRgn::塞特勒克·雷克根](#setrectrgn)|將`CRgn`物件設置到指定的矩形區域。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRgn::管理員 HRGN](#operator_hrgn)|返回`CRgn`物件中包含的 Windows 句柄。|

## <a name="remarks"></a>備註

區域是視窗中的橢圓或多邊形區域。 要使用區域,請使用類`CRgn`的成員函數,其中的剪輯函數定義為類`CDC`的成員。

`CRgn`創建、更改和檢索有關為其調用它們的區域物件的資訊的成員函數。

有關`CRgn`使用的詳細資訊,請參考[圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="crgncombinergn"></a><a name="combinergn"></a>CRgn::聯合Rgn

通過合併兩個現有區域創建新的 GDI 區域。

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>參數

*pRgn1*<br/>
標識現有區域。

*pRgn2*<br/>
標識現有區域。

*n 合併模式*<br/>
指定合併兩個源區域時要執行的操作。 它可以是以下任一值:

- RGN_AND 使用兩個區域(交集)的重疊區域。

- RGN_COPY 創建區域 1 的複本(由*pRgn1*標識)。

- RGN_DIFF 創建一個區域,由區域 1(由*pRgn1*標識)的區域組成,區域 2 不屬於區域 2(由*pRgn2*標識)。

- RGN_OR將兩個區域全部合併(聯合)。

- RGN_XOR合併兩個區域,但刪除重疊區域。

### <a name="return-value"></a>傳回值

指定生成的區域的類型。 它可能是下列其中一個值：

- 複雜區域 新區域具有重疊邊框。

- 錯誤 未創建新區域。

- NULL 區域新區域為空。

- SIMPLE區域 新區域沒有重疊邊框。

### <a name="remarks"></a>備註

區域按*nCombineMode*指定進行群組。

兩個指定的區域合併在一起,產生的區域句柄儲存在物件中`CRgn`。 因此,`CRgn`物件中存儲的任何區域都將替換為組合區域。

區域的大小限制為 32,767 個邏輯單元或 64K 記憶體(以較小者為準)。

使用[CopyRgn](#copyrgn)只需將一個區域複製到另一個區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

## <a name="crgncopyrgn"></a><a name="copyrgn"></a>CRgn::複製Rgn

將*pRgnSrc*定義的區域複製`CRgn`到物件中。

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>參數

*普根斯克*<br/>
標識現有區域。

### <a name="return-value"></a>傳回值

指定生成的區域的類型。 它可能是下列其中一個值：

- 複雜區域 新區域具有重疊邊框。

- 錯誤 未創建新區域。

- NULL 區域新區域為空。

- SIMPLE區域 新區域沒有重疊邊框。

### <a name="remarks"></a>備註

新區域替換以前存儲在物件中的`CRgn`區域。 此函數是[組合 Rgn](#combinergn)成員函數的特例。

### <a name="example"></a>範例

  請參閱[CRgn 的範例::創建橢圓。](#createellipticrgn)

## <a name="crgncreateellipticrgn"></a><a name="createellipticrgn"></a>CRgn::創造橢圓形

創建橢圓區域。

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>參數

*x1*<br/>
指定橢圓邊界矩形左上角的邏輯 x 座標。

*y1*<br/>
指定橢圓邊界矩形左上角的邏輯 y 座標。

*x2*<br/>
指定橢圓邊界矩形右下角的邏輯 x 座標。

*y2*<br/>
指定橢圓邊界矩形右下角的邏輯 y 座標。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

該區域由*x1、y1* *、x2*和*y1* *y2*指定的邊界矩形定義。 此區域儲存在物件中`CRgn`。

區域的大小限制為 32,767 個邏輯單元或 64K 記憶體(以較小者為準)。

使用使用`CreateEllipticRgn`函數創建的區域完成後,應用程式應從設備上下文中選擇該區域,並使用函數`DeleteObject`將其刪除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

## <a name="crgncreateellipticrgnindirect"></a><a name="createellipticrgnindirect"></a>CRgn::創造橢圓形間接

創建橢圓區域。

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向包含橢`RECT`圓邊界矩`CRect`形 左上角和右下角邏輯座標的結構或物件。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

區域由*lpRect*指向的結構或物件定義,並儲存在`CRgn`物件中 。

區域的大小限制為 32,767 個邏輯單元或 64K 記憶體(以較小者為準)。

使用使用`CreateEllipticRgnIndirect`函數創建的區域完成後,應用程式應從設備上下文中選擇該區域,並使用函數`DeleteObject`將其刪除。

### <a name="example"></a>範例

  請參考[CRgn 的範例:建立 RectRgn 間接](#createrectrgnindirect)。

## <a name="crgncreatefromdata"></a><a name="createfromdata"></a>CRgn::從資料建立

從給定區域創建區域和轉換數據。

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>參數

*lpXForm*<br/>
指向定義要在區域上執行的轉換的[XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)ata 結構。 如果此指標為 NULL,則使用標識轉換。

*n( N) Count*<br/>
指定*pRgnData*指向的位元組數。

*pRgnData*<br/>
指向包含區域數據的[RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata)資料結構。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式可以通過調`CRgn::GetRegionData`用 函數來檢索區域的數據。

## <a name="crgncreatefrompath"></a><a name="createfrompath"></a>CRgn::從路徑建立

從所選到給定設備上下文的路徑創建區域。

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
標識包含閉合路徑的設備上下文。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

*pDC*參數標識的設備上下文必須包含閉合路徑。 將`CreateFromPath`路徑轉換為區域後,Windows 將從設備上下文中丟棄關閉的路徑。

## <a name="crgncreatepolygonrgn"></a><a name="createpolygonrgn"></a>CRgn::創造波隆龍

創建多邊形區域。

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>參數

*lpPoints*<br/>
指向`POINT`結構陣組或`CPoint`物件陣列。 每個結構指定多邊形一個頂點的 x 座標和 y 座標。 結構`POINT`具有以下形式:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*n( N) Count*<br/>
指定*lpPoints*指向`CPoint`的陣`POINT`列中的結構或物件數。

*nMode*<br/>
指定區域的填充模式。 此參數可以是 ALTERNATE 或 WINDING。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

如有必要,系統通過繪製從最後一個頂點到第一個頂點的線自動關閉面。 產生的區域儲存在物件中`CRgn`。

區域的大小限制為 32,767 個邏輯單元或 64K 記憶體(以較小者為準)。

當多邊形填充模式為 ALTERNATE 時,系統將填充每個掃描行上的奇數和偶數多邊形邊之間的區域。 也就是說,系統填充第一和第二側之間的區域,在第三和第四側之間,等等。

當多邊形填充模式為 WINDING 時,系統使用繪製圖形的方向來確定是否填充區域。 多邊形中的每個線段都以順時針或逆時針方向繪製。 每當從封閉區域繪製到圖形外部的虛線經過順時針線段時,計數就會遞增。 當線通過逆時針線段時,計數將遞減。 如果計數在行到達圖形外部時計數為非零,則填充該區域。

當應用程式使用使用`CreatePolygonRgn`函數創建的區域完成時,它應從設備上下文中選擇該區域,並使用函數`DeleteObject`將其刪除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

## <a name="crgncreatepolypolygonrgn"></a><a name="createpolypolygonrgn"></a>CRgn::創造多聚貢

創建由一系列閉合多邊形組成的區域。

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>參數

*lpPoints*<br/>
指向結構陣列`POINT`或定義多邊形頂`CPoint`點 的物件陣列。 必須顯式關閉每個面,因為系統不會自動關閉它們。 連續指定多邊形。 結構`POINT`具有以下形式:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
指向整數陣列。 第一個整數指定*lpPoints*陣列中第一個多邊形中的頂點數,第二個整數指定第二個多邊形中的頂點數,等等。

*n( N) Count*<br/>
指定*lpPolyCounts*陣列中的整數總數。

*nPolyFill模式下*<br/>
指定多邊形填充模式。 此值可以是 ALTERNATE 或 WINDING。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

產生的區域儲存在物件中`CRgn`。

多邊形可能不交,也可能重疊。

區域的大小限制為 32,767 個邏輯單元或 64K 記憶體(以較小者為準)。

當多邊形填充模式為 ALTERNATE 時,系統將填充每個掃描行上的奇數和偶數多邊形邊之間的區域。 也就是說,系統填充第一和第二側之間的區域,在第三和第四側之間,等等。

當多邊形填充模式為 WINDING 時,系統使用繪製圖形的方向來確定是否填充區域。 多邊形中的每個線段都以順時針或逆時針方向繪製。 每當從封閉區域繪製到圖形外部的虛線經過順時針線段時,計數就會遞增。 當線通過逆時針線段時,計數將遞減。 如果計數在行到達圖形外部時計數為非零,則填充該區域。

當應用程式使用使用`CreatePolyPolygonRgn`函數創建的區域完成時,它應該從設備上下文中選擇該區域,並使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函數來刪除它。

## <a name="crgncreaterectrgn"></a><a name="createrectrgn"></a>CRgn::建立RectRgn

建立存儲在物件中的`CRgn`矩形區域。

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>參數

*x1*<br/>
指定區域左上角的邏輯 x 座標。

*y1*<br/>
指定區域左上角的邏輯 y 座標。

*x2*<br/>
指定區域右下角的邏輯 x 座標。

*y2*<br/>
指定區域右下角的邏輯 y 座標。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

區域的大小限制為 32,767 個邏輯單元或 64K 記憶體(以較小者為準)。

應用程式在完成使用 由創建`CreateRectRgn`的區域後,應使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函數刪除該區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

有關其他範例,請參閱[CRgn::合併 Rgn](#combinergn)。

## <a name="crgncreaterectrgnindirect"></a><a name="createrectrgnindirect"></a>CRgn::創建rectRgn間接

建立存儲在物件中的`CRgn`矩形區域。

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向包含區域`RECT`左`CRect`上 角和右下角的邏輯座標的結構或物件。 結構`RECT`具有以下形式:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

區域的大小限制為 32,767 個邏輯單元或 64K 記憶體(以較小者為準)。

應用程式在完成使用 由創建`CreateRectRgnIndirect`的區域後,應使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函數刪除該區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

## <a name="crgncreateroundrectrgn"></a><a name="createroundrectrgn"></a>CRgn::建立圓形雷茨爾格

建立矩形區域,其圓角儲存在物件中`CRgn`。

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>參數

*x1*<br/>
指定區域左上角的邏輯 x 座標。

*y1*<br/>
指定區域左上角的邏輯 y 座標。

*x2*<br/>
指定區域右下角的邏輯 x 座標。

*y2*<br/>
指定區域右下角的邏輯 y 座標。

*x3*<br/>
指定用於創建圓角的橢圓的寬度。

*y3*<br/>
指定用於創建圓角的橢圓的高度。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

區域的大小限制為 32,767 個邏輯單元或 64K 記憶體(以較小者為準)。

當應用程式使用使用`CreateRoundRectRgn`函數創建的區域完成時,它應該從設備上下文中選擇該區域,並使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函數來刪除它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

## <a name="crgncrgn"></a><a name="crgn"></a>CRgn:CRgn

建構 `CRgn` 物件。

```
CRgn();
```

### <a name="remarks"></a>備註

在`m_hObject`使用一個或多個其他`CRgn`成員 函數初始化物件之前,數據成員不包含有效的 Windows GDI 區域。

### <a name="example"></a>範例

  請參考[CRgn 的範例:建立 RoundrectRgn](#createroundrectrgn)。

## <a name="crgnequalrgn"></a><a name="equalrgn"></a>CRgn::平等Rgn

確定給定區域是否等效於存儲在物件中的`CRgn`區域。

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>參數

*pRgn*<br/>
標識區域。

### <a name="return-value"></a>傳回值

如果兩個區域等效,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

## <a name="crgnfromhandle"></a><a name="fromhandle"></a>CRgn::從手柄

當為 Windows`CRgn`區域指定句柄時,返回指向物件的指標。

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>參數

*hRgn*<br/>
指定 Windows 區域的句柄。

### <a name="return-value"></a>傳回值

`CRgn` 物件的指標。 如果函數未成功,則返回值為 NULL。

### <a name="remarks"></a>備註

如果物件`CRgn`尚未附加到句柄,則創建並附加`CRgn`臨時 物件。 此臨時`CRgn`物件僅在下次應用程式在其事件迴圈中有空閑時間之前有效,此時將刪除所有臨時圖形物件。 另一種說法是臨時物件僅在處理一個視窗消息期間有效。

## <a name="crgngetregiondata"></a><a name="getregiondata"></a>CRgn:取得區域資料

使用描述區域的數據填充指定的緩衝區。

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>參數

*lpRgn 資料*<br/>
指向接收資訊的[RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata)資料結構。 如果此參數為 NULL,則傳回值包含區域資料所需的位元組數。

*n( N) Count*<br/>
指定*lpRgnData*緩衝區的大小(以位元組為單位)。

### <a name="return-value"></a>傳回值

如果函數成功,並且*nCount*指定足夠的位元組數,則傳回值始終為*nCount*。 如果函數失敗,或者如果*nCount*指定的位元組數少於足夠數,則返回值為 0(錯誤)。

### <a name="remarks"></a>備註

此數據包括構成區域的矩形的尺寸。 此功能與函數`CRgn::CreateFromData`結合使用。

## <a name="crgngetrgnbox"></a><a name="getrgnbox"></a>CRgn::GetRgnBox

檢索對象邊界矩形`CRgn`的座標。

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`結構或`CRect`物件以接收邊界矩形的座標。 結構`RECT`具有以下形式:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>傳回值

指定區域的類型。 可以是下列其中任何一個值：

- 複雜區域具有重疊邊框。

- NULL 區域為空。

- 錯誤`CRgn`物件不指定有效的區域。

- SIMPLE 區域沒有重疊邊框。

### <a name="example"></a>範例

  請參考[CRgn 的範例::建立 PolygonRgn](#createpolygonrgn)。

## <a name="crgnoffsetrgn"></a><a name="offsetrgn"></a>CRgn::偏移Rgn

按指定的偏移量移動存儲在`CRgn`物件中的區域。

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>參數

*X.*<br/>
指定向左或向右移動的單位數。

*Y*<br/>
指定要向上或向下移動的單位數。

*點*<br/>
*點的*x 座標指定向左或向右移動的單位數。 *點的*y 座標指定要向上或向下移動的單位數。 *點*參數可以`POINT`是結構參數,也可以`CPoint`是 物件。

### <a name="return-value"></a>傳回值

新區域的類型。 它可以是以下任一值:

- 複雜區域具有重疊邊框。

- 錯誤區域句柄無效。

- NULL 區域為空。

- SIMPLE 區域沒有重疊邊框。

### <a name="remarks"></a>備註

該函數沿 x 軸移動區域*x*單位,沿 y 軸*移動 y*單位。

區域座標值必須小於或等於 32,767,大於或等於 -32,768。 必須仔細選擇*x*和*y*參數,以防止區域座標無效。

### <a name="example"></a>範例

  請參閱[CRgn 的範例::創建橢圓。](#createellipticrgn)

## <a name="crgnoperator-hrgn"></a><a name="operator_hrgn"></a>CRgn::管理員 HRGN

使用此運算元獲取`CRgn`物件的附加 Windows GDI 句柄。

```
operator HRGN() const;
```

### <a name="return-value"></a>傳回值

如果成功,則對物件表示的 Windows`CRgn`GDI 物件的句柄;如果成功,則對物件表示的 Windows GDI 物件的句柄。否則 NULL。

### <a name="remarks"></a>備註

此運算子是強制轉換運算符,支援直接使用HRGN物件。

有關使用圖形物件的詳細資訊,請參閱 Windows SDK 中的[「圖形物件](/windows/win32/gdi/graphic-objects)」一文。

## <a name="crgnptinregion"></a><a name="ptinregion"></a>CRgn::Ptin區域

檢查*x*和*y*給出`CRgn`的點是否位於 儲存在物件中的區域中。

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>參數

*X.*<br/>
指定要測試的點的邏輯 x 座標。

*Y*<br/>
指定要測試的點的邏輯 y 座標。

*點*<br/>
*點的*x 座標和 y 座標指定要測試 的值的點的 x 和 y 座標。 *點*參數可以`POINT`是結構參數,也可以`CPoint`是 物件。

### <a name="return-value"></a>傳回值

如果點位於該區域中,則非零;否則 0。

## <a name="crgnrectinregion"></a><a name="rectinregion"></a>CRgn::Rectin 區域

確定*lpRect*指定的矩形的任何部分是否位於`CRgn`存儲在 物件中的區域的邊界內。

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`結構或`CRect`物件。 結構`RECT`具有以下形式:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>傳回值

如果指定矩形的任何部分位於區域的邊界內,則非零;否則 0。

## <a name="crgnsetrectrgn"></a><a name="setrectrgn"></a>CRgn::塞特勒克·雷克根

創建矩形區域。

```
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*x1*<br/>
指定矩形區域左上角的 x 座標。

*y1*<br/>
指定矩形區域左上角的 y 座標。

*x2*<br/>
指定矩形區域右下角的 x 座標。

*y2*<br/>
指定矩形區域右下角的 y 座標。

*lpRect*<br/>
指定矩形區域。 可以是指向結構的指標,`RECT`也可以是`CRect`物件。

### <a name="remarks"></a>備註

但是,與[CreateRectRgn](#createrectrgn)不同,它不從本地 Windows 應用程式堆中分配任何其他記憶體。 相反,它使用為存儲在`CRgn`物件中的區域分配的空間。 這意味著在調用`SetRectRgn``CRgn`之前,對象必須已使用有效的 Windows 區域初始化。 x1、y1、x2*x2*和*y2*給出的點指定分配空間的*x1**y1*最小大小。

使用此函數而不是`CreateRectRgn`成員函數以避免呼叫本地記憶體管理員。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
