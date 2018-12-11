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
ms.openlocfilehash: 74ee046e81e0f55e5550220166c957317c2bf6cd
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178547"
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
|[CRgn::CRgn](#crgn)|建構 `CRgn` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|設定組`CRgn`物件，讓它相當於兩個指定的聯集`CRgn`物件。|
|[CRgn::CopyRgn](#copyrgn)|設定組`CRgn`物件，使它是一份指定的`CRgn`物件。|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|初始化`CRgn`橢圓形的區域物件。|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|初始化`CRgn`物件所定義的橢圓形區域[RECT](/windows/desktop/api/windef/ns-windef-tagrect)結構。|
|[CRgn::CreateFromData](#createfromdata)|從指定的區域和轉換資料，會建立區域。|
|[CRgn::CreateFromPath](#createfrompath)|從所選入指定的裝置內容的路徑中建立區域。|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|初始化`CRgn`物件的多邊形的區域。 系統多邊形會自動關閉，如有必要，所繪製一條線從上次的頂點，第一個。|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|初始化`CRgn`物件，其中包含一系列的封閉的多邊形的區域。 多邊形可能是脫離的或者可能會重疊。|
|[CRgn::CreateRectRgn](#createrectrgn)|初始化`CRgn`物件的矩形區域。|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|初始化`CRgn`物件所定義的矩形區域[RECT](/windows/desktop/api/windef/ns-windef-tagrect)結構。|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|初始化`CRgn`物件與具有圓角矩形區域。|
|[CRgn::EqualRgn](#equalrgn)|檢查兩個`CRgn`物件，判斷它們是否相等。|
|[CRgn::FromHandle](#fromhandle)|將指標傳回至`CRgn`物件給 Windows 區域中的控制代碼時。|
|[CRgn::GetRegionData](#getregiondata)|描述指定的區域的資料填入指定的緩衝區。|
|[CRgn::GetRgnBox](#getrgnbox)|擷取指定的週框的座標`CRgn`物件。|
|[CRgn::OffsetRgn](#offsetrgn)|移動`CRgn`物件所指定的位移。|
|[CRgn::PtInRegion](#ptinregion)|判斷指定的點是否在區域中。|
|[CRgn::RectInRegion](#rectinregion)|判斷指定的任何的矩形部分是否為區域的界限內。|
|[CRgn::SetRectRgn](#setrectrgn)|設定`CRgn`物件到指定的矩形區域。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRgn::operator HRGN](#operator_hrgn)|傳回包含在 Windows 控制代碼`CRgn`物件。|

## <a name="remarks"></a>備註

區域是在範圍內的橢圓形或多邊形的區域。 若要使用的區域，您可以使用類別的成員函式`CRgn`裁剪函式定義為類別的成員與`CDC`。

成員函式`CRgn`建立、 改變和擷取的呼叫它們的區域物件的相關資訊。

如需有關使用`CRgn`，請參閱 <<c2> [ 圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="combinergn"></a>  CRgn::CombineRgn

藉由結合兩個現有的區域中建立新的 GDI 區域。

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>參數

*pRgn1*<br/>
識別現有的區域。

*pRgn2*<br/>
識別現有的區域。

*nCombineMode*<br/>
指定合併兩個來源區域時要執行的作業。 它可以是下列值之一：

- RGN_AND 使用重疊的兩個區域 （交集） 的區域。

- RGN_COPY 建立區域 1 的複本 (由*pRgn1*)。

- RGN_DIFF 建立組成區域 1 的區域的區域 (由*pRgn1*)，不是 2 個區域的一部分 (識別*pRgn2*)。

- RGN_OR 結合這兩個區域中完整 （聯集）。

- RGN_XOR 結合這兩個區域，但會移除重疊的區域。

### <a name="return-value"></a>傳回值

指定產生的區域類型。 它可以是下列值之一：

- COMPLEXREGION 新區域會有重疊的框線。

- 沒有新的區域建立的錯誤。

- NULLREGION 新區域是空的。

- SIMPLEREGION 新區域沒有任何重疊的框線。

### <a name="remarks"></a>備註

區域的組合所指定*nCombineMode*。

兩個指定的區域的組合，而且產生的區域控制代碼會儲存在`CRgn`物件。 因此，任何區域會儲存在`CRgn`結合區域所取代的物件。

區域的大小限制為 32767 的 32,767 的邏輯單元或 64k 的記憶體，取其較小。

使用[CopyRgn](#copyrgn) ，只要將一個區域複製到另一個區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>  CRgn::CopyRgn

複製所定義的區域*pRgnSrc*到`CRgn`物件。

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>參數

*pRgnSrc*<br/>
識別現有的區域。

### <a name="return-value"></a>傳回值

指定產生的區域類型。 它可以是下列值之一：

- COMPLEXREGION 新區域會有重疊的框線。

- 沒有新的區域建立的錯誤。

- NULLREGION 新區域是空的。

- SIMPLEREGION 新區域沒有任何重疊的框線。

### <a name="remarks"></a>備註

新的區域會取代先前儲存在區域`CRgn`物件。 此函式是特殊案例[CombineRgn](#combinergn)成員函式。

### <a name="example"></a>範例

  範例，請參閱[CRgn::CreateEllipticRgn](#createellipticrgn)。

##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn

建立橢圓形的區域。

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>參數

*x1*<br/>
指定邏輯橢圓形的週框矩形的左上角的 x 座標。

*y1*<br/>
指定邏輯橢圓形的週框矩形的左上角的 y 座標。

*x2*<br/>
指定邏輯橢圓形的週框矩形右下角的 x 座標。

*y2*<br/>
指定邏輯橢圓形的週框矩形右下角的 y 座標。

### <a name="return-value"></a>傳回值

如果作業成功，否則為非零值否則為 0。

### <a name="remarks"></a>備註

區域由所指定的週框矩形*x1*， *y1*， *x2*，以及*y2*。 區域儲存在`CRgn`物件。

區域的大小限制為 32767 的 32,767 的邏輯單元或 64k 的記憶體，取其較小。

已完成時使用以建立區域`CreateEllipticRgn`函式應用程式應該選取的裝置內容和使用的區域放大`DeleteObject`函式來移除它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

建立橢圓形的區域。

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`結構或`CRect`物件，其中包含邏輯橢圓形的週框左上角和右下角邊角的座標。

### <a name="return-value"></a>傳回值

如果作業成功，否則為非零值否則為 0。

### <a name="remarks"></a>備註

結構或所指向的物件所定義的區域*lpRect*並儲存在`CRgn`物件。

區域的大小限制為 32767 的 32,767 的邏輯單元或 64k 的記憶體，取其較小。

已完成時使用以建立區域`CreateEllipticRgnIndirect`函式應用程式應該選取的裝置內容和使用的區域放大`DeleteObject`函式來移除它。

### <a name="example"></a>範例

  範例，請參閱[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)。

##  <a name="createfromdata"></a>  CRgn::CreateFromData

從指定的區域和轉換資料，會建立區域。

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>參數

*lpXForm*<br/>
指向[XFORM](/windows/desktop/api/wingdi/ns-wingdi-tagxform)資料結構，定義要在區域上執行的轉換。 如果此指標為 NULL，則會使用識別轉換。

*nCount*<br/>
指定所指向的位元組數目*pRgnData*。

*pRgnData*<br/>
指向[RGNDATA](/windows/desktop/api/wingdi/ns-wingdi-_rgndata)資料結構，包含區域資料。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式可以擷取區域的資料，藉由呼叫`CRgn::GetRegionData`函式。

##  <a name="createfrompath"></a>  CRgn::CreateFromPath

從所選入指定的裝置內容的路徑中建立區域。

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
識別包含封閉的路徑的裝置內容。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

所識別的裝置內容*pDC*參數必須包含已關閉的路徑。 之後`CreateFromPath`路徑到區域時，Windows 將會捨棄從裝置內容已關閉的路徑。

##  <a name="createpolygonrgn"></a>  CRgn::CreatePolygonRgn

建立多邊形的區域。

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>參數

*lpPoints*<br/>
指向陣列`POINT`結構或陣列`CPoint`物件。 每個結構指定的 x 座標和 y 座標一個多邊形頂點。 `POINT`結構具有下列格式：

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
指定的數目`POINT`結構或`CPoint`所指陣列中的物件*lpPoints*。

*nMode*<br/>
指定區域的填滿模式。 這個參數可能是替代或捲繞。

### <a name="return-value"></a>傳回值

如果作業成功，否則為非零值否則為 0。

### <a name="remarks"></a>備註

系統多邊形會自動關閉，如有必要，所繪製一條線從上次的頂點，第一個。 產生的區域會儲存在`CRgn`物件。

區域的大小限制為 32767 的 32,767 的邏輯單元或 64k 的記憶體，取其較小。

替代的多邊形填滿模式時，系統就會填入掃描一行奇數和偶數的多邊形側邊之間的區域。 亦即，系統會填滿區域之間的第一個和第二個邊，等第三個和第四個側邊之間。

當捲繞多邊形填滿模式時，系統就會使用以判斷是否要填滿區域已繪製圖形的方向。 順時針或逆時針方向會繪製多邊形中的每個直線線段。 每當從括住的區域繪製到圖表的外部虛構線段通過順時針方向的線段的計數會遞增。 當行通過逆時針算起的直線線段時，計數會遞減。 如果計數為非零值，在線條數到達外部的圖時，會填滿區域。

當應用程式已完成使用區域，以建立`CreatePolygonRgn`函式，它應該選取的裝置內容和使用的區域放大`DeleteObject`函式來移除它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn

建立包含一系列的封閉的多邊形的區域。

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>參數

*lpPoints*<br/>
指向陣列`POINT`結構或陣列`CPoint`定義的多邊形頂點的物件。 每個多邊形必須明確地關閉，因為系統不會關閉其自動。 多邊形會指定連續。 `POINT`結構具有下列格式：

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
指向陣列的整數。 第一個整數指定的頂點數目在中，第一個多邊形*lpPoints*第二個整數的陣列指定的頂點數目在第二個多邊形，依此類推。

*nCount*<br/>
指定之整數的總數*lpPolyCounts*陣列。

*nPolyFillMode*<br/>
指定的多邊形填滿模式。 此值可能替代或捲繞。

### <a name="return-value"></a>傳回值

如果作業成功，否則為非零值否則為 0。

### <a name="remarks"></a>備註

產生的區域會儲存在`CRgn`物件。

多邊形可能是脫離的或者可能會重疊。

區域的大小限制為 32767 的 32,767 的邏輯單元或 64k 的記憶體，取其較小。

替代的多邊形填滿模式時，系統就會填入掃描一行奇數和偶數的多邊形側邊之間的區域。 亦即，系統會填滿區域之間的第一個和第二個邊，等第三個和第四個側邊之間。

當捲繞多邊形填滿模式時，系統就會使用以判斷是否要填滿區域已繪製圖形的方向。 順時針或逆時針方向會繪製多邊形中的每個直線線段。 每當從括住的區域繪製到圖表的外部虛構線段通過順時針方向的線段的計數會遞增。 當行通過逆時針算起的直線線段時，計數會遞減。 如果計數為非零值，在線條數到達外部的圖時，會填滿區域。

當應用程式已完成使用區域，以建立`CreatePolyPolygonRgn`函式，它應該選取的裝置內容和使用的區域放大[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式，將它移除。

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

建立會儲存在矩形區域`CRgn`物件。

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>參數

*x1*<br/>
指定邏輯區域的左上角的 x 座標。

*y1*<br/>
指定邏輯區域的左上角的 y 座標。

*x2*<br/>
指定邏輯區域右下角的 x 座標。

*y2*<br/>
指定邏輯區域右下角的 y 座標。

### <a name="return-value"></a>傳回值

如果作業成功，否則為非零值否則為 0。

### <a name="remarks"></a>備註

區域的大小限制為 32767 的 32,767 的邏輯單元或 64k 的記憶體，取其較小。

當完成使用所建立的區域`CreateRectRgn`，應用程式應該使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式來移除區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

如需其他範例，請參閱 < [CRgn::CombineRgn](#combinergn)。

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

建立會儲存在矩形區域`CRgn`物件。

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`結構或`CRect`物件，包含區域的左上角和右下角邊角的邏輯座標。 `RECT`結構具有下列格式：

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>傳回值

如果作業成功，否則為非零值否則為 0。

### <a name="remarks"></a>備註

區域的大小限制為 32767 的 32,767 的邏輯單元或 64k 的記憶體，取其較小。

當完成使用所建立的區域`CreateRectRgnIndirect`，應用程式應該使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式來移除區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn

建立具有圓角中所儲存的矩形區域`CRgn`物件。

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
指定邏輯區域的左上角的 x 座標。

*y1*<br/>
指定邏輯區域的左上角的 y 座標。

*x2*<br/>
指定邏輯區域右下角的 x 座標。

*y2*<br/>
指定邏輯區域右下角的 y 座標。

*x3*<br/>
指定用來建立圓的角的省略符號的寬度。

*y3*<br/>
指定用來建立圓的角的省略符號的高度。

### <a name="return-value"></a>傳回值

如果作業成功，否則為非零值否則為 0。

### <a name="remarks"></a>備註

區域的大小限制為 32767 的 32,767 的邏輯單元或 64k 的記憶體，取其較小。

當應用程式已完成使用區域，以建立`CreateRoundRectRgn`函式，它應該選取的裝置內容和使用的區域放大[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式，將它移除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>  CRgn::CRgn

建構 `CRgn` 物件。

```
CRgn();
```

### <a name="remarks"></a>備註

`m_hObject`資料成員不包含有效的 Windows GDI 區域，直到物件會初始化與一或多個其他`CRgn`成員函式。

### <a name="example"></a>範例

  範例，請參閱[CRgn::CreateRoundRectRgn](#createroundrectrgn)。

##  <a name="equalrgn"></a>  CRgn::EqualRgn

判斷指定的區域是否相當於儲存在區域`CRgn`物件。

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>參數

*pRgn*<br/>
識別的區域。

### <a name="return-value"></a>傳回值

如果兩個區域相等，非零值。否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>  CRgn::FromHandle

將指標傳回至`CRgn`物件給 Windows 區域中的控制代碼時。

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>參數

*hRgn*<br/>
指定 Windows 區域的控制代碼。

### <a name="return-value"></a>傳回值

`CRgn` 物件的指標。 如果函式不成功，則傳回的值會是 NULL。

### <a name="remarks"></a>備註

如果`CRgn`物件尚未附加至控制代碼，暫存`CRgn`建立物件並將其連結。 此暫存`CRgn`物件是否有效，直到下一次應用程式在其事件迴圈中有閒置的時間，在那所有暫存的圖形物件，會刪除只。 另一種說法是，此暫存物件的一個視窗訊息處理期間才有效。

##  <a name="getregiondata"></a>  CRgn::GetRegionData

描述區域的資料填入指定的緩衝區。

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>參數

*lpRgnData*<br/>
指向[RGNDATA](/windows/desktop/api/wingdi/ns-wingdi-_rgndata)接收資訊的資料結構。 如果此參數為 NULL，則傳回的值會包含所需的區域資料的位元組數目。

*nCount*<br/>
指定的大小，以位元組為單位*lpRgnData*緩衝區。

### <a name="return-value"></a>傳回值

如果函式成功並*nCount*指定足夠數目的位元組，傳回的值一定是*nCount*。 如果函式失敗，或如果*nCount*指定小於比足夠的位元組數目，傳回值是 0 （錯誤）。

### <a name="remarks"></a>備註

此資料包含組成區域的矩形的維度。 此函式用於搭配`CRgn::CreateFromData`函式。

##  <a name="getrgnbox"></a>  CRgn::GetRgnBox

擷取指定的週框的座標`CRgn`物件。

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`結構或`CRect`物件接收指定的週框的座標。 `RECT`結構具有下列格式：

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>傳回值

指定區域的類型。 它可以是下列值之一：

- COMPLEXREGION 區域具有重疊的框線。

- NULLREGION 區域是空的。

- 錯誤`CRgn`物件未指定有效的區域。

- SIMPLEREGION 區域沒有任何重疊的框線。

### <a name="example"></a>範例

  範例，請參閱[CRgn::CreatePolygonRgn](#createpolygonrgn)。

##  <a name="offsetrgn"></a>  CRgn::OffsetRgn

將儲存在區域`CRgn`物件所指定的位移。

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>參數

*x*<br/>
指定要向左移動或向右的單位數目。

*y*<br/>
指定要上移或下移的單位數。

*點*<br/>
X 座標*點*指定要向左移動或向右的單位數目。 Y 座標*點*指定要上移或下移的單位數。 *點*參數可以是`POINT`結構或`CPoint`物件。

### <a name="return-value"></a>傳回值

新的區域類型。 它可以是下列值之一：

- COMPLEXREGION 區域具有重疊的框線。

- 錯誤區域控制代碼無效。

- NULLREGION 區域是空的。

- SIMPLEREGION 區域沒有任何重疊的框線。

### <a name="remarks"></a>備註

函式會移動的區域*x*沿著 x 軸單位並*y*沿著 y 軸的單位。

區域的座標值必須小於或等於 32,767 而且大於或等於-32,768。 *x*並*y*參數必須小心選擇以防止無效的區域座標。

### <a name="example"></a>範例

  範例，請參閱[CRgn::CreateEllipticRgn](#createellipticrgn)。

##  <a name="operator_hrgn"></a>  CRgn::operator HRGN

使用這個運算子來取得附加的 Windows GDI 控制代碼的`CRgn`物件。

```
operator HRGN() const;
```

### <a name="return-value"></a>傳回值

如果成功，Windows GDI 物件的控制代碼所表示`CRgn`物件; 否則為 NULL。

### <a name="remarks"></a>備註

這位操作員便轉型運算子，可支援直接使用 HRGN 物件。

如需有關如何使用 圖形物件的詳細資訊，請參閱[圖形物件](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

##  <a name="ptinregion"></a>  CRgn::PtInRegion

檢查是否所指定的點*x*並*y*儲存在位於區域`CRgn`物件。

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>參數

*x*<br/>
指定要測試的點的邏輯 x 座標。

*y*<br/>
指定要測試的點的邏輯 y 座標。

*點*<br/>
X 和 y 座標的*點*指定要測試的值的點 x 和 y 座標。 *點*參數可以是`POINT`結構或`CPoint`物件。

### <a name="return-value"></a>傳回值

如果該點是在區域中，為非零否則為 0。

##  <a name="rectinregion"></a>  CRgn::RectInRegion

判斷所指定矩形的任何一部分*lpRect*是儲存在區域的界限內`CRgn`物件。

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`結構或`CRect`物件。 `RECT`結構具有下列格式：

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>傳回值

如果指定的任何的矩形部分位於界限內的區域，為非零否則為 0。

##  <a name="setrectrgn"></a>  CRgn::SetRectRgn

建立矩形區域。

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
指定之矩形區域左上角的 x 座標。

*y1*<br/>
指定之矩形區域左上角的 y 座標。

*x2*<br/>
指定之矩形區域右下角的 x 座標。

*y2*<br/>
指定之矩形區域右下角的 y 座標。

*lpRect*<br/>
指定的矩形區域。 可以是以指標`RECT`結構或`CRect`物件。

### <a name="remarks"></a>備註

不同於[CreateRectRgn](#createrectrgn)，不過，它不會配置任何額外的記憶體從本機 Windows 應用程式堆積。 相反地，它會使用配置的儲存區域的空間`CRgn`物件。 這表示`CRgn`物件必須有已初始化有效的 Windows 地區，然後再呼叫與`SetRectRgn`。 所指定的點*x1*， *y1*， *x2*，以及*y2*指定的最小的已配置空間。

使用此函式，而不是`CreateRectRgn`成員函式，以避免呼叫本機記憶體管理員。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

