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
ms.openlocfilehash: c59ed587e2c8e51f5c08a026a7ee0b9d0af25168
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317709"
---
# <a name="crect-class"></a>CRect 類別

類似於 Windows [RECT](/windows/win32/api/windef/ns-windef-rect)結構。

## <a name="syntax"></a>語法

```
class CRect : public tagRECT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRect:CRect](#crect)|建構 `CRect` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRect::右下](#bottomright)|傳回的右下角`CRect`點 。|
|[CRect::中心點](#centerpoint)|返回的中心`CRect`點。|
|[CRect::複製](#copyrect)|將來源矩形的大小複製到`CRect`。|
|[CRect::D](#deflaterect)|減小的`CRect`寬度和高度。|
|[CRect::平等](#equalrect)|確定是否`CRect`等於給定的矩形。|
|[CRect::高度](#height)|計算高度`CRect`。|
|[CRect::充氣](#inflaterect)|增加的`CRect`寬度和高度。|
|[CRect::相交雷](#intersectrect)|設置`CRect`等於兩個矩形的交集。|
|[CRect::isrectEmpty](#isrectempty)|確定是否`CRect`為空。 `CRect`如果寬度和/或高度為 0,則為空。|
|[CRect::IsrectNull](#isrectnull)|確定`top`、 `bottom``left`、`right`和成員變數是否都等於 0。|
|[Crect::移動](#movetox)|移動到`CRect`指定的 x 座標。|
|[Crect::移動](#movetoxy)|移動到`CRect`指定的 x 座標和 y 座標。|
|[Crect::移動玩具](#movetoy)|移動到`CRect`指定的 y 座標。|
|[CRect::規範化Rect](#normalizerect)|標準化的高度`CRect`和寬度。|
|[CRect::偏移重](#offsetrect)|按`CRect`指定的偏移量移動。|
|[Crect::P](#ptinrect)|確定指定的點是否位於中`CRect`。|
|[CRect::SetRect](#setrect)|設置的`CRect`尺寸。|
|[CRect::設定重新清空](#setrectempty)|設置`CRect`為空矩形(所有座標等於 0)。|
|[CRect::大小](#size)|計算的大小`CRect`。|
|[CRect::減法](#subtractrect)|從另一個矩形中減去一個矩形。|
|[CRect:左上](#topleft)|傳回左上方 。`CRect`|
|[CRect::聯合](#unionrect)|設置`CRect`等於兩個矩形的合併。|
|[CRect::寬度](#width)|計算的`CRect`寬度。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRect::運算符 -](#operator_-)|從`CRect`中減到定的偏移或放`CRect`空並傳回產生的`CRect`。|
|[CRect::操作員LPCRECT](#operator_lpcrect)|將 `CRect` 轉換成 `LPCRECT`。|
|[CRect::操作員 LPRECT](#operator_lprect)|將 `CRect` 轉換成 `LPRECT`。|
|[CRect::操作員!*](#operator_neq)|確定是否`CRect`不等於矩形。|
|[CRect::運算子&amp;](#operator_amp)|建立與`CRect`的交集,並傳回產生`CRect`的 。|
|[CRect::運算子&amp;=](#operator_amp_eq)|設置`CRect`等於和`CRect`的 交集和矩形。|
|[CRect::操作員&#124;](#operator_or)|建立與`CRect`的聯合矩形,並傳回產生`CRect`的 。|
|[CRect::操作員&#124;|](#operator_or_eq)|設置`CRect`等於和的`CRect`合併。|
|[CRect::運算符 |](#operator_add)|將給定位移量到`CRect`或膨脹`CRect`並傳回產生`CRect`的 。|
|[CRect::操作員 |](#operator_add_eq)|將指定的偏移量到`CRect`或膨脹 。 `CRect`|
|[CRect::運算符 |](#operator_eq)|將矩形的大小複製到`CRect`。|
|[CRect::運算符 -*](#operator_-_eq)|從`CRect`中減到指定的偏移或放空`CRect`。|
|[CRect::運算符 |](#operator_eq_eq)|確定是否`CRect`等於矩形。|

## <a name="remarks"></a>備註

`CRect`還包括用於操作`CRect`物件和`RECT`Windows 結構的成員函數。

物件`CRect``RECT`可以在 結構的任何位置作為函數參數`LPCRECT`傳遞`LPRECT`, 也可以傳遞 。

> [!NOTE]
> 此類派生自結構`tagRECT`。 (名稱`tagRECT`是`RECT`結構不太常用的名稱。`top``right`這意味著`bottom`結構的數據成員 (、 、 和`CRect`) 是 可訪問的數據成員。`left``RECT`

包含`CRect`定義矩形的左上角和右下角點的成員變數。

指定`CRect`時,必須小心構造它,以便將其規範化 — 換句話說,左座標的值小於右側,頂部小於底部。 例如,左上角(10,10)和右下角(20,20)定義一個規範化矩形,但左上角 (20,20) 和右下角 (10,10) 定義非規範化矩形。 如果矩形未規範化,許多`CRect`成員函數可能會返回不正確的結果。 (請參閱[CRect::規範化 Rect,](#normalizerect)瞭解這些函數的清單。在調用需要規範化矩形的函數之前,可以通過調`NormalizeRect`用 函數來規範化非規範化矩形。

使用`CRect`[CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp)和[CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp)成員函數操作 時,應謹慎。 如果顯示上下文的映射模式使 y 範圍為負,如`MM_LOENGLISH`在`CDC::DPtoLP`中`CRect`,則將轉換 , 以便其頂部大於底部。 等`Height`函`Size`數 隨後將`CRect`返回轉換 高度的負值,矩形將非規範化。

使用重載`CRect`運算子時,第一個`CRect`操作數必須是 ;第二個可以是[RECT](/windows/win32/api/windef/ns-windef-rect)`CRect`結構或 物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagRECT`

`CRect`

## <a name="requirements"></a>需求

**標題:** atltype.h

## <a name="crectbottomright"></a><a name="bottomright"></a>CRect::右下

座標將為對中包含的[CPoint](cpoint-class.md)物件的`CRect`參考傳回 。

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>傳回值

矩形右下角的座標。

### <a name="remarks"></a>備註

您可以使用此函數獲取或設置矩形的右下角。 使用賦值運算符左側的函數設置角。

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

## <a name="crectcenterpoint"></a><a name="centerpoint"></a>CRect::中心點

通過添加左值和右`CRect`值並將之除以 2 以及添加頂部和底部值以及除以 2 來計算的中心點。

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>傳回值

作為`CPoint`的中心點的物件`CRect`。

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

## <a name="crectcopyrect"></a><a name="copyrect"></a>CRect::複製

將`lpSrcRect`矩形複製`CRect`到 中。

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>參數

*lpSrcrect*<br/>
指向要複製的[RECT](/windows/win32/api/windef/ns-windef-rect)`CRect`結構或 物件。

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

## <a name="crectcrect"></a><a name="crect"></a>CRect:CRect

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

*我*<br/>
指定`CRect`的 左位置。

*t*<br/>
指定的頂部`CRect`。

*R*<br/>
指定的正確位置`CRect`。

*B*<br/>
指定的底部`CRect`。

*斯克拉特*<br/>
指具有座標的`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*lpSrcrect*<br/>
指向`RECT`一個座標`CRect`結構 。

*點*<br/>
指定要建構的矩形的原點。 對應於左上角。

*大小*<br/>
指定要建構的矩形從左上角到右下角的位移。

*topLeft*<br/>
指定左上方位置`CRect`。

*bottomRight*<br/>
指定的右下角位置`CRect`。

### <a name="remarks"></a>備註

如果未`left`給出參數,則不會初始化`top``right`、`bottom`和成員。

`CRect`(`const RECT&``CRect`)`LPCRECT`與 ( ) 建構函數執行[複寫重新 。](#copyrect) 其他構造函數直接初始化對象的成員變數。

### <a name="example"></a>範例

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

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

## <a name="crectdeflaterect"></a><a name="deflaterect"></a>CRect::D

`DeflateRect``CRect`通過移動其兩側向其中心。

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>參數

*X.*<br/>
指定要放氣 的左側和右側的`CRect`單位 數。

*Y*<br/>
指定要放氣 的上部和下部的`CRect`單位 數。

*大小*<br/>
指定要放放`CRect`的單位數[的大小或](/windows/win32/api/windef/ns-windef-size)[大小。](csize-class.md) 該`cx`值指定用於放氣左右兩側的單位數`cy`, 該值指定用於放氣頂部和底部的單位數。

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)`CRect`結構或 指定要放氣每側的單位數。

*我*<br/>
指定要放氣 的左側的`CRect`單位 數。

*t*<br/>
指定要放氣 頂部的`CRect`單位 數。

*R*<br/>
指定要放氣 右側的`CRect`單位 數。

*B*<br/>
指定要放氣 的`CRect`單位 數。

### <a name="remarks"></a>備註

為此,在`DeflateRect`左側和頂部添加單位,並從右側和底部減去單位。 的`DeflateRect`參數是已簽名的值;正值放空`CRect`,負值膨脹。

前兩個重載將兩對相反的兩對`CRect`放氣,使其總寬度減少 2 倍*x* `cx`(或 ), 其總高度減少 2`cy`倍*y* (或 )。 其他兩個重載使每一側`CRect`都獨立於其他側進行放氣。

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

## <a name="crectequalrect"></a><a name="equalrect"></a>CRect::平等

確定是否`CRect`等於給定的矩形。

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向包含矩形的左上角`CRect`和右下角座標的[RECT](/windows/win32/api/windef/ns-windef-rect)結構或物件。

### <a name="return-value"></a>傳回值

如果兩個矩形具有相同的頂部、左側、底部和右側值,則非零;否則 0。

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

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

## <a name="crectheight"></a><a name="height"></a>CRect::高度

通過從底部值中`CRect`減去最高值來計算 的高度。

```
int Height() const throw();
```

### <a name="return-value"></a>傳回值

的高度`CRect`。

### <a name="remarks"></a>備註

生成的值可以是負數。

> [!NOTE]
> 矩形必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

### <a name="example"></a>範例

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a>CRect::充氣

`InflateRect`通過將其側面`CRect`從中心移開而膨脹。

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>參數

*X.*<br/>
指定要膨脹 的左側和右側的`CRect`單位 數。

*Y*<br/>
指定要膨脹 的上部和底部的`CRect`單位 數。

*大小*<br/>
指定要膨脹的單位數的[SIZE](/windows/win32/api/windef/ns-windef-size)或`CRect`[CSize。](csize-class.md) 該`cx`值指定要膨脹左右兩側的單位數`cy`, 該值指定要膨脹頂部和底部的單位數。

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)`CRect`結構或 指定要膨脹每側的單位數。

*我*<br/>
指定要膨脹 的`CRect`單位 數。

*t*<br/>
指定要膨脹 的`CRect`單位 數。

*R*<br/>
指定要膨脹 的右側的`CRect`單位 數。

*B*<br/>
指定要膨脹 的`CRect`單位 數。

### <a name="remarks"></a>備註

為此,`InflateRect`從左側和頂部減去單位,並在右側和底部添加單位。 的`InflateRect`參數是已簽名的值;正值膨脹`CRect`,負值將其放氣。

前兩個重載將兩對相反的兩對膨脹,`CRect`使其總寬度增加 2 倍`cx`*x* (或 ),`cy`其總高度增加 2*y*倍 y (或 )。 其他兩個重載使每一側`CRect`相互膨脹,而與其他重載無關。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a>CRect::相交雷

使等於`CRect`兩個現有矩形的交集。

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>參數

*lpRect1*<br/>
指向包含源矩形的[RECT](/windows/win32/api/windef/ns-windef-rect)`CRect`結構或 物件。

*lpRect2*<br/>
指向包含源`RECT`矩形的`CRect`結構 或物件。

### <a name="return-value"></a>傳回值

如果交點不為空,則非零;如果交點為空,則為 0。

### <a name="remarks"></a>備註

交集是兩個現有矩形中包含的最大矩形。

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

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

## <a name="crectisrectempty"></a><a name="isrectempty"></a>CRect::isrectEmpty

確定是否`CRect`為空。

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>傳回值

非零(`CRect`如果為空);0,`CRect`如果不是空。

### <a name="remarks"></a>備註

如果寬度和/或高度為 0 或負,則矩形為空。 與`IsRectNull`不同,後者確定矩形的所有座標是否為零。

> [!NOTE]
> 矩形必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

### <a name="example"></a>範例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a>CRect::IsrectNull

確定的`CRect`上值、左值、下值和右值是否都等於 0。

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>傳回值

如果"的頂部`CRect`、左側、底部和右側"值都等於 0,則非零;如果"上、左、下和右"值均等於 0;如果"上、左、下和右"值均等於 0,則為非零。否則 0。

### <a name="remarks"></a>備註

與`IsRectEmpty`不同,後者確定矩形是否為空。

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

## <a name="crectmovetox"></a><a name="movetox"></a>Crect::移動

呼叫此函數以將矩形移動到*x*指定的絕對 x 座標。

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>參數

*X.*<br/>
矩形左上角的絕對 x 座標。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a>Crect::移動

呼叫此函數以將矩形移動到指定的絕對 x 座標和 y 座標。

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>參數

*X.*<br/>
矩形左上角的絕對 x 座標。

*Y*<br/>
矩形左上角的絕對 y 座標。

*點*<br/>
指定`POINT`矩形的絕對左上角的結構。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a>Crect::移動玩具

呼叫此函數以將矩形移動到*y*指定的絕對 y 座標。

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>參數

*Y*<br/>
矩形左上角的絕對 y 座標。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a>CRect::規範化Rect

規範化`CRect`,以便高度和寬度均為正數。

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>備註

矩形規範化為第四象限定位,Windows 通常用於座標。 `NormalizeRect`比較頂部和底部值,如果頂部大於底部,則交換它們。 同樣,如果左側大於右側,則交換左側和右側值。 在處理不同的映射模式和反轉矩形時,此功能非常有用。

> [!NOTE]
> 以下`CRect`成員函數需要規範化矩形才能正常工作:[高度](#height)、[寬度](#width)、[大小](#size)[、isrectEmpty、PtInRect、](#isrectempty)[相等重、](#equalrect)[聯合重整](#unionrect),[相交雷ct、](#intersectrect)[減法、](#subtractrect)[運算符 *、](#operator_eq_eq)[操作員 !*、](#operator_neq)[操作員&#124;、](#operator_or)[操作員&#124;、](#operator_or_eq)[操作員&](#operator_amp)和[運算符&=](#operator_amp_eq)。 [PtInRect](#ptinrect)

### <a name="example"></a>範例

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a>CRect::偏移重

按`CRect`指定的偏移量移動。

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>參數

*X.*<br/>
指定向左或向右移動的金額。 向左移動必須為負數。

*Y*<br/>
指定向上或向下移動的金額。 向上移動必須為負數。

*點*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件,指定要移動的兩個維度。

*大小*<br/>
包含指定要移動的兩個維度[的 SIZE](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件。

### <a name="remarks"></a>備註

沿`CRect`x 軸和*y*單位沿 y 軸移動*x*單位。 *x*和*y*參數是`CRect`簽名值, 因此可以向左或向右移動,向上或向下移動。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a>CRect::運算子 LPCRECT`CRect`將 轉換為[LPCRECT](../../mfc/reference/data-types-mfc.md)。

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>備註

使用此函數時,不需要位址**&**() 運算子。 當您將`CRect`物件傳遞給需要`LPCRECT`的函數時,將自動使用此運算符。

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a>CRect::操作員 LPRECT

轉換為`CRect` [LPRECT](../../mfc/reference/data-types-mfc.md)。

```
operator LPRECT() throw();
```

### <a name="remarks"></a>備註

使用此函數時,不需要位址**&**() 運算子。 當您將`CRect`物件傳遞給需要`LPRECT`的函數時,將自動使用此運算符。

### <a name="example"></a>範例

請參閱[CRect::運算符 LPCRECT](#operator_lpcrect)的範例。

## <a name="crectoperator-"></a><a name="operator_eq"></a>CRect::運算符 |

將*srcRect*`CRect`分配給 。

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>參數

*斯克拉特*<br/>
引用源矩形。 可以是[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="example"></a>範例

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a>CRect::運算符 |

通過比較`rect`其左上角和右下角角的座標,確定是否等於`CRect`。

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>參數

*矩形*<br/>
引用源矩形。 可以是[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>傳回值

等於非零;否則 0。

### <a name="remarks"></a>備註

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

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

## <a name="crectoperator-"></a><a name="operator_neq"></a>CRect::操作員!*

通過比較右上角和右下角的座標,確定*整流*是否等`CRect`於。

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>參數

*矩形*<br/>
引用源矩形。 可以是[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>傳回值

非零,如果不是相等;否則 0。

### <a name="remarks"></a>備註

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

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

## <a name="crectoperator-"></a><a name="operator_add_eq"></a>CRect::操作員 |

前兩個重載按`CRect`指定的偏移量移動。

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>參數

*點*<br/>
指定要移動矩形的單位數的[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件。

*大小*<br/>
指定要移動矩形的單位數的[SIZE](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件。

*lpRect*<br/>
指向包含要膨脹的兩側的`CRect`單位數的`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)結構或物件。

### <a name="remarks"></a>備註

參數的*x*和*y* `cx` (`cy`或和 )`CRect`值將添加到中。

第三個過載按`CRect`參數的每個成員中指定的單位數膨脹。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a>CRect::運算符 -*

前兩個重載按`CRect`指定的偏移量移動。

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>參數

*點*<br/>
指定要移動矩形的單位數的[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件。

*大小*<br/>
指定要移動矩形的單位數的[SIZE](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件。

*lpRect*<br/>
指向包含要放氣 的`CRect`每 一側的單位`CRect`數的[RECT](/windows/win32/api/windef/ns-windef-rect)結構或物件。

### <a name="remarks"></a>備註

參數的*x*和*y* `cx` (`cy`或 和 )`CRect`值從 中減去。

第三個過載`CRect`按參數的每個成員中指定的單位數進行放量。 請注意,此重載函數類似於[DeflateRect](#deflaterect)。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a>CRect::運算子&amp;=

設置`CRect`等於和`rect`的`CRect`交集。

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>參數

*矩形*<br/>
包含[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="remarks"></a>備註

交集是兩個矩形中包含的最大矩形。

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

### <a name="example"></a>範例

請參閱[CRect::相交雷ct的範例](#intersectrect)。

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a>CRect::操作員&#124;|

集`CRect`等於和`rect`的`CRect`聯合。

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>參數

*矩形*<br/>
包含或`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)。

### <a name="remarks"></a>備註

聯合是包含兩個源矩形的最小矩形。

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a>CRect::運算符 |

前兩個重載返回一`CRect`個物件,該`CRect`物件 等於由指定的偏移量置換。

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
指定要移動返回值的單位數的[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件。

*大小*<br/>
指定要移動返回值的單位數的[SIZE](/windows/win32/api/windef/ns-windef-size)結構或[CSize](csize-class.md)物件。

*lpRect*<br/>
指向包含要膨脹返回值每`CRect`一側的單位數的[RECT](/windows/win32/api/windef/ns-windef-rect)結構或物件。

### <a name="return-value"></a>傳回值

由按參數中指定的單位數移動或膨脹`CRect`的結果`CRect`。

### <a name="remarks"></a>備註

參數的*x*和*y* `cx` (`cy`或 與 )`CRect`參數將新增到位置。

第三個重載返回`CRect`一個新值,`CRect`該新重載等於按參數的每個成員中指定的單位數膨脹。

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a>CRect::運算符 -

前兩個重載返回一`CRect`個物件,該`CRect`物件 等於由指定的偏移量置換。

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
指定[POINT](/windows/win32/api/windef/ns-windef-point)要移動`CPoint`返回 值的單位數的 POINT 結構或物件。

*大小*<br/>
指定[SIZE](/windows/win32/api/windef/ns-windef-size)要移動`CSize`返回 值的單位數的 SIZE 結構或物件。

*lpRect*<br/>
指向包含用於放氣返回值`CRect`每一側的單位數的[RECT](/windows/win32/api/windef/ns-windef-rect)結構或物件。

### <a name="return-value"></a>傳回值

由按參數中指定的單位數移動或消減`CRect`的結果`CRect`。

### <a name="remarks"></a>備註

參數的*x*和`cy`*y* `cx` (`CRect`或 和 ) 參數從 位置中減去。

第三個重載返回`CRect`一個新值,`CRect`該新重載等於按參數的每個成員中指定的單位數進行放氣。 請注意,此重載函數如[DeflateRect,](#deflaterect)而不是[減減 。](#subtractrect)

### <a name="example"></a>範例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a>CRect::運算子&amp;

傳`CRect`回`CRect`為與*rect2*的交集的 。

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>參數

*rect2*<br/>
包含[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>傳回值

A`CRect`是`CRect`和*rect2*的交集。

### <a name="remarks"></a>備註

交集是兩個矩形中包含的最大矩形。

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a>CRect::操作員&#124;

傳`CRect`回與的`CRect`聯合項目 *。*

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>參數

*rect2*<br/>
包含[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>傳回值

A`CRect`是`CRect`和*rect2*的合併。

### <a name="remarks"></a>備註

聯合是包含兩個矩形的最小矩形。

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a>Crect::P

確定指定的點是否位於中`CRect`。

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](cpoint-class.md)物件。

### <a name="return-value"></a>傳回值

如果點位於`CRect`中 ,則非零。否則 0。

### <a name="remarks"></a>備註

如果點位於左側`CRect`或頂部或位於所有四面內,則該點位於內。 右邊或底部的點位於`CRect`外部 。

> [!NOTE]
> 矩形必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

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

## <a name="crectsetrect"></a><a name="setrect"></a>CRect::SetRect

將`CRect`的尺寸設置到指定的座標。

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

## <a name="crectsetrectempty"></a><a name="setrectempty"></a>CRect::設定重新清空

通過將`CRect`所有座標設置為零,使矩形變為空矩形。

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

## <a name="crectsize"></a><a name="size"></a>CRect::大小

返回`cx`值`cy`和成員包含`CRect`的高度和寬度。

```
CSize Size() const throw();
```

### <a name="return-value"></a>傳回值

包含大小的[CSize](csize-class.md)物件`CRect`。

### <a name="remarks"></a>備註

高度或寬度可以是負數。

> [!NOTE]
> 矩形必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

### <a name="example"></a>範例

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a>CRect::減法

使的`CRect`尺寸等於從`lpRectSrc2``lpRectSrc1`的減法。

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>參數

*lpRectSrc1*<br/>
指向要從中減去矩形的`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)結構或物件。

*lprectSrc2*<br/>
指向要從`RECT``CRect` *lpRectSrc1*參數指向的矩形中減去的結構或物件。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

減法是最小的矩形,它包含*lpRectScr1*中所有不在*lpRectScr1 和 lpRectScr2*的*lpRectScr2*交集中的點。

如果*lpRectSrc2*指定的矩形不完全重疊*lpRectSrc1*指定的矩形,則*lpRectSrc1*指定的矩形將至少與一個 x 或 y 方向重疊,則該矩形將保持不變。

例如,如果*lpRectSrc1*為 (10,10, 100,100)和*lpRectSrc2* (50,50, 150,150),則當函數返回時 *,lpRectSrc1*指向的矩形將保持不變。 但是 *,如果 lpRectSrc1* (10,10, 100,100) 和*lpRectSrc2*是 (50,10, 150,150),則在函數返回時 *,lpRectSrc1*指向的矩形將包含座標 (10,10,50,100)。

`SubtractRect`與[運算子和運算元](#operator_-) [-=](#operator_-_eq)不同。 這兩個運營商都沒有打過`SubtractRect`電話。

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

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

## <a name="crecttopleft"></a><a name="topleft"></a>CRect:左上

座標將為對中包含的[CPoint](cpoint-class.md)物件的`CRect`參考傳回 。

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>傳回值

矩形左上角的座標。

### <a name="remarks"></a>備註

可以使用此函數獲取或設置矩形的左上角。 使用賦值運算符左側的函數設置角。

### <a name="example"></a>範例

請參閱[CRect::中心點](#centerpoint)的範例。

## <a name="crectunionrect"></a><a name="unionrect"></a>CRect::聯合

使的`CRect`尺寸等於兩個源矩形的合併。

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>參數

*lpRect1*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`包含源矩形。

*lpRect2*<br/>
指向包含`RECT`源`CRect`矩形的或。

### <a name="return-value"></a>傳回值

如果聯合不為空,則為非零;如果聯合為空,則為 0。

### <a name="remarks"></a>備註

聯合是包含兩個源矩形的最小矩形。

視窗忽略空矩形的尺寸;Windows 忽略空矩形的尺寸。即沒有高度或沒有寬度的矩形。

> [!NOTE]
> 兩個矩形都必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

### <a name="example"></a>範例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a>CRect::寬度

通過從右值中`CRect`減去左值來計算的寬度。

```
int Width() const throw();
```

### <a name="return-value"></a>傳回值

的寬度`CRect`。

### <a name="remarks"></a>備註

寬度可以是負數。

> [!NOTE]
> 矩形必須規範化,否則此函數可能會失敗。 在調用此函數之前,可以調用[NormalizeRect](#normalizerect)來規範化矩形。

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
