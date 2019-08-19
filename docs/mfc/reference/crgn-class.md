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
ms.openlocfilehash: 34dcc618f603302c5598e42588ffad78d61ee222
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502718"
---
# <a name="crgn-class"></a>CRgn 類別

封裝 Windows 繪圖裝置介面 (GDI) 區域。

## <a name="syntax"></a>語法

```
class CRgn : public CGdiObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CRgn:: CRgn](#crgn)|建構 `CRgn` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|設定物件, 使其相當於兩個指定`CRgn`之物件的聯集。 `CRgn`|
|[CRgn::CopyRgn](#copyrgn)|設定物件, 使其成為指定`CRgn`之物件的複本。 `CRgn`|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|初始化具有橢圓形區域的物件。`CRgn`|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|使用[矩形](/windows/win32/api/windef/ns-windef-tagrect)結構所定義的橢圓形區域, 初始化物件。`CRgn`|
|[CRgn::CreateFromData](#createfromdata)|從指定的區域和轉換資料建立區域。|
|[CRgn::CreateFromPath](#createfrompath)|從選取的路徑建立區域到指定的裝置內容。|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|使用多邊形區域初始化物件。`CRgn` 系統會在必要時自動關閉多邊形, 方法是從最後一個頂點繪製一條線到第一個。|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|使用由一系列封閉多邊形組成的區域, 初始化物件。`CRgn` 多邊形可能不相鄰, 或可能會重迭。|
|[CRgn::CreateRectRgn](#createrectrgn)|使用矩形區域初始化物件。`CRgn`|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|使用由[矩形](/windows/win32/api/windef/ns-windef-rect)結構 t) 所定義的矩形區域, 初始化物件。`CRgn`|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|使用具有圓角的矩形區域, 初始化物件。`CRgn`|
|[CRgn::EqualRgn](#equalrgn)|檢查兩`CRgn`個物件, 判斷它們是否相等。|
|[CRgn::FromHandle](#fromhandle)|當指定 Windows 區域的`CRgn`控制碼時, 傳回物件的指標。|
|[CRgn::GetRegionData](#getregiondata)|以描述給定區域的資料填滿指定的緩衝區。|
|[CRgn::GetRgnBox](#getrgnbox)|抓取`CRgn`物件周框的座標。|
|[CRgn::OffsetRgn](#offsetrgn)|依據指定的位移移動物件。`CRgn`|
|[CRgn::PtInRegion](#ptinregion)|判斷指定的點是否在區域中。|
|[CRgn::RectInRegion](#rectinregion)|判斷指定之矩形的任何部分是否在區域的界限內。|
|[CRgn::SetRectRgn](#setrectrgn)|`CRgn`將物件設定為指定的矩形區域。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRgn:: operator HRGN](#operator_hrgn)|傳回包含在`CRgn`物件中的 Windows 控制碼。|

## <a name="remarks"></a>備註

區域是視窗內的橢圓形或多邊形區域。 若要使用區域, 您可以使用類別`CRgn`的成員函式, 並將裁剪函式定義為類別`CDC`的成員。

的成員`CRgn`函式會建立、改變和抓取其所呼叫之區域物件的相關資訊。

如需使用`CRgn`的詳細資訊, 請參閱[繪圖物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="combinergn"></a>CRgn:: CombineRgn

結合兩個現有的區域, 以建立新的 GDI 區域。

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
指定合併兩個來源區域時要執行的作業。 它可以是下列任何一個值:

- RGN_AND 會使用兩個區域的重迭區域 (交集)。

- RGN_COPY 會建立區域1的複本 (由*pRgn1*識別)。

- RGN_DIFF 會建立一個區域, 其中包含不屬於區域 2 (由*pRgn2*識別) 的區域1區域 (由*pRgn1*識別)。

- RGN_OR 會將這兩個區域全部結合在一起 (聯集)。

- RGN_XOR 會結合這兩個區域, 但會移除重迭的區域。

### <a name="return-value"></a>傳回值

指定所產生之區域的類型。 它可以是下列其中一個值:

- COMPLEXREGION 新區域具有重迭的框線。

- 錯誤: 未建立任何新區域。

- NullREGION 新區域是空的。

- SIMPLEREGION 新區域沒有任何重迭的框線。

### <a name="remarks"></a>備註

區域會依照*nCombineMode*所指定的方式結合。

這兩個指定的區域會合並, 而產生的區域控制碼會`CRgn`儲存在物件中。 因此, 儲存在`CRgn`物件中的任何區域都會由合併的區域取代。

區域的大小限制為32767、32767個邏輯單元或64K 的記憶體, 取兩者中較小者。

使用[CopyRgn](#copyrgn)直接將一個區域複製到另一個區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>CRgn:: CopyRgn

將*pRgnSrc*定義的區域複製到`CRgn`物件中。

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>參數

*pRgnSrc*<br/>
識別現有的區域。

### <a name="return-value"></a>傳回值

指定所產生之區域的類型。 它可以是下列其中一個值:

- COMPLEXREGION 新區域具有重迭的框線。

- 錯誤: 未建立任何新區域。

- NullREGION 新區域是空的。

- SIMPLEREGION 新區域沒有任何重迭的框線。

### <a name="remarks"></a>備註

新的區域會取代先前儲存在`CRgn`物件中的區域。 此函式是[CombineRgn](#combinergn)成員函式的特殊案例。

### <a name="example"></a>範例

  請參閱[CRgn:: CreateEllipticRgn](#createellipticrgn)的範例。

##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn

建立橢圓形區域。

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>參數

*x1*<br/>
指定橢圓形的周框左上角的邏輯 x 座標。

*y1*<br/>
指定橢圓形的周框左上角的邏輯 y 座標。

*x2*<br/>
指定橢圓形周框之右下角的邏輯 x 座標。

*y2*<br/>
指定橢圓形周框之右下角的邏輯 y 座標。

### <a name="return-value"></a>傳回值

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

區域是由*x1*、 *y1*、 *x2*和*y2*所指定的周框所定義。 區域會儲存在`CRgn`物件中。

區域的大小限制為32767、32767個邏輯單元或64K 的記憶體, 取兩者中較小者。

當它完成使用以`CreateEllipticRgn`函式建立的區域時, 應用程式應該從裝置內容中選取區域, 並`DeleteObject`使用函式將它移除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

建立橢圓形區域。

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
`RECT`指向結構`CRect`或物件, 其中包含橢圓形周框的左上角和右下角的邏輯座標。

### <a name="return-value"></a>傳回值

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

區域是由*lpRect*所指向的結構或物件所定義, 並儲存在`CRgn`物件中。

區域的大小限制為32767、32767個邏輯單元或64K 的記憶體, 取兩者中較小者。

當它完成使用以`CreateEllipticRgnIndirect`函式建立的區域時, 應用程式應該從裝置內容中選取區域, 並`DeleteObject`使用函式將它移除。

### <a name="example"></a>範例

  請參閱[CRgn:: CreateRectRgnIndirect](#createrectrgnindirect)的範例。

##  <a name="createfromdata"></a>CRgn:: CreateFromData

從指定的區域和轉換資料建立區域。

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>參數

*lpXForm*<br/>
指向[XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)ata 結構, 其定義要在區域上執行的轉換。 如果此指標為 Null, 則會使用身分識別轉換。

*nCount*<br/>
指定*pRgnData*所指向的位元組數目。

*pRgnData*<br/>
指向包含區域資料的[RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata)資料結構。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式可以藉由呼叫`CRgn::GetRegionData`函數來抓取區域的資料。

##  <a name="createfrompath"></a>CRgn:: CreateFromPath

從選取的路徑建立區域到指定的裝置內容。

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
識別包含關閉路徑的裝置內容。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

*PDC*參數所識別的裝置內容必須包含封閉式路徑。 將`CreateFromPath`路徑轉換成區域之後, Windows 會捨棄裝置內容中的關閉路徑。

##  <a name="createpolygonrgn"></a>CRgn:: CreatePolygonRgn

建立多邊形區域。

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>參數

*lpPoints*<br/>
指向結構的`POINT`陣列或物件的`CPoint`陣列。 每個結構都會指定多邊形的一個頂點的 x 座標和 y 座標。 `POINT`結構具有下列格式:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
指定 lpPoints 所指向`POINT`之陣列`CPoint`中的結構或物件數目。

*nMode*<br/>
指定區域的填滿模式。 這個參數可以是替代或纏繞。

### <a name="return-value"></a>傳回值

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

系統會在必要時自動關閉多邊形, 方法是從最後一個頂點繪製一條線到第一個。 產生的區域會儲存在`CRgn`物件中。

區域的大小限制為32767、32767個邏輯單元或64K 的記憶體, 取兩者中較小者。

當多邊形填滿模式為 [替代] 時, 系統會在每個掃描線上的奇數和偶數多邊形邊填滿區域。 也就是說, 系統會填滿第一個和第二端之間、第三和第四端之間的區域, 依此類推。

當多邊形填滿模式是纏繞時, 系統會使用繪製圖形的方向來判斷是否要填滿區域。 多邊形中的每個直線線段都會以順時針或逆時針方向繪製。 每當從封閉區域繪製到圖形外的虛數直線通過順時針線段時, 就會遞增計數。 當線條通過逆時針線段時, 計數就會遞減。 當線條到達圖表的外部時, 如果計數為非零值, 則會填滿區域。

當應用程式完成使用以`CreatePolygonRgn`函式建立的區域時, 應該從裝置內容中選取區域, 並`DeleteObject`使用函式將它移除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>CRgn:: CreatePolyPolygonRgn

建立由一系列封閉多邊形組成的區域。

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>參數

*lpPoints*<br/>
指向結構的`POINT`陣列, 或定義多邊形頂點的`CPoint`物件陣列。 每個多邊形都必須明確地關閉, 因為系統不會自動關閉它們。 多邊形會連續指定。 `POINT`結構具有下列格式:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
指向整數陣列。 第一個整數指定*lpPoints*陣列中第一個多邊形的頂點數目, 第二個整數指定第二個多邊形的頂點數目, 依此類推。

*nCount*<br/>
指定*lpPolyCounts*陣列中的整數總數。

*nPolyFillMode*<br/>
指定多邊形填滿模式。 此值可以是 [替代] 或 [纏繞]。

### <a name="return-value"></a>傳回值

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

產生的區域會儲存在`CRgn`物件中。

多邊形可能不相鄰, 或可能會重迭。

區域的大小限制為32767、32767個邏輯單元或64K 的記憶體, 取兩者中較小者。

當多邊形填滿模式為 [替代] 時, 系統會在每個掃描線上的奇數和偶數多邊形邊填滿區域。 也就是說, 系統會填滿第一個和第二端之間、第三和第四端之間的區域, 依此類推。

當多邊形填滿模式是纏繞時, 系統會使用繪製圖形的方向來判斷是否要填滿區域。 多邊形中的每個直線線段都會以順時針或逆時針方向繪製。 每當從封閉區域繪製到圖形外的虛數直線通過順時針線段時, 就會遞增計數。 當線條通過逆時針線段時, 計數就會遞減。 當線條到達圖表的外部時, 如果計數為非零值, 則會填滿區域。

當應用程式完成使用以`CreatePolyPolygonRgn`函式建立的區域時, 應該從裝置內容中選取區域, 並使用[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式將它移除。

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

建立儲存在`CRgn`物件中的矩形區域。

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

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

區域的大小限制為32767、32767個邏輯單元或64K 的記憶體, 取兩者中較小者。

當它使用建立`CreateRectRgn`的區域完成時, 應用程式應該使用[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式來移除該區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

如需其他範例, 請參閱[CRgn:: CombineRgn](#combinergn)。

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

建立儲存在`CRgn`物件中的矩形區域。

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向結構或`CRect`物件, 其中包含區域左上方和右下角的邏輯座標。 `RECT` `RECT`結構具有下列格式:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>傳回值

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

區域的大小限制為32767、32767個邏輯單元或64K 的記憶體, 取兩者中較小者。

當它使用建立`CreateRectRgnIndirect`的區域完成時, 應用程式應該使用[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式來移除該區域。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>CRgn:: CreateRoundRectRgn

建立具有圓角的矩形區域, 並儲存在`CRgn`物件中。

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
指定用來建立圓角的橢圓形寬度。

*y3*<br/>
指定用來建立圓角的橢圓形高度。

### <a name="return-value"></a>傳回值

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

區域的大小限制為32767、32767個邏輯單元或64K 的記憶體, 取兩者中較小者。

當應用程式完成使用以`CreateRoundRectRgn`函式建立的區域時, 應該從裝置內容中選取區域, 並使用[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式將它移除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>CRgn:: CRgn

建構 `CRgn` 物件。

```
CRgn();
```

### <a name="remarks"></a>備註

資料成員不包含有效的 Windows GDI 區域, 直到使用一或多個其他`CRgn`成員函式初始化物件為止。 `m_hObject`

### <a name="example"></a>範例

  請參閱[CRgn:: CreateRoundRectRgn](#createroundrectrgn)的範例。

##  <a name="equalrgn"></a>CRgn:: EqualRgn

判斷指定的區域是否等同于儲存在`CRgn`物件中的區域。

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>參數

*pRgn*<br/>
識別區域。

### <a name="return-value"></a>傳回值

如果兩個區域相等, 則為非零值;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>CRgn:: FromHandle

當指定 Windows 區域的`CRgn`控制碼時, 傳回物件的指標。

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>參數

*hRgn*<br/>
指定 Windows 區域的控制碼。

### <a name="return-value"></a>傳回值

          `CRgn` 物件的指標。 如果函式不成功, 則傳回值為 Null。

### <a name="remarks"></a>備註

如果物件尚未附加至控制碼, 則會建立並附加`CRgn`暫存物件。 `CRgn` 這個暫存`CRgn`物件只有在下一次應用程式的事件迴圈中有閒置時間時才有效, 此時所有的暫存繪圖物件都會被刪除。 另一個指出這種情況的方法是, 暫存物件只在處理一個視窗訊息期間有效。

##  <a name="getregiondata"></a>CRgn:: GetRegionData

以描述區域的資料填滿指定的緩衝區。

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>參數

*lpRgnData*<br/>
指向接收資訊的[RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata)資料結構。 如果這個參數是 Null, 則傳回值會包含區域資料所需的位元組數目。

*nCount*<br/>
指定*lpRgnData*緩衝區的大小 (以位元組為單位)。

### <a name="return-value"></a>傳回值

如果函式成功, 而且*nCount*指定了足夠的位元組數目, 則傳回值一律會是*nCount*。 如果函式失敗, 或*nCount*指定的位元組數目少於足夠, 則傳回值為 0 (錯誤)。

### <a name="remarks"></a>備註

此資料包含組成區域的矩形維度。 此函式會與`CRgn::CreateFromData`函數搭配使用。

##  <a name="getrgnbox"></a>CRgn:: GetRgnBox

抓取`CRgn`物件周框的座標。

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向結構或`CRect`物件, 以接收周框的座標。 `RECT` `RECT`結構具有下列格式:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>傳回值

指定區域的類型。 它可以是下列任何值:

- COMPLEXREGION 區域具有重迭的框線。

- NullREGION 區域是空的。

- 錯誤`CRgn`物件未指定有效的區域。

- SIMPLEREGION 區域沒有重迭的框線。

### <a name="example"></a>範例

  請參閱[CRgn:: CreatePolygonRgn](#createpolygonrgn)的範例。

##  <a name="offsetrgn"></a>  CRgn::OffsetRgn

依據指定的位移, 移動`CRgn`儲存在物件中的區域。

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>參數

*x*<br/>
指定要向左或向右移動的單位數。

*y*<br/>
指定要向上或向下移動的單位數。

*point*<br/>
*Point*的 x 座標會指定要向左或向右移動的單位數。 *Point*的 y 座標會指定要向上或向下移動的單位數。 *Point*參數可以`POINT`是結構或`CPoint`物件。

### <a name="return-value"></a>傳回值

新區域的類型。 它可以是下列任何一個值:

- COMPLEXREGION 區域具有重迭的框線。

- 錯誤區域控制碼無效。

- NullREGION 區域是空的。

- SIMPLEREGION 區域沒有重迭的框線。

### <a name="remarks"></a>備註

函式沿著 X 軸和*y*軸移動區域*x*單位。

區域的座標值必須小於或等於 32767, 且大於或等於-32768。 必須謹慎選擇*x*和*y*參數, 以防止不正確區域座標。

### <a name="example"></a>範例

  請參閱[CRgn:: CreateEllipticRgn](#createellipticrgn)的範例。

##  <a name="operator_hrgn"></a>CRgn:: operator HRGN

使用這個運算子取得`CRgn`物件附加的 Windows GDI 控制碼。

```
operator HRGN() const;
```

### <a name="return-value"></a>傳回值

如果成功, 則為`CRgn`物件所表示之 Windows GDI 物件的控制碼, 否則為 Null。

### <a name="remarks"></a>備註

這個運算子是一個轉型運算子, 可支援直接使用 HRGN 物件。

如需使用繪圖物件的詳細資訊, 請參閱 Windows SDK 中的[繪圖物件](/windows/win32/gdi/graphic-objects)一文。

##  <a name="ptinregion"></a>CRgn::P tInRegion

檢查*x*和*y*所指定的點是否位於`CRgn`儲存于物件中的區域。

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>參數

*x*<br/>
指定要測試之點的邏輯 x 座標。

*y*<br/>
指定要測試之點的邏輯 y 座標。

*point*<br/>
*Point*的 x 和 y 座標會指定點的 x 和 y 座標, 以測試的值。 *Point*參數可以是`POINT`結構或`CPoint`物件。

### <a name="return-value"></a>傳回值

如果點在區域中, 則為非零值;否則為0。

##  <a name="rectinregion"></a>  CRgn::RectInRegion

判斷*lpRect*所指定之矩形的任何部分是否在`CRgn`物件所儲存區域的界限內。

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向結構或`CRect`物件。 `RECT` `RECT`結構具有下列格式:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>傳回值

如果指定矩形的任何部分位於區域界限內, 則為非零值;否則為0。

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
指定矩形區域左上角的 x 座標。

*y1*<br/>
指定矩形區域左上角的 y 座標。

*x2*<br/>
指定矩形區域右下角的 x 座標。

*y2*<br/>
指定矩形區域右下角的 y 座標。

*lpRect*<br/>
指定矩形區域。 可以是`RECT`結構`CRect`或物件的指標。

### <a name="remarks"></a>備註

但是與[CreateRectRgn](#createrectrgn)不同的是, 它不會從本機 Windows 應用程式堆積配置任何額外的記憶體。 相反地, 它會使用配置給儲存在`CRgn`物件中之區域的空間。 這表示在`CRgn`呼叫`SetRectRgn`之前, 物件必須已經使用有效的 Windows 區域初始化。 *X1*、 *y1*、 *x2*和*y2*所提供的點會指定配置空間的大小下限。

使用此函式而非`CreateRectRgn`成員函式, 以避免呼叫本機記憶體管理員。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
