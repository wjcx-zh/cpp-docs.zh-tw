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
ms.openlocfilehash: 331b89ff118f727303e887670960ee6078b01fb1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747092"
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
|[CPoint:CPoint](#cpoint)|建構 `CPoint`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPoint:偏移](#offset)|新增值到`x`與中`y``CPoint`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPoint::運算符 -](#operator_-)|返回`CPoint`和 大小的差異,或點的否定,或兩個點之間的大小差異,或由負大小的偏移。|
|[CPoint::操作員!*](#operator_neq)|檢查兩點之間的不平等。|
|[CPoint::運算符 |](#operator_add)|返回和`CPoint`大小或點的總和,`CRect`或偏移大小。|
|[CPoint::運算符 |](#operator_add_eq)|`CPoint`通過添加大小或點進行偏移。|
|[CPoint::運算符 -*](#operator_-_eq)|`CPoint`通過減去大小或點來偏移。|
|[CPoint::運算符 |](#operator_eq_eq)|檢查兩點之間的相等性。|

## <a name="remarks"></a>備註

它還包括要操作`CPoint`的成員函數和[POINT](/windows/win32/api/windef/ns-windef-point)結構。

對`CPoint`象 可以在使用結構的`POINT`任何位置 使用。 與「大小」互動的此類運算符接受[CSize](../../atl-mfc-shared/reference/csize-class.md)物件或[SIZE](/windows/win32/api/windef/ns-windef-size)結構,因為兩者是可互換的。

> [!NOTE]
> 此類派生自結構`tagPOINT`。 (名稱`tagPOINT`是`POINT`結構不太常用的名稱。這意味著`POINT`結構的數據成員`x`和`y`是的`CPoint`可訪問數據成員。

> [!NOTE]
> 有關共用實用程式類的詳細資訊(如`CPoint`),請參閱[共享類](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagPOINT`

`CPoint`

## <a name="requirements"></a>需求

**標題:** atltype.h

## <a name="cpointcpoint"></a><a name="cpoint"></a>CPoint:CPoint

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
[POINT](/windows/win32/api/windef/ns-windef-point)結構`CPoint`或指定用於初始`CPoint`化的值。

*initSize*<br/>
[指定](/windows/win32/api/windef/ns-windef-size)用於初始`CPoint`化的值的大小結構或[CSize。](../../atl-mfc-shared/reference/csize-class.md)

*dwPoint*<br/>
將`x`成員設為*dwPoint*的低階字`y`,將 成員設到*dwPoint*的高階字。

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

## <a name="cpointoffset"></a><a name="offset"></a>CPoint:偏移

新增值到`x`與中`y``CPoint`。

```cpp
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>參數

*x 位移*<br/>
指定要偏移`x`的成員的`CPoint`金額 。

*yOffset*<br/>
指定要偏移`y`的成員的`CPoint`金額 。

*點*<br/>
指定要偏移的`CPoint`量`CPoint`( [POINT](/windows/win32/api/windef/ns-windef-point)或 )。

*size*<br/>
指定要偏移的`CPoint`量[(SIZE](/windows/win32/api/windef/ns-windef-size)或["大小](../../atl-mfc-shared/reference/csize-class.md))。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a>CPoint::運算符 |

檢查兩點之間的相等性。

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)`CPoint`結構或 物件。

### <a name="return-value"></a>傳回值

如果點相等,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a>CPoint::操作員!*

檢查兩點之間的不平等。

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)`CPoint`結構或 物件。

### <a name="return-value"></a>傳回值

如果點不相等,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a>CPoint::運算符 |

第一個重載到`CPoint`新增大小到 。

```cpp
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>參數

*size*<br/>
包含[SIZE](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

*點*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

### <a name="remarks"></a>備註

第二個重載到`CPoint`新增點到 。

在這兩種情況下,添加是通過將右側操作數`x`的成員`cx`(`x`或) 成員添加`CPoint`到右側操作數的成員`y`,並將右側操作`cy`數的 (或`y`)`CPoint`成員添加到成員。

例如,新增到`CPoint(5, -7)`包含的`CPoint(30, 40)`變數會改變為`CPoint(35, 33)`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a>CPoint::運算符 -*

第一個重載從 中減`CPoint`去 大小。

```cpp
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>參數

*size*<br/>
包含[SIZE](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

*點*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

### <a name="remarks"></a>備註

第二個重載從 中減`CPoint`去 一個點。

在這兩種情況下,減法是通過從 中減去`x`右側`cx``x`操作數的成員(`CPoint`或 )`y``cy``y`成員,並從 中減去右側操作數`CPoint`的成員來完成。

例如,從包含的`CPoint(5, -7)``CPoint(30, 40)`變數中減去將變數更改為`CPoint(25, 47)`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a>CPoint::運算符 |

使用此運算子`CPoint`可以偏移`CPoint``CSize`或 物件,或是由`CRect``CPoint`位移 。

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>參數

*size*<br/>
包含[SIZE](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

*點*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

*lpRect*<br/>
包含指向[RECT](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標。

### <a name="return-value"></a>傳回值

由`CPoint`大小偏移的 a、`CPoint`由點 偏移`CRect`的 a 或 偏移點。

### <a name="remarks"></a>備註

例如,使用前兩個重載之`CPoint(25, -19)`一按`CPoint(15, 5)`點`CSize(15, 5)`或大小 偏移點`CPoint(40, -14)`將返回值 。

將矩形添加到點返回矩形後偏移在點中指定的`x``y`和值。 例如,使用最後一個重載來偏移矩形`CRect(125, 219, 325, 419)`的`CPoint(25, -19)`點`CRect(150, 200, 350, 400)`傳回 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a>CPoint::運算符 -

使用前兩個重載之一從`CPoint``CSize``CPoint`中減去 或 物件。

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>參數

*點*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)結構或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標。

### <a name="return-value"></a>傳回值

A`CSize`是兩個點之間的差異,一`CPoint`個 被大小否定所抵消,一`CRect`個是 被點否定所抵消`CPoint`的,或者是 點的否定。

### <a name="remarks"></a>備註

第三個重載`CRect`通過否定偏`CPoint`移 a。 最後,使用一元運算元否定`CPoint`。

例如,使用第一個重載來查找兩個點`CPoint(25, -19)``CPoint(15, 5)`和`CSize(10, -24)`返回之間的差異。

`CSize`從中`CPoint`減去 執行與上述相同的計算,`CPoint`但返回`CSize`物件,而不是物件。 例如,使用第二個重載搜尋點`CPoint(25, -19)`和大小`CSize(15, 5)`之間的差值傳回`CPoint(10, -24)`。

從點中減去矩形返回由點中指定的`x``y`和 值的底數偏移的矩形。 例如,使用最後一個重載按點`CRect(125, 200, 325, 400)``CPoint(25, -19)`偏移矩形`CRect(100, 219, 300, 419)`傳回 。

使用一元運算符否定點。 例如,使用帶有點的`CPoint(25, -19)`一元運算符傳回`CPoint(-25, 19)`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[點結構](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize 類別](../../atl-mfc-shared/reference/csize-class.md)
