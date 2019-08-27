---
title: CPoint 類別
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: b7c13ef8b9656c5c2fa6a90fefca0d9babbe1c84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491219"
---
# <a name="cpoint-class"></a>CPoint 類別

類似於 Windows `POINT` 結構。

## <a name="syntax"></a>語法

```
class CPoint : public tagPOINT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPoint:: CPoint](#cpoint)|建構 `CPoint`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPoint::Offset](#offset)|將值加入至`x`的`y`和成員`CPoint`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPoint:: operator-](#operator_-)|傳回`CPoint`和大小的差異, 或點的負數, 或兩個點之間的大小差異, 或以負大小的位移。|
|[CPoint:: operator! =](#operator_neq)|檢查兩個點之間是否不相等。|
|[CPoint:: operator +](#operator_add)|傳回`CPoint`和大小或點的總和, `CRect`或大小的位移。|
|[CPoint:: operator + =](#operator_add_eq)|藉`CPoint`由新增大小或點來位移。|
|[CPoint::operator -=](#operator_-_eq)|藉`CPoint`由減去大小或點來位移。|
|[CPoint:: operator = =](#operator_eq_eq)|檢查兩個點之間是否相等。|

## <a name="remarks"></a>備註

它也包含操作`CPoint`和[指向](/windows/win32/api/windef/ns-windef-point)結構的成員函式。

物件可以在使用`POINT`結構的任何位置使用。 `CPoint` 這個類別的運算子與「大小」互動會接受[CSize](../../atl-mfc-shared/reference/csize-class.md)物件或[大小](/windows/win32/api/windef/ns-windef-size)結構, 因為這兩者都可以互換。

> [!NOTE]
>  這個類別衍生自`tagPOINT`結構。 (名稱`tagPOINT`是`POINT`結構較不常使用的名稱)。這表示`POINT`結構的資料成員 ( `x`和`y`) 是的`CPoint`可存取資料成員。

> [!NOTE]
>  如需共用公用程式類別 (例如`CPoint`) 的詳細資訊, 請參閱[共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagPOINT`

`CPoint`

## <a name="requirements"></a>需求

**標頭:** atltypes。h

##  <a name="cpoint"></a>CPoint:: CPoint

建構 `CPoint` 物件。

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>參數

*initX*<br/>
指定 `x` 之 `CPoint` 成員的值。

*initY*<br/>
指定 `y` 之 `CPoint` 成員的值。

*initPt*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構或`CPoint` , 指定用來初始化`CPoint`的值。

*initSize*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md) , 指定用來初始化`CPoint`的值。

*dwPoint*<br/>
將成員設為`y` *dwPoint*的低序位單字, 並將成員設定為 dwPoint 的高序位單字。 `x`

### <a name="remarks"></a>備註

如果未提供引數，`x` 和 `y` 成員都會設定為 0。

### <a name="example"></a>範例

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

##  <a name="offset"></a>CPoint:: Offset

將值加入至`x`的`y`和成員`CPoint`。

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>參數

*xOffset*<br/>
指定`x` 成員`CPoint`的位移數量。

*yOffset*<br/>
指定`y` 成員`CPoint`的位移數量。

*point*<br/>
指定要位移的`CPoint`數量 ( `CPoint`[點](/windows/win32/api/windef/ns-windef-point)或)。

*size*<br/>
指定要位移的`CPoint`數量 ([大小](/windows/win32/api/windef/ns-windef-size)或[CSize](../../atl-mfc-shared/reference/csize-class.md))。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CPoint:: operator = =

檢查兩個點之間是否相等。

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>參數

*point*<br/>
包含[點](/windows/win32/api/windef/ns-windef-point)結構或`CPoint`物件。

### <a name="return-value"></a>傳回值

如果點相等, 則為非零值;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>CPoint:: operator! =

檢查兩個點之間是否不相等。

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>參數

*point*<br/>
包含[點](/windows/win32/api/windef/ns-windef-point)結構或`CPoint`物件。

### <a name="return-value"></a>傳回值

如果點不相等, 則為非零值;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>CPoint:: operator + =

第一個多載會將大小新增`CPoint`至。

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>參數

*size*<br/>
包含[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

*point*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

### <a name="remarks"></a>備註

第二個多載會將點`CPoint`加入至。

在這兩種情況下, 只要將右`x`運算元的`cx`(或`CPoint` ) 成員加入至`x`的成員, 並將右運算元的`y` (或`cy`) 成員加入至, 即可完成加法。`y` 的`CPoint`成員。

例如, 將新增`CPoint(5, -7)`至包含`CPoint(30, 40)`的變數會將變數變更為`CPoint(35, 33)`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>CPoint:: operator-=

第一個多載會從`CPoint`減去大小。

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>參數

*size*<br/>
包含[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

*point*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

### <a name="remarks"></a>備註

第二個多載會將中`CPoint`的點減去。

在這兩種情況下, 減法都是`x`藉由`cx` `CPoint`從`x`的成員減去右運算元的 (或) 成員來完成, 並減去`y`右手邊`cy`的 (或) 成員來自`y` 成員`CPoint`的運算元。

例如, 減去`CPoint(5, -7)`包含`CPoint(30, 40)`的變數會將變數變更為`CPoint(25, 47)`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>CPoint:: operator +

使用這個運算子, 以`CPoint` `CPoint`或`CSize` 物件位移`CRect` , 或由位移。 `CPoint`

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>參數

*size*<br/>
包含[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

*point*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

*lpRect*<br/>
包含[RECT](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標。

### <a name="return-value"></a>傳回值

, 其位移為大小、以`CPoint`點位移的, 或`CRect`某個點的位移。 `CPoint`

### <a name="remarks"></a>備註

例如, 使用前兩個多載的其中一個, 以點`CPoint(25, -19)` `CPoint(15, 5)`或大小`CSize(15, 5)`來位移點, 會傳回`CPoint(40, -14)`值。

將矩形加入至某個點之後, 會傳回以點中指定`x`的`y`和值位移後的矩形。 例如, 使用最後一個多載, 以`CRect(125, 219, 325, 419)` `CRect(150, 200, 350, 400)`點`CPoint(25, -19)`來位移矩形。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>CPoint:: operator-

使用前兩個多載的其中一個來`CPoint`減去`CSize`中`CPoint`的或物件。

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>參數

*point*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

*lpRect*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標。

### <a name="return-value"></a>傳回值

, 這是兩個點之間的差異, `CPoint`其位移為大小的否定、 `CRect`位移為點否定的, 或`CPoint`為負的點。 `CSize`

### <a name="remarks"></a>備註

第三個多載`CRect`會以的`CPoint`否定位移。 最後, 使用一元運算子來否定`CPoint`。

例如, 使用第一個多載來找出兩個點`CPoint(25, -19)`之間的差異`CSize(10, -24)`, 然後`CPoint(15, 5)`傳回。

從減去, 會執行與上述相同的計算, 但`CPoint`會傳回物件, `CSize`而不是物件。 `CPoint` `CSize` 例如, 使用第二個多載來尋找點`CPoint(25, -19)`和`CPoint(10, -24)`大小`CSize(15, 5)`之間的差異。

從點減去矩形會傳回以點中指定之`x`和`y`值的否定位移的矩形。 例如, 使用最後一個多載, 在`CRect(125, 200, 325, 400)` `CRect(100, 219, 300, 419)`點`CPoint(25, -19)`傳回時位移矩形。

使用一元運算子來否定某個點。 例如, 搭配使用一元運算子與點`CPoint(25, -19)` `CPoint(-25, 19)`會傳回。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[點結構](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize 類別](../../atl-mfc-shared/reference/csize-class.md)
