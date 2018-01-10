---
title: "CRect 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 067f683b5322b11a4ca33f015d64850c8113ce18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crect-class"></a>CRect 類別
類似於 Windows [RECT](../../mfc/reference/rect-structure1.md)結構。  
  
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
  
|名稱|描述|  
|----------|-----------------|  
|[CRect::BottomRight](#bottomright)|傳回的右下方點`CRect`。|  
|[CRect::CenterPoint](#centerpoint)|傳回的中心點`CRect`。|  
|[CRect::CopyRect](#copyrect)|將複製的來源矩形的尺寸`CRect`。|  
|[CRect::DeflateRect](#deflaterect)|減少的寬度和高度`CRect`。|  
|[CRect::EqualRect](#equalrect)|決定是否`CRect`是否等於指定的矩形。|  
|[CRect::Height](#height)|計算的高度`CRect`。|  
|[CRect::InflateRect](#inflaterect)|增加的寬度和高度`CRect`。|  
|[CRect::IntersectRect](#intersectrect)|設定`CRect`等於兩個矩形的交集。|  
|[CRect::IsRectEmpty](#isrectempty)|決定是否`CRect`是空的。 `CRect`如果，是空的寬度或高度為 0。|  
|[CRect::IsRectNull](#isrectnull)|決定是否**頂端**，**底部**，**左**，和**右**成員變數是所有等於 0。|  
|[CRect::MoveToX](#movetox)|移動`CRect`至指定的 x 座標。|  
|[CRect::MoveToXY](#movetoxy)|移動`CRect`來指定 x 和 y 座標。|  
|[CRect::MoveToY](#movetoy)|移動`CRect`至指定的 y 座標。|  
|[Normalizerect](#normalizerect)|標準化的高度和寬度`CRect`。|  
|[CRect::OffsetRect](#offsetrect)|移動`CRect`所指定的位移。|  
|[CRect::PtInRect](#ptinrect)|判斷指定的點是否位於內`CRect`。|  
|[CRect::SetRect](#setrect)|設定的維度`CRect`。|  
|[CRect::SetRectEmpty](#setrectempty)|設定`CRect`來為空的矩形 （所有座標都等於 0）。|  
|[CRect::Size](#size)|計算的大小`CRect`。|  
|[CRect::SubtractRect](#subtractrect)|減去另一個矩形。|  
|[CRect::TopLeft](#topleft)|傳回的左上方點`CRect`。|  
|[CRect::UnionRect](#unionrect)|設定`CRect`等於兩個矩形的聯集。|  
|[CRect::Width](#width)|計算的寬度`CRect`。|  
  
### <a name="public-operators"></a>公用運算子    
|名稱|描述|  
|----------|-----------------|  
|[CRect::operator-](#operator_-)|減去指定的位移，從`CRect`或 「 洩氣 」`CRect`並傳回產生`CRect`。|  
|[LPCRECT CRect::operator](#operator_lpcrect)|將轉換`CRect`至**LPCRECT**。|  
|[CRect::operator LPRECT](#operator_lprect)|將轉換`CRect`至`LPRECT`。|  
|[CRect::operator ！ =](#operator_neq)|決定是否`CRect`不等於矩形。|  
|[CRect::operator&amp;](#operator_amp)|建立交集的`CRect`和矩形，並傳回產生`CRect`。|  
|[CRect::operator&amp;=](#operator_amp_eq)|設定`CRect`等於交集`CRect`和矩形。|  
|[CRect::operator |](#operator_or)|建立的聯集`CRect`和矩形，並傳回產生`CRect`。|  
|[CRect::operator |=](#operator_or_eq)|設定`CRect`等於的聯集`CRect`和矩形。|  
|[CRect::operator +](#operator_add)|將指定的位移`CRect`或 「 充氣 」`CRect`並傳回產生`CRect`。|  
|[CRect::operator + =](#operator_add_eq)|加入至指定的位移`CRect`或 「 充氣 」 `CRect`。|  
|[CRect::operator =](#operator_eq)|將複製的矩形的尺寸`CRect`。|  
|[CRect::operator =](#operator_-_eq)|減去指定的位移，從`CRect`或 「 洩氣 」 `CRect`。|  
|[CRect::operator = =](#operator_eq_eq)|決定是否`CRect`等於矩形。|  
  
## <a name="remarks"></a>備註  
 `CRect`也包含成員函式來管理`CRect`物件和 Windows`RECT`結構。  
  
 A`CRect`物件可以傳遞做為函式參數只要`RECT`結構**LPCRECT**，或`LPRECT`可以傳遞。  
  
> [!NOTE]
>  這個類別衍生自**tagRECT**結構。 (名稱**tagRECT**小於-常用的名稱`RECT`結構。)這表示資料成員 (**左**，**頂端**，**右**，和**底部**) 的`RECT`結構是可存取的資料成員`CRect`。  
  
 A`CRect`包含定義矩形的左上角和右下方點的成員變數。  
  
 指定時`CRect`，您必須非常小心建構它，它會正規化，換句話說，這類的左方座標的值是否小於右邊和頂端會小於。 比方說，左上角 (10,10) 和右下方 (20,20) 定義標準化的矩形左上角 (20,20) 但右下方 (10,10) 定義了非標準化的矩形。 如果矩形不會正規化，許多`CRect`成員函式可能會傳回不正確的結果。 (請參閱[Normalizerect](#normalizerect)如需這些函式的清單。)在呼叫的函式需要正規化的矩形之前，您可以將非標準化的矩形正規化藉由呼叫`NormalizeRect`函式。  
  
 處理時請特別小心`CRect`與[CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp)和[CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp)成員函式。 顯示內容的對應模式是否 y-範圍是負數，像是`MM_LOENGLISH`，然後`CDC::DPtoLP`會將轉換`CRect`使其頂層是大於底部。 函式，如**高度**和**大小**接著會傳回負數值的轉換高度`CRect`，且該矩形將非標準化。  

  
 當使用多載`CRect`運算子，在第一個運算元必須是`CRect`; 第二個可以是[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tagRECT`  
  
 `CRect`  
  
## <a name="requirements"></a>需求  
 **標頭：** atltypes.h  
  
##  <a name="bottomright"></a>CRect::BottomRight  
 座標會傳回做為參考[CPoint](cpoint-class.md)中所包含的物件`CRect`。  
  
```  
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 矩形的右下角的座標。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式，取得或設定矩形的右下角。 指派運算子的左邊使用此函式，以設定邊角。  
  
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
  
##  <a name="centerpoint"></a>CRect::CenterPoint 
 計算的中心點`CRect`加入左和右值除以兩個，並加入的上方和下方的值，並藉以除以兩個。  
  
```  
CPoint CenterPoint() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 A`CPoint`物件的中心點`CRect`。  
  
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
  
##  <a name="copyrect"></a>CRect::CopyRect  
 複製`lpSrcRect`矩形到`CRect`。  
  
```  
void CopyRect(LPCRECT lpSrcRect) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `lpSrcRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`是要複製的物件。  
  
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

  
##  <a name="crect"></a>CRect::CRect  
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
 *l*  
 指定的左方的位置`CRect`。  
  
 *t*  
 指定頂端`CRect`。  
  
 *r*  
 指定的正確位置`CRect`。  
  
 *b*  
 指定底部`CRect`。  
  
 *srcRect*  
 是指[RECT](../../mfc/reference/rect-structure1.md)結構的座標`CRect`。  
  
 `lpSrcRect`  
 指向`RECT`結構的座標`CRect`。  
  
 `point`  
 指定要建構的矩形的原點。 對應至左上角。  
  
 `size`  
 指定從左上角到右下角的矩形，要建構開始位移。  
  
 *topLeft*  
 指定的左上角位置`CRect`。  
  
 *bottomRight*  
 指定的右下方位置`CRect`。  
  
### <a name="remarks"></a>備註  
 如果任何引數不指定**左**，**頂端**，**右**，和**底部**成員不會初始化。  
  
 `CRect`(**Const RECT &**) 和`CRect`(**LPCRECT**) 建構函式執行[CopyRect](#copyrect)。 其他建構函式直接初始化物件的成員變數。  
  
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
  
##  <a name="deflaterect"></a>CRect::DeflateRect  
 `DeflateRect`「 洩氣 」`CRect`其兩側邁向對其中心。  
  
```  
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();  
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要 deflate 左邊的單位數目及左右兩側`CRect`。  
  
 *y*  
 指定要 deflate 頂端和底部的單位數`CRect`。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)或[CSize](csize-class.md) ，指定要 deflate 的單位數`CRect`。 `cx`值會指定要 deflate 左側和右側的單位數和`cy`值會指定要 deflate 上方和下方的單位數。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`，指定要 deflate 每一端的單位數。  
  
 *l*  
 指定要 deflate 左邊的單位數`CRect`。  
  
 *t*  
 指定要 deflate 頂端的單位數`CRect`。  
  
 *r*  
 指定要 deflate 右邊的單位數`CRect`。  
  
 *b*  
 指定要 deflate 底部的單位數`CRect`。  
  
### <a name="remarks"></a>備註  
 若要這樣做，`DeflateRect`新增單位左邊和頂端，並減去從右側和底部的單位。 參數的`DeflateRect`簽署值; 正值 deflate`CRect`和負值增加它。  
  
 前兩個多載 deflate 配對的相反邊`CRect`使其總寬度就會減少兩次*x* (或`cx`) 和兩次就會減少其總高度*y* (或`cy`)。 其他兩個多載 deflate 的每一端`CRect`各自。  
  
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
  
##  <a name="equalrect"></a>CRect::EqualRect  
 決定是否`CRect`是否等於指定的矩形。  
  
```  
BOOL EqualRect(LPCRECT lpRect) const throw();
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`物件，其中包含矩形的左上角和右下角座標。  
  
### <a name="return-value"></a>傳回值  
 如果兩個矩形會有相同的頂端、 左邊、 下框線和右值，則為非零否則便是 0。  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
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

##  <a name="height"></a>CRect::Height  
 計算的高度`CRect`減去下值的最上層值。  
  
```  
int Height() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 高度`CRect`。  
  
### <a name="remarks"></a>備註  
 產生的值可以是負數。  
  
> [!NOTE]
>  矩形都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect(20, 30, 80, 70);
 int nHt = rect.Height();

```cpp  
   CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

   // nHt is now 40
   ASSERT(nHt == 40);   
```

  
##  <a name="inflaterect"></a>CRect::InflateRect  
 `InflateRect`「 充氣 」`CRect`離開其中心移動其側邊。  
  
```  
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();  
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要擴大左邊的單位數目及左右兩側`CRect`。  
  
 *y*  
 指定要擴大頂端和底部的單位數`CRect`。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)或[CSize](csize-class.md) ，指定要擴大的單位數`CRect`。 `cx`值會指定要擴大左側和右側的單位數和`cy`值會指定要擴大的頂端和底部的單位數。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`，指定要增加每一端的單位數。  
  
 *l*  
 指定要擴大的左半部的單位數`CRect`。  
  
 *t*  
 指定要擴大頂端的單位數`CRect`。  
  
 *r*  
 指定要擴大右邊的單位數`CRect`。  
  
 *b*  
 指定要擴大底部的單位數`CRect`。  
  
### <a name="remarks"></a>備註  
 若要這樣做，`InflateRect`減去從左邊和頂端的單位，並將單位加入至右側和底部。 參數的`InflateRect`簽署值; 正數值擴大`CRect`和負值 deflate 它。  
  
 前兩個多載擴大的相反邊的配對`CRect`使其總寬度會增加兩倍*x* (或`cx`) 和兩次來增加其總高度*y* (或`cy`)。 其他兩個多載擴大的每一端`CRect`各自。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect(0, 0, 300, 300);
 rect.InflateRect(50, 200);

 // rect is now (-50, -200, 350, 500)
 ASSERT(rect == CRect(-50, -200, 350, 500));  
```
  
##  <a name="intersectrect"></a>CRect::IntersectRect  
 可讓`CRect`等於兩個現有矩形的交集。  
  
```  
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();  
```  
  
### <a name="parameters"></a>參數  
 `lpRect1`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`物件，其中包含來源矩形。  
  
 `lpRect2`  
 指向`RECT`結構或`CRect`物件，其中包含來源矩形。  
  
### <a name="return-value"></a>傳回值  
 如果交集不是空的則為非零0，如果交集是空的。  
  
### <a name="remarks"></a>備註  
 交集是最大的矩形包含在兩個現有的矩形中。  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rectOne(125, 0, 150, 200);
 CRect rectTwo(0, 75, 350,  95);
 CRect rectInter;

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
  
##  <a name="isrectempty"></a>CRect::IsRectEmpty  
 決定是否`CRect`是空的。  
  
```  
BOOL IsRectEmpty() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果`CRect`是空的 0 如果`CRect`不是空的。  
  
### <a name="remarks"></a>備註  
 矩形會是空白如果寬度或高度為 0 或負數。 不同於`IsRectNull`，它會決定是否所有矩形的座標都為零。  
  
> [!NOTE]
>  矩形都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rectNone(0, 0, 0, 0);
 CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
   ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
   ASSERT(rectEmpty.IsRectEmpty());   
```

  
##  <a name="isrectnull"></a>CRect::IsRectNull  
 決定是否 top，left、 下方、 和右值`CRect`所有等於 0。  
  
```  
BOOL IsRectNull() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果`CRect`左上方的底部，和右值為所有等於 0; 否則為 0。  
  
### <a name="remarks"></a>備註  
 不同於`IsRectEmpty`，以決定是否是空的矩形。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rectNone(0, 0, 0, 0);
 CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
   ASSERT(!rectSome.IsRectNull());
 // note that null means _all_ zeros

 CRect rectNotNull(0, 0, 35, 50);
 ASSERT(!rectNotNull.IsRectNull());  
```
  
##  <a name="movetox"></a>CRect::MoveToX  
 呼叫此函式可將矩形移至所指定絕對 x 座標*x*。  
  
```  
void MoveToX(int x) throw();  
```  
  
### <a name="parameters"></a>參數  
 *x*  
 絕對 x 座標之矩形左上角。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToX(10);

```cpp  
   CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

   // rect is now (10, 0, 110, 100);
   ASSERT(rect == CRect(10, 0, 110, 100));   
```
  
##  <a name="movetoxy"></a>CRect::MoveToXY  
 呼叫此函式可將矩形移至絕對 x 和 y 座標指定。  
  
```  
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();  
```  
  
### <a name="parameters"></a>參數  
 *x*  
 絕對 x 座標之矩形左上角。  
  
 *y*  
 絕對 y 座標之矩形左上角。  
  
 `point`  
 A**點**結構，指定絕對左上角的矩形。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToXY(10, 10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
   ASSERT(rect == CRect(10, 10, 110, 110));   
```

  
##  <a name="movetoy"></a>CRect::MoveToY  
 呼叫此函式可將矩形移至所指定絕對 y 座標*y*。  
  
```  
void MoveToY(int y) throw();  
```  
  
### <a name="parameters"></a>參數  
 *y*  
 絕對 y 座標之矩形左上角。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToY(10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
   ASSERT(rect == CRect(0, 10, 100, 110));   
```

  
##  <a name="normalizerect"></a>Normalizerect  
 正規化`CRect`以便高度和寬度都是正數。  
  
```  
void NormalizeRect() throw();
```  
  
### <a name="remarks"></a>備註  
 矩形會正規化第四個象限定位，以其 Windows 通常會使用座標。 `NormalizeRect`比較的上方和下方的值，及是否大於底部頂部會交換。 同樣地，它交換的左邊和右邊的值，如果左側大於右側。 此函式時，處理不同的對應模式和反轉矩形。  
  
> [!NOTE]
>  下列`CRect`成員函式需要正規化的矩形才能正常運作：[高度](#height)，[寬度](#width)，[大小](#size)， [IsRectEmpty](#isrectempty)， [PtInRect](#ptinrect)， [EqualRect](#equalrect)， [UnionRect](#unionrect)， [IntersectRect](#intersectrect)， [SubtractRect](#subtractrect)，[運算子 = =](#operator_eq_eq)，[運算子 ！ =](#operator_neq)，[運算子 &#124;](#operator_or)，[運算子 &#124; =](#operator_or_eq)，[運算子 （& s)](#operator_amp)，和[運算子 （& a) =](#operator_amp_eq)。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect1(110, 100, 250, 310);
 CRect rect2(250, 310, 110, 100);

```cpp  
   CRect rect1(110, 100, 250, 310);
   CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
   rect2.NormalizeRect();
 ASSERT(rect1 == rect2);  
```
  
##  <a name="offsetrect"></a>CRect::OffsetRect  
 移動`CRect`所指定的位移。  
  
```  
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();  
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要向左移動或向右的數量。 它必須是負向左移動。  
  
 *y*  
 指定要上移或下移的數量。 它必須是負數向上移動。  
  
 `point`  
 包含[點](../../mfc/reference/point-structure1.md)結構或[CPoint](cpoint-class.md)物件，指定要移動的兩個維度。  
  
 `size`  
 包含[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構或[CSize](csize-class.md)物件，指定要移動的兩個維度。  
  
### <a name="remarks"></a>備註  
 移動`CRect` *x*沿著 x 軸單位並*y*沿著 y 軸的單位。 *x*和*y*參數都是帶正負號的值，因此`CRect`可移動向左或向右和啟動或關閉。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect(0, 0, 35, 35);
 rect.OffsetRect(230, 230);

```cpp  
   CRect rect(0, 0, 35, 35);
   rect.OffsetRect(230, 230);

   // rect is now (230, 230, 265, 265)
   ASSERT(rect == CRect(230, 230, 265, 265));   
```

  
##  <a name="operator_lpcrect"></a>CRect::operator LPCRECT 轉換`CRect`至[LPCRECT](../../mfc/reference/data-types-mfc.md)。  

  
```  
operator LPCRECT() const throw();
```  
  
### <a name="remarks"></a>備註  
 當您使用此函式時，您不需要位址的 (**&**) 運算子。 當您傳遞時自動使用此運算子`CRect`函式的預期物件**LPCRECT**。  
  

##  <a name="operator_lprect"></a>CRect::operator LPRECT  
 將轉換`CRect`至[LPRECT](../../mfc/reference/data-types-mfc.md)。  

  
```
operator LPRECT() throw();
```  
  
### <a name="remarks"></a>備註  
 當您使用此函式時，您不需要位址的 (**&**) 運算子。 當您傳遞時自動使用此運算子`CRect`函式的預期物件`LPRECT`。  
  
### <a name="example"></a>範例  
 請參閱範例的[CRect::operator LPCRECT](#operator_lpcrect)。  
  
##  <a name="operator_eq"></a>CRect::operator =  
 指派*srcRect*至`CRect`。  
  
```  
void operator=(const RECT& srcRect) throw();
```  
  
### <a name="parameters"></a>參數  
 *srcRect*  
 是指來源矩形。 可以是[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect(0, 0, 127, 168);
 CRect rect2;

```cpp  
   CRect rect(0, 0, 127, 168);
   CRect rect2;

   rect2 = rect;
   ASSERT(rect2 == CRect(0, 0, 127, 168));   
```

  
##  <a name="operator_eq_eq"></a>CRect::operator = =  
 決定是否`rect`等於`CRect`藉由比較其左上角和右下角的座標。  
  
```  
BOOL operator==(const RECT& rect) const throw();
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 是指來源矩形。 可以是[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果相等。否則便是 0。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect1(35, 150, 10, 25);
 CRect rect2(35, 150, 10, 25);
 CRect rect3(98, 999,  6,  3);

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

  
##  <a name="operator_neq"></a>CRect::operator ！ =  
 決定是否`rect`不等於`CRect`藉由比較其左上角和右下角的座標。  
  
```  
BOOL operator!=(const RECT& rect) const throw();
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 是指來源矩形。 可以是[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果不相等。否則便是 0。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect1(35, 150, 10, 25);
 CRect rect2(35, 150, 10, 25);
 CRect rect3(98, 999,  6,  3);

```cpp  
   CRect rect1(35, 150, 10, 25);
   CRect rect2(35, 150, 10, 25);
   CRect rect3(98, 999, 6, 3);
ASSERT(rect1 != rect3);
 // works just fine against RECTs, as well

 RECT test;
 test.left = 35;
 test.top = 150;
 test.right = 10;
 test.bottom = 25;

 ASSERT(rect3 != test);  
```
  
##  <a name="operator_add_eq"></a>CRect::operator + =  
 前兩個多載移動`CRect`所指定的位移。  
  
```  
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A[點](../../mfc/reference/point-structure1.md)結構或[CPoint](cpoint-class.md)物件，指定要移動矩形的單位數。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構或[CSize](csize-class.md)物件，指定要移動矩形的單位數。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`物件，其中包含要擴大的每一端的單位數`CRect`。  
  
### <a name="remarks"></a>備註  
 參數的*x*和*y* (或`cx`和`cy`) 值新增至`CRect`。  
  
 第三個多載會擴大`CRect`單位指定每個成員的參數數目。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect1(100, 235, 200, 335);
 CPoint pt(35, 65);
 CRect rect2(135, 300, 235, 400);

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2(135, 300, 235, 400);

   rect1 += pt;
   ASSERT(rect1 == rect2);   
```
  
##  <a name="operator_-_eq"></a>CRect::operator =  
 前兩個多載移動`CRect`所指定的位移。  
  
```  
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A[點](../../mfc/reference/point-structure1.md)結構或[CPoint](cpoint-class.md)物件，指定要移動矩形的單位數。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構或[CSize](csize-class.md)物件，指定要移動矩形的單位數。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`物件，其中包含要 deflate 的每一端的單位數`CRect`。  
  
### <a name="remarks"></a>備註  
 參數的*x*和*y* (或`cx`和`cy`) 值會減去`CRect`。  
  
 第三個多載 「 洩氣 」`CRect`單位指定每個成員的參數數目。 請注意，這個多載函式，例如[DeflateRect](#deflaterect)。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect1(100, 235, 200, 335);
 CPoint pt(35, 65);
 rect1 -= pt;

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);

   rect1 -= pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect1 == rectResult);   
```
  
##  <a name="operator_amp_eq"></a>CRect::operator&amp;=  
 設定`CRect`等於交集`CRect`和`rect`。  
  
```  
void operator&=(const RECT& rect) throw();
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 包含[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="remarks"></a>備註  
 交集是包含在兩個矩形的最大矩形。  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
 請參閱範例的[CRect::IntersectRect](#intersectrect)。  
  
##  <a name="operator_or_eq"></a>CRect::operator &#124; =  
 設定`CRect`等於的聯集`CRect`和`rect`。  
  
```  
void operator|=(const RECT& rect) throw();
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 包含`CRect`或[RECT](../../mfc/reference/rect-structure1.md)。  
  
### <a name="remarks"></a>備註  
 等位是包含兩個來源矩形的最小矩形。  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect1(100,   0, 200, 300);
 CRect rect2( 0, 100, 300, 200);
 rect1 |= rect2;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);

   rect1 |= rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect1);   
```

  
##  <a name="operator_add"></a>CRect::operator +  
 前兩個多載會傳回`CRect`物件是否等於`CRect`位移的指定位移。  
  
```  
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A[點](../../mfc/reference/point-structure1.md)結構或[CPoint](cpoint-class.md)物件，指定要移動的傳回值的單位數。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構或[CSize](csize-class.md)物件，指定要移動的傳回值的單位數。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`物件，其中包含要擴大的傳回值的每一端的單位數。  
  
### <a name="return-value"></a>傳回值  
 `CRect`所產生的移動或因而誇大`CRect`參數中指定的單位數。  
  
### <a name="remarks"></a>備註  
 參數的*x*和*y* (或`cx`和`cy`) 會將參數加入至`CRect`的位置。  
  
 第三個多載會傳回新`CRect`等於`CRect`膨脹單位指定每個成員的參數數目。  
  
### <a name="example"></a>範例  
```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 + pt;
   CRect   rectResult(135, 300, 235, 400);
   ASSERT(rectResult == rect2);   
```

  
##  <a name="operator_-"></a>CRect::operator-  
 前兩個多載會傳回`CRect`物件是否等於`CRect`位移的指定位移。  
  
```  
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A[點](../../mfc/reference/point-structure1.md)結構或`CPoint`物件，指定要移動的傳回值的單位數。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構或`CSize`物件，指定要移動的傳回值的單位數。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`物件，其中包含要 deflate 每一端的傳回值的單位數。  
  
### <a name="return-value"></a>傳回值  
 `CRect`所產生的移動或升空的方式回應`CRect`參數中指定的單位數。  
  
### <a name="remarks"></a>備註  
 參數的*x*和*y* (或`cx`和`cy`) 參數會減去`CRect`的位置。  
  
 第三個多載會傳回新`CRect`等於`CRect`縮小單位指定每個成員的參數數目。 請注意，這個多載函式，例如[DeflateRect](#deflaterect)，而非[SubtractRect](#subtractrect)。  
  
### <a name="example"></a>範例  
```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 - pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect2 == rectResult);   
```

  
##  <a name="operator_amp"></a>CRect::operator&amp;  
 傳回`CRect`也就是交集`CRect`和*rect2*。  
  
```  
CRect operator&(const RECT& rect2) const throw();
```  
  
### <a name="parameters"></a>參數  
 *rect2*  
 包含[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="return-value"></a>傳回值  
 A`CRect`也就是交集`CRect`和*rect2*。  
  
### <a name="remarks"></a>備註  
 交集是包含在兩個矩形的最大矩形。  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 & rect2;
   CRect   rectResult(100, 100, 200, 200);
   ASSERT(rectResult == rect3);   
```

  
##  <a name="operator_or"></a>CRect::operator &#124;  
 傳回`CRect`也就是聯集的`CRect`和*rect2*。  
  
```   
CRect operator|(const RECT& 
rect2) const throw(); 
```  
  
### <a name="parameters"></a>參數  
 *rect2*  
 包含[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="return-value"></a>傳回值  
 A`CRect`也就是聯集的`CRect`和*rect2*。  
  
### <a name="remarks"></a>備註  
 等位是包含兩個矩形的最小矩形。  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect1(100,   0, 200, 300);
 CRect rect2( 0, 100, 300, 200);
 CRect rect3;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 | rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```

  
##  <a name="ptinrect"></a>CRect::PtInRect  
 判斷指定的點是否位於內`CRect`。  
  
```   
BOOL PtInRect(POINT point) const throw(); 
```  
  
### <a name="parameters"></a>參數  
 `point`  
 包含[點](../../mfc/reference/point-structure1.md)結構或[CPoint](cpoint-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果這個點位於內則為非零`CRect`; 否則為 0。  
  
### <a name="remarks"></a>備註  
 點位於`CRect`它位於左邊或最上層的一邊或四個邊內。 在右側或底端端上的點超出`CRect`。  
  
> [!NOTE]
>  矩形都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
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
  
##  <a name="setrect"></a>CRect::SetRect  
 設定的維度`CRect`至指定的座標。  
  
```   
void SetRect(int x1, int y1, int x2, int y2) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `x1`  
 指定左上角的 x 座標。  
  
 `y1`  
 指定左上角的 y 座標。  
  
 `x2`  
 指定右下角的 x 座標。  
  
 `y2`  
 指定右下角的 y 座標。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect;
 rect.SetRect(256, 256, 512, 512);

```cpp  
   CRect rect;
   rect.SetRect(256, 256, 512, 512);
   ASSERT(rect == CRect(256, 256, 512, 512));   
```

  
##  <a name="setrectempty"></a>CRect::SetRectEmpty  
 可讓`CRect`null 矩形將所有座標設定為零。  
  
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
  
##  <a name="size"></a>CRect::SIZE 
 `cx`和`cy`成員的傳回值包含高度和寬度`CRect`。  
  
```  
CSize Size() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 A [CSize](csize-class.md)物件，其中包含的大小`CRect`。  
  
### <a name="remarks"></a>備註  
 高度或寬度可以是負數。  
  
> [!NOTE]
>  矩形都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
 CRect rect(10, 10, 50, 50);
 CSize sz = rect.Size();
 ASSERT(sz.cx == 40 && sz.cy == 40);  
```

##  <a name="subtractrect"></a>CRect::SubtractRect  
 可讓維度的**CRect**等於的減法`lpRectSrc2`從`lpRectSrc1`。  
  
```  
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpRectSrc1`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或`CRect`從中矩形是要減去的物件。  
  
 `lpRectSrc2`  
 指向`RECT`結構或`CRect`指向的物件會將被減去矩形`lpRectSrc1`參數。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 減法是包含中的所有點的最小矩形`lpRectScr1`所沒有的交集`lpRectScr1`和*lpRectScr2*。  
  
 所指定的矩形`lpRectSrc1`將會維持不變，如果所指定的矩形`lpRectSrc2`完全不重疊所指定的矩形*lpRectSrc1*中至少一個的 x 或 y-方向。  
  
 例如，如果`lpRectSrc1`已 10,10 (100,100） 和`lpRectSrc2`已 50,50 (150,150），矩形所指`lpRectSrc1`函式傳回時就會維持不變。 如果`lpRectSrc1`已 10,10 (100,100） 和`lpRectSrc2`已 50,10 (150,150），不過，在矩形所指`lpRectSrc1`會包含座標 （10,10、 50100） 函式傳回時。  
  
 `SubtractRect`不與相同[運算子-](#operator_-)也[運算子-=](#operator_-_eq)。 這些運算子任一曾經呼叫`SubtractRect`。  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
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
  
##  <a name="topleft"></a>CRect::TopLeft  
 座標會傳回做為參考[CPoint](cpoint-class.md)中所包含的物件`CRect`。  
  
```  
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw(); 
```  
  
### <a name="return-value"></a>傳回值  
 矩形的左上角的座標。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式，取得或設定矩形左上角。 指派運算子的左邊使用此函式，以設定邊角。  
  
### <a name="example"></a>範例  
 請參閱範例的[CRect::CenterPoint](#centerpoint)。  
  
##  <a name="unionrect"></a>CRect::UnionRect  
 可讓維度的`CRect`等於兩個來源矩形的聯集。  
  
```  
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpRect1`  
 指向[RECT](../../mfc/reference/rect-structure1.md)或`CRect`，其中包含來源矩形。  
  
 `lpRect2`  
 指向`RECT`或`CRect`，其中包含來源矩形。  
  
### <a name="return-value"></a>傳回值  
 如果等位不是空的則為非零0，表示聯集為空白。  
  
### <a name="remarks"></a>備註  
 等位是包含兩個來源矩形的最小矩形。  
  
 Windows 會忽略空的矩形中維度也就是一個矩形，沒有高度，或者沒有寬度。  
  
> [!NOTE]
>  這兩個矩形的連接都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  
```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3.UnionRect(&rect1, &rect2);
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```
 
##  <a name="width"></a>CRect::Width  
 計算的寬度`CRect`減去右值的左的值。  
  
```  
int Width() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 寬度`CRect`。  
  
### <a name="remarks"></a>備註  
 寬度可以是負數。  
  
> [!NOTE]
>  矩形都必須正規化，或此函式可能會失敗。 您可以呼叫[NormalizeRect](#normalizerect)正規化矩形，然後再呼叫此函式。  
  
### <a name="example"></a>範例  

```cpp  
   CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
   // nWid is now 60
   ASSERT(nWid == 60);   
```
## <a name="see-also"></a>請參閱  
 [CPoint 類別](cpoint-class.md)   
 [CSize 類別](csize-class.md)   
 [RECT](../../mfc/reference/rect-structure1.md)


