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
ms.openlocfilehash: f45090971e8dbb89ae281b408cc3a14e102ffe17
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502876"
---
# <a name="crect-class"></a>CRect 類別

類似于 Windows [RECT](/windows/win32/api/windef/ns-windef-rect) 結構。

## <a name="syntax"></a>語法

```
class CRect : public tagRECT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRect：： CRect](#crect)|建構 `CRect` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRect：： BottomRight](#bottomright)|傳回的右下角 `CRect` 。|
|[CRect：： CenterPoint](#centerpoint)|傳回的 centerpoint `CRect` 。|
|[CRect：： CopyRect](#copyrect)|將來源矩形的維度複製到 `CRect` 。|
|[CRect：:D eflateRect](#deflaterect)|減少的寬度和高度 `CRect` 。|
|[CRect：： EqualRect](#equalrect)|判斷是否 `CRect` 等於指定的矩形。|
|[CRect：： Height](#height)|計算的高度 `CRect` 。|
|[CRect：： InflateRect](#inflaterect)|增加的寬度和高度 `CRect` 。|
|[CRect：： IntersectRect](#intersectrect)|設定 `CRect` 等於兩個矩形的交集。|
|[CRect：： IsRectEmpty](#isrectempty)|判斷是否 `CRect` 為空的。 `CRect` 如果寬度和/或高度為0，則為空白。|
|[CRect：： IsRectNull](#isrectnull)|判斷 `top` 、 `bottom` 、 `left` 和 `right` 成員變數全都是否等於0。|
|[CRect：： MoveToX](#movetox)|移 `CRect` 至指定的 x 座標。|
|[CRect：： MoveToXY](#movetoxy)|移 `CRect` 至指定的 x 和 y 座標。|
|[CRect：： MoveToY](#movetoy)|移 `CRect` 至指定的 y 座標。|
|[CRect：： NormalizeRect](#normalizerect)|標準化的高度和寬度 `CRect` 。|
|[CRect：： OffsetRect](#offsetrect)|`CRect`依指定的位移移動。|
|[CRect：:P tInRect](#ptinrect)|判斷指定的點是否位於內部 `CRect` 。|
|[CRect：： SetRect](#setrect)|設定的維度 `CRect` 。|
|[CRect：： SetRectEmpty](#setrectempty)|設定 `CRect` 為空的矩形， (所有座標等於 0) 。|
|[CRect：： Size](#size)|計算的大小 `CRect` 。|
|[CRect：： SubtractRect](#subtractrect)|將一個矩形減去另一個。|
|[CRect：：下拉式功能表](#topleft)|傳回的左上角 `CRect` 。|
|[CRect：： UnionRect](#unionrect)|設定 `CRect` 等於兩個矩形的聯集。|
|[CRect：： Width](#width)|計算的寬度 `CRect` 。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRect：： operator-](#operator_-)|從或「洩氣」減去指定的位移 `CRect` `CRect` ，並傳回結果 `CRect` 。|
|[CRect：： operator LPCRECT](#operator_lpcrect)|將 `CRect` 轉換成 `LPCRECT`。|
|[CRect：： operator LPRECT](#operator_lprect)|將 `CRect` 轉換成 `LPRECT`。|
|[CRect：： operator！ =](#operator_neq)|判斷是否 `CRect` 不等於矩形。|
|[CRect：： operator &amp;](#operator_amp)|建立 `CRect` 和矩形的交集，並傳回結果 `CRect` 。|
|[CRect：： operator &amp;=](#operator_amp_eq)|設定 `CRect` 等於和矩形的交集 `CRect` 。|
|[CRect：： operator &#124;](#operator_or)|建立和矩形的聯集 `CRect` ，並傳回結果 `CRect` 。|
|[CRect：： operator &#124;=](#operator_or_eq)|設定 `CRect` 等於和矩形的聯集 `CRect` 。|
|[CRect：： operator +](#operator_add)|將指定的位移加入 `CRect` 或擴大 `CRect` ，並傳回產生的 `CRect` 。|
|[CRect：： operator + =](#operator_add_eq)|將指定的位移加入至 `CRect` 或擴大 `CRect` 。|
|[CRect：： operator =](#operator_eq)|將矩形的維度複製到 `CRect` 。|
|[CRect：： operator-=](#operator_-_eq)|從或「洩氣」減去指定的位移 `CRect` `CRect` 。|
|[CRect：： operator = =](#operator_eq_eq)|判斷是否 `CRect` 等於矩形。|

## <a name="remarks"></a>備註

`CRect` 也包含可操作 `CRect` 物件和 Windows 結構的成員函式 `RECT` 。

`CRect`只要 `RECT` `LPCRECT` 可以傳遞結構、或，就可以將物件傳遞為函數參數 `LPRECT` 。

> [!NOTE]
> 這個類別衍生自 `tagRECT` 結構。  (名稱 `tagRECT` 是結構較不常使用的名稱 `RECT` 。 ) 這表示結構 (、、和) 的資料成員 `left` `top` `right` `bottom` `RECT` 都是的資料成員 `CRect` 。

`CRect`包含定義矩形左上角和右下角的成員變數。

當您指定時 `CRect` ，您必須謹慎地加以建立，以便進行正規化，也就是左座標的值小於右邊，而頂端小於底部。 例如，左上角的 (10、10) 和右下角 (20、20) 定義正規化的矩形，但 (10 的左上角)  () ，10定義非正規化的矩形。 如果矩形未正規化，許多成員函式 `CRect` 可能會傳回不正確的結果。  (請參閱 [CRect：： NormalizeRect](#normalizerect) ，以取得這些函式的清單 ) 。在呼叫需要標準化矩形的函式之前，您可以呼叫函式來正規化非正規化 `NormalizeRect` 的矩形。

使用 `CRect` [cdc：:D Ptolp](../../mfc/reference/cdc-class.md#dptolp) 和 [cdc：： LPtoDP](../../mfc/reference/cdc-class.md#lptodp) 成員函式來處理時，請特別小心。 如果顯示內容的對應模式是因為 y 範圍是負數， `MM_LOENGLISH` 則 `CDC::DPtoLP` 會將轉換成， `CRect` 使其頂端大於底部。 然後，等函式 `Height` `Size` 會針對已轉換的高度傳回負值 `CRect` ，而且矩形將不會正規化。

使用多載 `CRect` 運算子時，第一個運算元必須是 `CRect` ; 第二個運算元可以是 [RECT](/windows/win32/api/windef/ns-windef-rect) 結構或 `CRect` 物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagRECT`

`CRect`

## <a name="requirements"></a>需求

**標頭：** atltypes。h

## <a name="crectbottomright"></a><a name="bottomright"></a> CRect：： BottomRight

座標會傳回做為所包含之 [CPoint](cpoint-class.md) 物件的參考 `CRect` 。

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>傳回值

矩形右下角的座標。

### <a name="remarks"></a>備註

您可以使用這個函數來取得或設定矩形的右下角。 在指派運算子的左側使用此函數來設定角落。

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

## <a name="crectcenterpoint"></a><a name="centerpoint"></a> CRect：： CenterPoint

藉 `CRect` 由新增左邊和右邊的值並除以兩個值來計算的 centerpoint，然後新增頂端和下值並除以二。

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>傳回值

`CPoint`Centerpoint 的物件 `CRect` 。

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

## <a name="crectcopyrect"></a><a name="copyrect"></a> CRect：： CopyRect

將 `lpSrcRect` 矩形複製到 `CRect` 。

```cpp
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>參數

*lpSrcRect*<br/>
指向要複製的 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構或 `CRect` 物件。

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

## <a name="crectcrect"></a><a name="crect"></a> CRect：： CRect

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
指定的左邊位置 `CRect` 。

*t*<br/>
指定的頂端 `CRect` 。

*r*<br/>
指定的正確位置 `CRect` 。

*b*<br/>
指定的底部 `CRect` 。

*>srcrect*<br/>
參考具有座標的 [RECT](/windows/win32/api/windef/ns-windef-rect) 結構 `CRect` 。

*lpSrcRect*<br/>
指向 `RECT` 結構，其座標為 `CRect` 。

*點*<br/>
指定要建立之矩形的起點。 相對於左上角。

*size*<br/>
指定從左上角到要建立之矩形右下角的位移。

*topLeft*<br/>
指定左上角的位置 `CRect` 。

*bottomRight*<br/>
指定右下角的位置 `CRect` 。

### <a name="remarks"></a>備註

如果未指定任何引數，則、、 `left` `top` `right` 和 `bottom` 成員都會設定為0。

`CRect` (`const RECT&`) 和 () 的函式會 `CRect` `LPCRECT` 執行[CopyRect](#copyrect)。 其他的函式會直接初始化物件的成員變數。

### <a name="example"></a>範例

```cpp
// default constructor is equivalent to CRect(0, 0, 0, 0)
CRect emptyRect;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT structure
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

## <a name="crectdeflaterect"></a><a name="deflaterect"></a> CRect：:D eflateRect

`DeflateRect` 將 `CRect` 其邊移至其中心來「洩氣」。

```cpp
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
指定要 deflate 左右兩側的單位數目 `CRect` 。

*y*<br/>
指定要 deflate 其頂端和底部的單位數 `CRect` 。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)或[CSize](csize-class.md) ，指定要 deflate 的單位數 `CRect` 。 `cx`值會指定要 deflate 左邊和右邊的單位數，而 `cy` 值會指定要 deflate 頂端和底部的單位數。

*lpRect*<br/>
指向 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構或，以 `CRect` 指定要 deflate 每一側的單位數。

*l*<br/>
指定要 deflate 左側的單位數目 `CRect` 。

*t*<br/>
指定要 deflate 頂端的單位數目 `CRect` 。

*r*<br/>
指定要 deflate 右邊的單位數目 `CRect` 。

*b*<br/>
指定要 deflate 其底部的單位數 `CRect` 。

### <a name="remarks"></a>備註

若要這樣做，請 `DeflateRect` 將單位新增至左方和頂端，並從右邊和底部減去單位。 的參數為帶正負號的 `DeflateRect` 值; 正值 deflate `CRect` 和負值會將它擴充。

前兩個多載會 deflate 這兩個相反的邊， `CRect` 使其總寬度減少兩倍 *x* (或 `cx`) ，而其總高度會減少兩倍的 *y* (或 `cy`) 。 另外兩個多載 deflate 每一側獨立于其他多載 `CRect` 。

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

## <a name="crectequalrect"></a><a name="equalrect"></a> CRect：： EqualRect

判斷是否 `CRect` 等於指定的矩形。

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect) `CRect` 包含矩形左上角和右下角座標的矩形結構或物件。

### <a name="return-value"></a>傳回值

如果兩個矩形的頂端、左、下和右邊的值相同，則為非零值;否則為0。

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

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

## <a name="crectheight"></a><a name="height"></a> CRect：： Height

藉 `CRect` 由從底部值減去 top 值來計算的高度。

```
int Height() const throw();
```

### <a name="return-value"></a>傳回值

的高度 `CRect` 。

### <a name="remarks"></a>備註

產生的值可能是負數。

> [!NOTE]
> 矩形必須正規化，否則此函數可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a> CRect：： InflateRect

`InflateRect` 擴大 `CRect` ，將其邊移離其中心。

```cpp
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
指定要擴大左右側邊的單位數目 `CRect` 。

*y*<br/>
指定要擴大頂端和底部的單位數 `CRect` 。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)或[CSize](csize-class.md) ，指定要擴充的單位數目 `CRect` 。 `cx`值會指定要向左和右邊擴充的單位數目，而值則是 `cy` 指定要擴大的單位數目。

*lpRect*<br/>
指向 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構或，以 `CRect` 指定要擴充每一端的單位數。

*l*<br/>
指定要擴充左邊的單位數目 `CRect` 。

*t*<br/>
指定要擴大頂端的單位數 `CRect` 。

*r*<br/>
指定要向右擴充的單位數目 `CRect` 。

*b*<br/>
指定要向下擴充的單位數目 `CRect` 。

### <a name="remarks"></a>備註

若要這樣做，請 `InflateRect` 從左邊和頂端減去單位，並將單位新增至右側和底部。 的參數為帶正負號的 `InflateRect` 值; 正值擴充 `CRect` 和負數值 deflate 它。

前兩個多載會將這兩個相反的邊成對， `CRect` 使其總寬度增加兩倍 *x* (或 `cx`) ，而其總高度會增加兩倍的 *y* (或 `cy`) 。 另外兩個多載會擴充彼此獨立的每一側 `CRect` 。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a> CRect：： IntersectRect

使 `CRect` 等於兩個現有矩形的交集。

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>參數

*lpRect1*<br/>
指向包含來源矩形的 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構或 `CRect` 物件。

*lpRect2*<br/>
指向 `RECT` `CRect` 包含來源矩形的結構或物件。

### <a name="return-value"></a>傳回值

如果交集不是空的，則為非零;如果交集是空的，則為0。

### <a name="remarks"></a>備註

交集是兩個現有矩形中包含的最大矩形。

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

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

## <a name="crectisrectempty"></a><a name="isrectempty"></a> CRect：： IsRectEmpty

判斷是否 `CRect` 為空的。

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果是空的，則為非零，如果不是空的則為 `CRect` 0 `CRect` 。

### <a name="remarks"></a>備註

如果寬度和/或高度為0或負數，矩形就會是空的。 與不同 `IsRectNull` ，它會決定矩形的所有座標是否為零。

> [!NOTE]
> 矩形必須正規化，否則此函數可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a> CRect：： IsRectNull

判斷的上、左、下和右值是否 `CRect` 全都等於0。

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>傳回值

非零 `CRect` 值（如果是 top、left、底端和 right 值）全都等於0，否則為0。

### <a name="remarks"></a>備註

與不同 `IsRectEmpty` ，可判斷矩形是否為空白。

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

## <a name="crectmovetox"></a><a name="movetox"></a> CRect：： MoveToX

呼叫此函式可將矩形移至 *x*所指定的絕對 x 座標。

```cpp
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

## <a name="crectmovetoxy"></a><a name="movetoxy"></a> CRect：： MoveToXY

呼叫此函式可將矩形移至指定的絕對 x 和 y 座標。

```cpp
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
矩形左上角的絕對 x 座標。

*y*<br/>
矩形左上角的絕對 y 座標。

*點*<br/>
`POINT`結構，指定矩形的絕對左上角。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a> CRect：： MoveToY

呼叫此函式可將矩形移至 *y*所指定的絕對 y 座標。

```cpp
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

## <a name="crectnormalizerect"></a><a name="normalizerect"></a> CRect：： NormalizeRect

正規化， `CRect` 讓高度和寬度都是正數。

```cpp
void NormalizeRect() throw();
```

### <a name="remarks"></a>備註

矩形會針對第四象限定位進行正規化，而 Windows 通常會使用它來做為座標。 `NormalizeRect` 比較頂端和下值，如果頂端大於底部，則將其交換。 同樣地，如果左邊大於右邊，則會交換左邊和右邊的值。 當處理不同的對應模式和反向矩形時，此函式很有用。

> [!NOTE]
> 下列成員函式 `CRect` 需要標準化的矩形，才能正常運作： [Height](#height)、 [Width](#width)、 [Size](#size)、 [IsRectEmpty](#isrectempty)、 [>ptinrect](#ptinrect)、 [EqualRect](#equalrect)、 [UnionRect](#unionrect)、 [IntersectRect](#intersectrect)、 [SubtractRect](#subtractrect)、 [operator = =](#operator_eq_eq)、 [operator！ =](#operator_neq)、 [operator &#124;](#operator_or)、 [operator &#124;=](#operator_or_eq)、 [operator &](#operator_amp)和 [運算子 &=](#operator_amp_eq)。

### <a name="example"></a>範例

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a> CRect：： OffsetRect

`CRect`依指定的位移移動。

```cpp
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
指定要向左或向右移動的數量。 它必須為負數，才能往左移動。

*y*<br/>
指定要向上或向下移動的數量。 必須為負數才能向上移動。

*點*<br/>
包含指定要移動之維度的 [點](/windows/win32/api/windef/ns-windef-point) 結構或 [CPoint](cpoint-class.md) 物件。

*size*<br/>
包含 [大小](/windows/win32/api/windef/ns-windef-size) 結構或 [CSize](csize-class.md) 物件，指定要移動的維度。

### <a name="remarks"></a>備註

沿著 `CRect` X 軸和*y*單位沿著 y 軸移動*x*單位。 *X*和*y*參數是帶正負號的值，因此 `CRect` 可以向左或向右和向上或向下移動。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a> CRect：： operator LPCRECT 會將轉換 `CRect` 為 [LPCRECT](../../mfc/reference/data-types-mfc.md)。

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>備註

當您使用此函式時，您不需要 (的位址 **&**) 操作員。 當您將物件傳遞給預期的函式時，將會自動使用這個運算子 `CRect` `LPCRECT` 。

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a> CRect：： operator LPRECT

將轉換 `CRect` 成 [LPRECT](../../mfc/reference/data-types-mfc.md)。

```
operator LPRECT() throw();
```

### <a name="remarks"></a>備註

當您使用此函式時，您不需要 (的位址 **&**) 操作員。 當您將物件傳遞給預期的函式時，將會自動使用這個運算子 `CRect` `LPRECT` 。

### <a name="example"></a>範例

請參閱 [CRect：： OPERATOR LPCRECT](#operator_lpcrect)的範例。

## <a name="crectoperator-"></a><a name="operator_eq"></a> CRect：： operator =

將 *>srcrect* 指派給 `CRect` 。

```cpp
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>參數

*>srcrect*<br/>
參考來源矩形。 可以是 [RECT](/windows/win32/api/windef/ns-windef-rect) 或 `CRect` 。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a> CRect：： operator = =

藉 `rect` `CRect` 由比較左上角和右下角的座標，判斷是否等於。

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>參數

*矩形*<br/>
參考來源矩形。 可以是 [RECT](/windows/win32/api/windef/ns-windef-rect) 或 `CRect` 。

### <a name="return-value"></a>傳回值

如果相等則為非零。否則為0。

### <a name="remarks"></a>備註

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

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

## <a name="crectoperator-"></a><a name="operator_neq"></a> CRect：： operator！ =

藉*rect* `CRect` 由比較左上角和右下角的座標，判斷矩形是否不等於。

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>參數

*矩形*<br/>
參考來源矩形。 可以是 [RECT](/windows/win32/api/windef/ns-windef-rect) 或 `CRect` 。

### <a name="return-value"></a>傳回值

非零（如果不相等）;否則為0。

### <a name="remarks"></a>備註

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

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

## <a name="crectoperator-"></a><a name="operator_add_eq"></a> CRect：： operator + =

前兩個多載會 `CRect` 依指定的位移移動。

```cpp
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>參數

*點*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件，指定要移動矩形的單位數目。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件，指定要移動矩形的單位數目。

*lpRect*<br/>
指向 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構或 `CRect` 物件，其中包含要擴充每一側的單位數 `CRect` 。

### <a name="remarks"></a>備註

參數的 *x* 和 *y* (或 `cx` 和 `cy`) 值會加入至 `CRect` 。

第三個多載會 `CRect` 依參數的每個成員中指定的單位數擴大。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a> CRect：： operator-=

前兩個多載會 `CRect` 依指定的位移移動。

```cpp
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>參數

*點*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件，指定要移動矩形的單位數目。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件，指定要移動矩形的單位數目。

*lpRect*<br/>
指向 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構或 `CRect` 物件，其中包含要 deflate 其每一側的單位數 `CRect` 。

### <a name="remarks"></a>備註

參數的 *x* 和 *y* (或 `cx` 和 `cy`) 值會從中減去 `CRect` 。

第三個多載會 `CRect` 依參數的每個成員中指定的單位數「洩氣」。 請注意，這個多載函式類似于 [DeflateRect](#deflaterect)。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a> CRect：： operator &amp;=

設定 `CRect` 等於和的交集 `CRect` `rect` 。

```cpp
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>參數

*矩形*<br/>
包含 [矩形](/windows/win32/api/windef/ns-windef-rect) 或 `CRect` 。

### <a name="remarks"></a>備註

交集是兩個矩形中包含的最大矩形。

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

### <a name="example"></a>範例

請參閱 [CRect：： IntersectRect](#intersectrect)的範例。

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a> CRect：： operator &#124;=

設定 `CRect` 等於和的聯集 `CRect` `rect` 。

```cpp
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>參數

*矩形*<br/>
包含 `CRect` 或 [RECT](/windows/win32/api/windef/ns-windef-rect)。

### <a name="remarks"></a>備註

聯集是包含這兩個來源矩形的最小矩形。

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a> CRect：： operator +

前兩個多載 `CRect` 會傳回物件，該物件等於以 `CRect` 指定的位移來取代。

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件，指定要移動傳回值的單位數。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件，指定要移動傳回值的單位數。

*lpRect*<br/>
指向 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構或 `CRect` 物件，其中包含要擴充傳回值每一側的單位數。

### <a name="return-value"></a>傳回值

`CRect` `CRect` 以參數中指定的單位數移動或因而誇大所產生的。

### <a name="remarks"></a>備註

參數的 *x* 和 *y* (或 `cx` 和 `cy`) 參數會加入至 `CRect` 的位置。

第三個多載會傳回新 `CRect` 的，其等於 `CRect` 在參數的每個成員中指定的單位數擴大。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a> CRect：： operator-

前兩個多載 `CRect` 會傳回物件，該物件等於以 `CRect` 指定的位移來取代。

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或 `CPoint` 物件，指定要移動傳回值的單位數。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或 `CSize` 物件，指定要移動傳回值的單位數。

*lpRect*<br/>
指向 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構或 `CRect` 物件，其中包含要 deflate 傳回值每一側的單位數。

### <a name="return-value"></a>傳回值

`CRect` `CRect` 以參數中指定的單位數移動或 deflating 所產生的。

### <a name="remarks"></a>備註

參數的 *x* 和 *y* (或 `cx` 和 `cy`) 參數會從 `CRect` 的位置減去。

第三個多載會傳回新 `CRect` 的，其等於 `CRect` 縮小的每個參數成員中指定的單位數。 請注意，這個多載函式（例如 [DeflateRect](#deflaterect)，而非 [SubtractRect](#subtractrect)）。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a> CRect：： operator &amp;

傳回， `CRect` 它是 `CRect` 和 *rect2*的交集。

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>參數

*rect2*<br/>
包含 [矩形](/windows/win32/api/windef/ns-windef-rect) 或 `CRect` 。

### <a name="return-value"></a>傳回值

， `CRect` 它是 `CRect` 和 *rect2*的交集。

### <a name="remarks"></a>備註

交集是兩個矩形中包含的最大矩形。

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a> CRect：： operator &#124;

傳回， `CRect` 它是 `CRect` 和 *rect2*的聯集。

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>參數

*rect2*<br/>
包含 [矩形](/windows/win32/api/windef/ns-windef-rect) 或 `CRect` 。

### <a name="return-value"></a>傳回值

， `CRect` 它是 `CRect` 和 *rect2*的聯集。

### <a name="remarks"></a>備註

聯集是包含這兩個矩形的最小矩形。

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a> CRect：:P tInRect

判斷指定的點是否位於內部 `CRect` 。

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
包含 [點](/windows/win32/api/windef/ns-windef-point) 結構或 [CPoint](cpoint-class.md) 物件。

### <a name="return-value"></a>傳回值

如果點位於零，則為非零， `CRect` 否則為0。

### <a name="remarks"></a>備註

如果點位於 `CRect` 左邊或上方，或在全部四邊內，則會在其中。 右側或底部的某個點位於外部 `CRect` 。

> [!NOTE]
> 矩形必須正規化，否則此函數可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

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

## <a name="crectsetrect"></a><a name="setrect"></a> CRect：： SetRect

將的維度設定 `CRect` 為指定的座標。

```cpp
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

## <a name="crectsetrectempty"></a><a name="setrectempty"></a> CRect：： SetRectEmpty

`CRect`將所有座標設定為零，以建立 null 矩形。

```cpp
void SetRectEmpty() throw();
```

### <a name="example"></a>範例

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

## <a name="crectsize"></a><a name="size"></a> CRect：： SIZE

傳回 `cx` 值的和 `cy` 成員包含的高度和寬度 `CRect` 。

```
CSize Size() const throw();
```

### <a name="return-value"></a>傳回值

[CSize](csize-class.md)物件，其中包含的大小 `CRect` 。

### <a name="remarks"></a>備註

高度或寬度可以是負數。

> [!NOTE]
> 矩形必須正規化，否則此函數可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a> CRect：： SubtractRect

使的維度等於的 `CRect` 減法 `lpRectSrc2` `lpRectSrc1` 。

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>參數

*lpRectSrc1*<br/>
指向要從中減去矩形的 [矩形結構或](/windows/win32/api/windef/ns-windef-rect) `CRect` 物件。

*lpRectSrc2*<br/>
指向 `RECT` `CRect` 要從 *lpRectSrc1* 參數所指向之矩形中減去的結構或物件。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

減法是最小的矩形，包含 *lpRectScr1* 中不在 *lpRectScr1* 和 *lpRectScr2*交集處的所有點。

如果*lpRectSrc2*指定的矩形未完全與*lpRectSrc1*中指定的矩形（至少一個 x 或 y 方向）重迭，則*lpRectSrc1*所指定的矩形將不會變更。

例如，如果 *lpRectSrc1* 是 (10、10、100100) ，而 *lpRectSrc2* (50、50、150150) ，則當函式傳回時， *lpRectSrc1* 所指向的矩形會維持不變。 如果 *lpRectSrc1* (10、10、100100) 和 *lpRectSrc2* (50、10、150150) ，則 *lpRectSrc1* 所指向的矩形會在函式傳回時包含 (10、10、50100) 的座標。

`SubtractRect` 與 [運算子](#operator_-) 或 [運算子-=](#operator_-_eq)不相同。 這兩個運算子都不會呼叫 `SubtractRect` 。

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

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

## <a name="crecttopleft"></a><a name="topleft"></a> CRect：：下拉式功能表

座標會傳回做為所包含之 [CPoint](cpoint-class.md) 物件的參考 `CRect` 。

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>傳回值

矩形左上角的座標。

### <a name="remarks"></a>備註

您可以使用此函式來取得或設定矩形的左上角。 在指派運算子的左側使用此函數來設定角落。

### <a name="example"></a>範例

請參閱 [CRect：： CenterPoint](#centerpoint)的範例。

## <a name="crectunionrect"></a><a name="unionrect"></a> CRect：： UnionRect

使維度 `CRect` 等於兩個來源矩形的聯集。

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>參數

*lpRect1*<br/>
指向包含來源矩形的 [矩形](/windows/win32/api/windef/ns-windef-rect) 或 `CRect` 。

*lpRect2*<br/>
指向 `RECT` `CRect` 包含來源矩形的或。

### <a name="return-value"></a>傳回值

如果聯集不是空的，則為非零;如果聯集是空的，則為0。

### <a name="remarks"></a>備註

聯集是包含這兩個來源矩形的最小矩形。

Windows 會忽略空矩形的維度;也就是沒有高度或沒有寬度的矩形。

> [!NOTE]
> 這兩個矩形都必須正規化，否則此函式可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a> CRect：： Width

藉 `CRect` 由從右邊的值減去左邊的值來計算的寬度。

```
int Width() const throw();
```

### <a name="return-value"></a>傳回值

的寬度 `CRect` 。

### <a name="remarks"></a>備註

寬度可以是負數。

> [!NOTE]
> 矩形必須正規化，否則此函數可能會失敗。 呼叫此函式之前，您可以呼叫 [NormalizeRect](#normalizerect) 來將矩形標準化。

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
[矩形](/windows/win32/api/windef/ns-windef-rect)
