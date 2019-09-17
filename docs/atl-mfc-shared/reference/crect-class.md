---
title: CRect 類別
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: 2c84ce888e37b2a8985ca63cf3544205bc61f69f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491537"
---
# <a name="crect-class"></a>CRect 類別

類似于 Windows [RECT](/windows/win32/api/windef/ns-windef-rect)結構。

## <a name="syntax"></a>語法

```
class CRect : public tagRECT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRect::CRect](#crect)|建構 `CRect` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|傳回的右下`CRect`角。|
|[CRect::CenterPoint](#centerpoint)|傳回的 centerpoint `CRect`。|
|[CRect::CopyRect](#copyrect)|將來源矩形的維度複製到`CRect`。|
|[CRect::DeflateRect](#deflaterect)|減少的寬度和高度`CRect`。|
|[CRect::EqualRect](#equalrect)|`CRect`判斷是否等於指定的矩形。|
|[CRect::Height](#height)|計算的高度`CRect`。|
|[CRect::InflateRect](#inflaterect)|增加的寬度和高度`CRect`。|
|[CRect::IntersectRect](#intersectrect)|設定`CRect`為等於兩個矩形的交集。|
|[CRect::IsRectEmpty](#isrectempty)|判斷是否`CRect`為空的。 `CRect`如果寬度和/或高度為0，則為空白。|
|[CRect::IsRectNull](#isrectnull)|判斷`top`、 `bottom`、 `left`和成員變數是否全部都等於0。`right`|
|[CRect::MoveToX](#movetox)|移`CRect`至指定的 x 座標。|
|[CRect::MoveToXY](#movetoxy)|移`CRect`至指定的 x 和 y 座標。|
|[CRect::MoveToY](#movetoy)|移`CRect`至指定的 y 座標。|
|[CRect::NormalizeRect](#normalizerect)|標準化的高度和寬度`CRect`。|
|[CRect::OffsetRect](#offsetrect)|依`CRect`指定的位移移動。|
|[CRect::PtInRect](#ptinrect)|判斷指定的點是否位於`CRect`。|
|[CRect::SetRect](#setrect)|設定的維度`CRect`。|
|[CRect::SetRectEmpty](#setrectempty)|將`CRect`設定為空的矩形（所有座標都等於0）。|
|[CRect::Size](#size)|計算的大小`CRect`。|
|[CRect::SubtractRect](#subtractrect)|減去另一個矩形。|
|[CRect::TopLeft](#topleft)|傳回的左上角`CRect`。|
|[CRect::UnionRect](#unionrect)|設定`CRect`為等於兩個矩形的聯集。|
|[CRect::Width](#width)|計算的寬度`CRect`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRect：： operator-](#operator_-)|從`CRect`或「洩氣」 `CRect`減去指定的位移，並傳回產生`CRect`的。|
|[CRect：： operator LPCRECT](#operator_lpcrect)|將 `CRect` 轉換成 `LPCRECT`。|
|[CRect：： operator LPRECT](#operator_lprect)|將 `CRect` 轉換成 `LPRECT`。|
|[CRect::operator !=](#operator_neq)|`CRect`判斷是否不等於矩形。|
|[CRect：： operator&amp;](#operator_amp)|建立`CRect`和矩形的交集，並傳回所產生`CRect`的。|
|[CRect：： operator&amp;=](#operator_amp_eq)|設定`CRect`為等於`CRect`和矩形的交集。|
|[CRect：： operator&#124;](#operator_or)|建立`CRect`和矩形的聯集，並傳回所產生`CRect`的。|
|[CRect::operator &#124;=](#operator_or_eq)|設定`CRect`為等於的聯`CRect`集和矩形。|
|[CRect：： operator +](#operator_add)|將指定的位移`CRect`加入或擴大`CRect` ，並傳回產生`CRect`的。|
|[CRect：： operator + =](#operator_add_eq)|將指定的位移`CRect`加入或擴大。 `CRect`|
|[CRect：： operator =](#operator_eq)|將矩形的維度複製到`CRect`。|
|[CRect::operator -=](#operator_-_eq)|從`CRect`或「洩氣」 `CRect`減去指定的位移。|
|[CRect：： operator = =](#operator_eq_eq)|`CRect`判斷是否等於矩形。|

## <a name="remarks"></a>備註

`CRect`也包含用來操作`CRect`物件和 Windows `RECT`結構的成員函式。

只要可以傳遞`LPCRECT` `CRect` `LPRECT`結構、或，就可以將物件當做函數參數傳遞。 `RECT`

> [!NOTE]
> 這個類別衍生自`tagRECT`結構。 （名稱`tagRECT`是`RECT`結構較不常使用的名稱）。這`left`表示`RECT`結構的資料成員（、 `top`、 `right`和`bottom`）是的可存取資料成員`CRect`。

`CRect`包含成員變數，可定義矩形的左上角和右下角點。

當指定`CRect`時，您必須謹慎地加以建立，使其正規化，換句話說，左邊座標的值小於右邊，而頂端小於底部的值。 例如，（10，10）和右下方（20，20）的左上角會定義正規化矩形，但（20，20）和右下方（10，10）的左上方則定義非正規化的矩形。 如果矩形未正規化，許多`CRect`成員函式可能會傳回不正確的結果。 （如需這些函式的清單，請參閱[CRect：： NormalizeRect](#normalizerect) ）。在呼叫需要正規化矩形的函式之前，您可以藉由呼叫`NormalizeRect`函式來將非正規化矩形標準化。

使用`CRect` [cdc：:D ptolp](../../mfc/reference/cdc-class.md#dptolp)和[cdc：： LPtoDP](../../mfc/reference/cdc-class.md#lptodp)成員函式來操作時，請務必小心。 如果顯示內容的對應模式是 y 範圍為負數（例如`MM_LOENGLISH`），則`CDC::DPtoLP`會轉換`CRect` ，使其頂端大於底端。 函式（ `Height`例如`Size`和）接著會針對已轉換`CRect`的高度傳回負值，而矩形則不會正規化。

使用`CRect`多載運算子時，第一個運算元必須`CRect`是，而第二個運算元可以是[RECT](/windows/win32/api/windef/ns-windef-rect)結構或`CRect`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagRECT`

`CRect`

## <a name="requirements"></a>需求

**標頭：** atltypes。h

##  <a name="bottomright"></a>CRect：： BottomRight

座標會當做包含在中`CRect`之[CPoint](cpoint-class.md)物件的參考傳回。

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>傳回值

矩形右下角的座標。

### <a name="remarks"></a>備註

您可以使用此函數來取得或設定矩形的右下角。 在指派運算子的左邊使用此函數來設定角落。

### <a name="example"></a>範例

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

##  <a name="centerpoint"></a>CRect：： CenterPoint

藉`CRect`由新增左和右值並除以二來計算的 centerpoint，並加入頂端和底端的值並除以二。

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>傳回值

Centerpoint `CPoint` 的`CRect`物件。

### <a name="example"></a>範例

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

##  <a name="copyrect"></a>CRect：： CopyRect

將矩形複製到`CRect`。 `lpSrcRect`

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>參數

*lpSrcRect*<br/>
指向要複製的[RECT](/windows/win32/api/windef/ns-windef-rect)結構`CRect`或物件。

### <a name="example"></a>範例

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

##  <a name="crect"></a>CRect：： CRect

建構 `CRect` 物件。

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>參數

*l*<br/>
指定的`CRect`左邊位置。

*t*<br/>
指定的頂端`CRect`。

*r*<br/>
指定的`CRect`正確位置。

*b*<br/>
指定的底部`CRect`。

*srcRect*<br/>
參考具有座標 `CRect`的[矩形](/windows/win32/api/windef/ns-windef-rect)結構。

*lpSrcRect*<br/>
指向具有`CRect`座標的結構。`RECT`

*point*<br/>
指定要建立之矩形的原點。 對應至左上角。

*size*<br/>
指定要建立之矩形右下角的位移。（從左上角）

*topLeft*<br/>
指定的左上角位置`CRect`。

*bottomRight*<br/>
指定的`CRect`右下角位置。

### <a name="remarks"></a>備註

如果未指定任何引數`left`， `top` `right`、、和`bottom`成員就不會初始化。

（ `CRect` ）`const RECT&`和（）`LPCRECT`的構造函式會執行[CopyRect。](#copyrect) `CRect` 其他的函式會直接初始化物件的成員變數。

### <a name="example"></a>範例

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT stucture
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

##  <a name="deflaterect"></a>  CRect::DeflateRect

`DeflateRect`將`CRect`其邊移至其中心，以「洩氣」。

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
指定要 deflate 左邊和右邊`CRect`的單位數。

*y*<br/>
指定要 deflate 頂端和底部`CRect`的單位數。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)或[CSize](csize-class.md) ，指定要 deflate `CRect`的單位數。 值會指定要向左和右側 deflate 的單位數，而值`cy`則指定要 deflate 頂端和底端的單位數。 `cx`

*lpRect*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)結構，或`CRect`指定要 deflate 每一側的單位數。

*l*<br/>
指定要 deflate 左側的`CRect`單位數。

*t*<br/>
指定要 deflate 頂端`CRect`的單位數。

*r*<br/>
指定要 deflate 右側`CRect`的單位數。

*b*<br/>
指定要 deflate 底部`CRect`的單位數。

### <a name="remarks"></a>備註

若要這麼做`DeflateRect` ，請將單位新增至左邊和上方，並將單位從右和下減去。 的參數`DeflateRect`是帶正負號的值，正值`CRect` deflate 和負值會擴大。

前兩個多載會 deflate 兩個相反的`CRect`邊，使其總寬度減少兩倍*x* （或`cx`），而其總高度會減少兩倍*y* （或`cy`）。 其他兩個多載會 deflate 彼此`CRect`獨立的每一邊。

### <a name="example"></a>範例

```cpp
CRect rect(10, 10, 50, 50);
rect.DeflateRect(1, 2);
ASSERT(rect.left == 11 && rect.right == 49);
ASSERT(rect.top == 12 && rect.bottom == 48);

CRect rect2(10, 10, 50, 50);
CRect rectDeflate(1, 2, 3, 4);
rect2.DeflateRect(&rectDeflate);
ASSERT(rect2.left == 11 && rect2.right == 47);
ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

##  <a name="equalrect"></a>CRect：： EqualRect

`CRect`判斷是否等於指定的矩形。

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向包含[矩形](/windows/win32/api/windef/ns-windef-rect)左上角和`CRect`右下角座標的矩形結構或物件。

### <a name="return-value"></a>傳回值

如果兩個矩形具有相同的上、左、下和右值，則為非零。否則為0。

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

##  <a name="height"></a>CRect：： Height

藉由從底部`CRect`值減去前一個值來計算的高度。

```
int Height() const throw();
```

### <a name="return-value"></a>傳回值

的高度`CRect`。

### <a name="remarks"></a>備註

產生的值可以是負數。

> [!NOTE]
>  矩形必須正規化，否則此函數可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)來將矩形正規化，再呼叫此函式。

### <a name="example"></a>範例

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>  CRect::InflateRect

`InflateRect`將`CRect`其邊移離其中心，以擴大。

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
指定要擴大左邊和右邊的`CRect`單位數。

*y*<br/>
指定要擴大頂端和底端`CRect`的單位數。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)或[CSize](csize-class.md) ，指定要擴充的`CRect`單位數。 值會指定要向左和右邊擴大的單位數，而值`cy`則指定要擴大頂端和底端的單位數。 `cx`

*lpRect*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)結構，或`CRect`指定要在每一端擴大的單位數。

*l*<br/>
指定要擴大左邊的`CRect`單位數。

*t*<br/>
指定要擴大頂端`CRect`的單位數。

*r*<br/>
指定要擴大右側的`CRect`單位數。

*b*<br/>
指定要擴大底部`CRect`的單位數。

### <a name="remarks"></a>備註

若要這麼做`InflateRect` ，請從左邊和上方減去單位，並將單位新增至右側和底部。 的參數`InflateRect`是帶正負號的值; 正值`CRect`和負值會 deflate 它。

前兩個多載會將這兩個相反`CRect`的邊同時擴大，使其總寬度增加了兩倍`cx` *x* （或），而其總高度會增加兩倍`cy` *y* （或）。 其他兩個多載會擴充彼此`CRect`獨立的每一邊。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>  CRect::IntersectRect

`CRect`使等於兩個現有矩形的交集。

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>參數

*lpRect1*<br/>
指向包含來源[矩形的矩形](/windows/win32/api/windef/ns-windef-rect)`CRect`結構或物件。

*lpRect2*<br/>
指向包含來源矩形的`CRect` 結構或物件。`RECT`

### <a name="return-value"></a>傳回值

如果交集不是空的，則為非零;如果交集是空的，則為0。

### <a name="remarks"></a>備註

交集是包含在兩個現有矩形中的最大矩形。

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect rectOne(125,  0, 150, 200);
CRect rectTwo(0, 75, 350, 95);
CRect rectInter;

rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

##  <a name="isrectempty"></a>CRect：： IsRectEmpty

判斷是否`CRect`為空的。

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果`CRect`是空的則為非`CRect`零; 如果不是空的，則為0。

### <a name="remarks"></a>備註

如果寬度和/或高度為0或負數，矩形就會是空的。 不同于`IsRectNull`，它會判斷矩形的所有座標是否為零。

> [!NOTE]
>  矩形必須正規化，否則此函數可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)來將矩形正規化，再呼叫此函式。

### <a name="example"></a>範例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>  CRect::IsRectNull

判斷的上、左、下和右值`CRect`是否全都等於0。

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>傳回值

如果`CRect`top、left、底端和 right 值全都等於0，則為非零，否則為0。

### <a name="remarks"></a>備註

不同于`IsRectEmpty`，它會判斷矩形是否為空的。

### <a name="example"></a>範例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

##  <a name="movetox"></a>  CRect::MoveToX

呼叫此函式可將矩形移至*x*所指定的絕對 x 座標。

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
矩形左上角的絕對 x 座標。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

##  <a name="movetoxy"></a>  CRect::MoveToXY

呼叫此函式可將矩形移至指定的絕對 x 和 y 座標。

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
矩形左上角的絕對 x 座標。

*y*<br/>
矩形左上角的絕對 y 座標。

*point*<br/>
`POINT`結構，指定矩形的絕對左上角。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>  CRect::MoveToY

呼叫此函式可將矩形移至*y*所指定的絕對 y 座標。

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>參數

*y*<br/>
矩形左上角的絕對 y 座標。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

##  <a name="normalizerect"></a>  CRect::NormalizeRect

正規化`CRect` ，使高度和寬度都是正數。

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>備註

矩形會針對第四象限位置正規化，而 Windows 通常會使用來進行座標。 `NormalizeRect`比較頂端和底端的值，並在頂端大於底部時加以交換。 同樣地，如果左邊大於右方，它就會交換左邊和右邊的值。 當處理不同的對應模式和反轉矩形時，此函式很有用。

> [!NOTE]
> 下列`CRect`成員函式需要正規化的矩形，才能正常運作：[Height](#height)、 [Width](#width)、 [Size](#size)、 [IsRectEmpty](#isrectempty)、 [PtInRect](#ptinrect)、 [EqualRect](#equalrect)、 [UnionRect](#unionrect)、 [IntersectRect](#intersectrect)、 [SubtractRect](#subtractrect)、 [operator = =](#operator_eq_eq)、 [operator！ =](#operator_neq)、[運算子&#124; ](#operator_or)、 [operator &#124;=](#operator_or_eq)、[運算子 &](#operator_amp)和[運算子 & =](#operator_amp_eq)。

### <a name="example"></a>範例

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>  CRect::OffsetRect

依`CRect`指定的位移移動。

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
指定要向左或向右移動的數量。 必須是負數才能向左移動。

*y*<br/>
指定要向上或向下移動的數量。 必須是負數才能上移。

*point*<br/>
包含[點](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件，指定要移動的兩個維度。

*size*<br/>
包含[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件，指定要移動的兩個維度。

### <a name="remarks"></a>備註

沿著`CRect`X 軸和*y*軸移動*x*個單位。 *X*和*y*參數是帶正負號的值`CRect` ，因此可以向左或向右和向上或向下移動。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>CRect：： operator LPCRECT 會將`CRect`轉換為[LPCRECT](../../mfc/reference/data-types-mfc.md)。

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>備註

當您使用此函式時，不需要 address （ **&** ）運算子。 當您將`CRect`物件傳遞至預期的函式`LPCRECT`時，將會自動使用此運算子。

##  <a name="operator_lprect"></a>CRect：： operator LPRECT

將轉換成 [LPRECT](../../mfc/reference/data-types-mfc.md) `CRect`。

```
operator LPRECT() throw();
```

### <a name="remarks"></a>備註

當您使用此函式時，不需要 address （ **&** ）運算子。 當您將`CRect`物件傳遞至預期的函式`LPRECT`時，將會自動使用此運算子。

### <a name="example"></a>範例

請參閱[CRect：： OPERATOR LPCRECT](#operator_lpcrect)的範例。

##  <a name="operator_eq"></a>CRect：： operator =

將*srcRect*指派`CRect`給。

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>參數

*srcRect*<br/>
參考來源矩形。 可以是[矩形](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>CRect：： operator = =

藉`CRect`由`rect`比較其左上角和右下角的座標，判斷是否等於。

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>參數

*rect*<br/>
參考來源矩形。 可以是[矩形](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>傳回值

如果等於則為非零值;否則為0。

### <a name="remarks"></a>備註

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

##  <a name="operator_neq"></a>CRect：： operator！ =

藉`CRect`由比較其左上角和右下角的座標，判斷*矩形*是否不等於。

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>參數

*rect*<br/>
參考來源矩形。 可以是[矩形](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>傳回值

非零（如果不等於）;否則為0。

### <a name="remarks"></a>備註

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

##  <a name="operator_add_eq"></a>CRect：： operator + =

前兩個多載`CRect`會依指定的位移移動。

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>參數

*point*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件，指定要移動矩形的單位數。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件，指定要移動矩形的單位數。

*lpRect*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)結構或`CRect`物件，其中包含要擴充每一側`CRect`的單位數。

### <a name="remarks"></a>備註

參數的*x*和*y* （或`cx`和`cy`）值會加入至`CRect`。

第三個多`CRect`載會以參數的每個成員中指定的單位數擴大。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>CRect：： operator-=

前兩個多載`CRect`會依指定的位移移動。

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>參數

*point*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件，指定要移動矩形的單位數。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件，指定要移動矩形的單位數。

*lpRect*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)結構或`CRect`物件，其中包含要`CRect`deflate 之每一方的單位數。

### <a name="remarks"></a>備註

參數的*x*和*y* （或`cx`和`cy`）值會從`CRect`減去。

第三個多`CRect`載會以參數的每個成員中指定的單位數「洩氣」。 請注意，這種多載的功能就像[DeflateRect](#deflaterect)。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>CRect：： operator&amp;=

設定`CRect`為等於`CRect`和`rect`的交集。

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>參數

*rect*<br/>
包含[矩形](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="remarks"></a>備註

交集是包含在這兩個矩形中的最大矩形。

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

請參閱[CRect：： IntersectRect](#intersectrect)的範例。

##  <a name="operator_or_eq"></a>CRect：： operator &#124;=

設定`CRect`為等於`CRect`和`rect`的聯集。

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>參數

*rect*<br/>
包含或[矩形。](/windows/win32/api/windef/ns-windef-rect) `CRect`

### <a name="remarks"></a>備註

聯集是包含兩個來源矩形的最小矩形。

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>CRect：： operator +

前兩個`CRect`多載會傳回等於以`CRect`指定位移來取代的物件。

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>參數

*point*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件，指定要移動傳回值的單位數。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件，指定要移動傳回值的單位數。

*lpRect*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)結構或`CRect`物件，其中包含要擴充傳回值各端的單位數。

### <a name="return-value"></a>傳回值

由`CRect`參數中指定的單位`CRect`數移動或因而誇大所產生的。

### <a name="remarks"></a>備註

參數的*x*和*y* （或`cx`和`cy`）參數會加入至`CRect`的位置。

第三個多載會`CRect`傳回新的， `CRect`其等於以參數的每個成員中指定的單位數來放大。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>CRect：： operator-

前兩個`CRect`多載會傳回等於以`CRect`指定位移來取代的物件。

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>參數

*point*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或`CPoint`物件，指定要移動傳回值的單位數。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或`CSize`物件，指定要移動傳回值的單位數。

*lpRect*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)結構或`CRect`物件，其中包含要 deflate 傳回值各端的單位數。

### <a name="return-value"></a>傳回值

由`CRect`參數中指定的單位`CRect`數移動或 deflating 所產生的。

### <a name="remarks"></a>備註

參數的*x*和*y* （或`cx`和`cy`）參數會從`CRect`的位置減去。

第三個多載會`CRect`傳回新的， `CRect`其等於縮小是參數的每個成員中指定的單位數。 請注意，這種多載功能如[DeflateRect](#deflaterect)，而非[SubtractRect](#subtractrect)。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>CRect：： operator&amp;

傳回與 rect2 交集的。 `CRect` `CRect`

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>參數

*rect2*<br/>
包含[矩形](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>傳回值

，它是`CRect`和 rect2 的交集。 `CRect`

### <a name="remarks"></a>備註

交集是包含在這兩個矩形中的最大矩形。

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>  CRect::operator &#124;

傳回， `CRect`它是和 rect2 的聯集。 `CRect`

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>參數

*rect2*<br/>
包含[矩形](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>傳回值

，它是`CRect`和 rect2 的聯集。 `CRect`

### <a name="remarks"></a>備註

聯集是最小的矩形，其中同時包含兩個矩形。

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>  CRect::PtInRect

判斷指定的點是否位於`CRect`。

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>參數

*point*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件。

### <a name="return-value"></a>傳回值

如果點位於內`CRect`，則為非零，否則為0。

### <a name="remarks"></a>備註

如果點位於左邊`CRect`或頂端，或是在四側的兩側，就會在內。 右側或底部的點在外`CRect`。

> [!NOTE]
>  矩形必須正規化，否則此函數可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)來將矩形正規化，再呼叫此函式。

### <a name="example"></a>範例

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

##  <a name="setrect"></a>  CRect::SetRect

將的維度`CRect`設定為指定的座標。

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>參數

*x1*<br/>
指定左上角的 x 座標。

*y1*<br/>
指定左上角的 y 座標。

*x2*<br/>
指定右下角的 x 座標。

*y2*<br/>
指定右下角的 y 座標。

### <a name="example"></a>範例

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>CRect：： SetRectEmpty

將`CRect`所有座標設定為零，以建立 null 矩形。

```
void SetRectEmpty() throw();
```

### <a name="example"></a>範例

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

##  <a name="size"></a>CRect：： SIZE

傳回`cx`值`cy`的和成員包含`CRect`的高度和寬度。

```
CSize Size() const throw();
```

### <a name="return-value"></a>傳回值

包含大小的`CRect`[CSize](csize-class.md) 物件。

### <a name="remarks"></a>備註

高度或寬度都可以是負數。

> [!NOTE]
>  矩形必須正規化，否則此函數可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)來將矩形正規化，再呼叫此函式。

### <a name="example"></a>範例

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>  CRect::SubtractRect

使的維度`CRect`等於的`lpRectSrc2`減去`lpRectSrc1`。

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>參數

*lpRectSrc1*<br/>
指向`CRect` [矩形結構或物件，以](/windows/win32/api/windef/ns-windef-rect)從中減去矩形。

*lpRectSrc2*<br/>
指向要從*lpRectSrc1*參數`CRect`所指向的矩形中減去的結構或物件。`RECT`

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

減法是最小的矩形，其中包含*lpRectScr1*中不在*lpRectScr1*和*lpRectScr2*交集的所有點。

如果*lpRectSrc2*所指定的矩形未完全與至少一個 x 或 y 方向的*lpRectSrc1*所指定的矩形重迭， *lpRectSrc1*所指定的矩形將會維持不變。

例如，如果*lpRectSrc1*是（10，10，100100），而*lpRectSrc2*是（50，50，150150），則當函式傳回時， *lpRectSrc1*所指向的矩形會保持不變。 不過，如果*lpRectSrc1*為（10，10，100100）且*lpRectSrc2*為（50，10，150150），則當函式傳回時， *lpRectSrc1*所指向的矩形會包含座標（10，10，50100）。

`SubtractRect`與[operator](#operator_-)和 operator [-=](#operator_-_eq)不相同。 這兩個運算子都不`SubtractRect`會呼叫。

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
RECT   rectOne;
RECT   rectTwo;

rectOne.left = 10;
rectOne.top = 10;
rectOne.bottom = 100;
rectOne.right = 100;

rectTwo.left = 50;
rectTwo.top = 10;
rectTwo.bottom = 150;
rectTwo.right = 150;

CRect   rectDiff;

rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

ASSERT(rectDiff == rectResult);

// works for CRect, too, since there is
// implicit CRect -> LPCRECT conversion

CRect rect1(10, 10, 100, 100);
CRect rect2(50, 10, 150, 150);
CRect rectOut;

rectOut.SubtractRect(rect1, rect2);
ASSERT(rectResult == rectOut);
```

##  <a name="topleft"></a>  CRect::TopLeft

座標會當做包含在中`CRect`之[CPoint](cpoint-class.md)物件的參考傳回。

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>傳回值

矩形左上角的座標。

### <a name="remarks"></a>備註

您可以使用此函式來取得或設定矩形的左上角。 在指派運算子的左邊使用此函數來設定角落。

### <a name="example"></a>範例

請參閱[CRect：： CenterPoint](#centerpoint)的範例。

##  <a name="unionrect"></a>  CRect::UnionRect

使的維度`CRect`等於兩個來源矩形的聯集。

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>參數

*lpRect1*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)或`CRect`包含來源矩形的。

*lpRect2*<br/>
指向包含來源矩形`CRect`的或。`RECT`

### <a name="return-value"></a>傳回值

如果聯集不是空的，則為非零;如果聯集是空的，則為0。

### <a name="remarks"></a>備註

聯集是包含兩個來源矩形的最小矩形。

Windows 會忽略空白矩形的維度;也就是沒有高度或沒有寬度的矩形。

> [!NOTE]
>  這兩個矩形必須正規化，否則此函式可能會失敗。 呼叫[NormalizeRect](#normalizerect)可在呼叫此函式之前，先將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="width"></a>CRect：： Width

藉`CRect`由從右邊的值減去左邊的值，來計算的寬度。

```
int Width() const throw();
```

### <a name="return-value"></a>傳回值

的寬度`CRect`。

### <a name="remarks"></a>備註

寬度可以是負數。

> [!NOTE]
>  矩形必須正規化，否則此函數可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)來將矩形正規化，再呼叫此函式。

### <a name="example"></a>範例

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>另請參閱

[CPoint 類別](cpoint-class.md)<br/>
[CSize 類別](csize-class.md)<br/>
[各種](/windows/win32/api/windef/ns-windef-rect)
