---
title: CSize 類別
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: 26bb43355f4dff3f77a905068bea83dd1ceaf79c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491648"
---
# <a name="csize-class"></a>CSize 類別

類似於實作相對座標或位置的 Windows [SIZE](/windows/win32/api/windef/ns-windef-size) 結構。

## <a name="syntax"></a>語法

```
class CSize : public tagSIZE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CSize：： CSize](#csize)|建構 `CSize` 物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSize：： operator-](#operator_-)|減去兩個大小。|
|[CSize：： operator！ =](#operator_neq)|檢查`CSize`和大小是否不相等。|
|[CSize：： operator +](#operator_add)|會加入兩個大小。|
|[CSize：： operator + =](#operator_add_eq)|將大小新增至`CSize`。|
|[CSize::operator -=](#operator_-_eq)|從中`CSize`減去大小。|
|[CSize：： operator = =](#operator_eq_eq)|檢查`CSize`和大小是否相等。|

## <a name="remarks"></a>備註

這個類別衍生自`SIZE`結構。 這`CSize`表示您可以在呼叫`SIZE`的參數中傳遞，而且`SIZE`結構的資料成員是可存取的資料成員`CSize`。

`SIZE` `cy` `cx` （和`CSize`）的和成員是公用的。 此外， `CSize`會執行成員函式來`SIZE`操作結構。

> [!NOTE]
> 如需共用公用程式類別（例如`CSize`）的詳細資訊，請參閱[共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagSIZE`

`CSize`

## <a name="requirements"></a>需求

**標頭：** atltypes。h

##  <a name="csize"></a>CSize：： CSize

建構 `CSize` 物件。

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>參數

*initCX*<br/>
設定的`CSize`成員。 `cx`

*initCY*<br/>
設定的`CSize`成員。 `cy`

*initSize*<br/>
用來`CSize` 初始化`CSize`的[大小](/windows/win32/api/windef/ns-windef-size)結構或物件。

*initPt*<br/>
用來`CPoint` 初始化`CSize`的[點](/windows/win32/api/windef/ns-windef-point)結構或物件。

*dwSize*<br/>
用來初始化`CSize`的 DWORD。 低序位單字是`cx`成員，而高序位單字`cy`是成員。

### <a name="remarks"></a>備註

如果未指定任何引數`cx` ， `cy`和會初始化為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CSize：： operator = =

檢查兩個大小是否相等。

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>備註

如果大小相等，則傳回非零值，otherwize 0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>CSize：： operator！ =

檢查兩個大小是否不相等。

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>備註

如果大小不相等，會傳回非零，否則會傳回0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>CSize：： operator + =

將大小新增至這個`CSize`。

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>CSize：： operator-=

從這個`CSize`減去大小。

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>CSize：： operator +

這些運算子會將`CSize`此值新增至參數的值。

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>備註

請參閱下列個別運算子的說明：

- **operator +(** *size* **)**

  這種作業會`CSize`新增兩個值。

- **operator +(** *point* **)**

  這項作業會以這個`CSize`值位移（移動）[點](/previous-versions/dd162805\(v=vs.85\))（或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)）值。 這個`cx` `x` 值的`POINT`和`cy`成員會加入至值的和`y`資料成員。 `CSize` 它類似于採用[大小](/windows/win32/api/windef/ns-windef-size)參數的[CPoint：： operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)版本。

- **operator +(** *lpRect* **)**

   這項作業會使用此`CSize`值來位移（移動）[矩形](/previous-versions/dd162897\(v=vs.85\))（或[CRect](../../atl-mfc-shared/reference/crect-class.md)）值。 這個`cx` `cy` `left` `top` `right`值的和成員會加入至`RECT`值的、、和`bottom`資料成員。 `CSize` 它類似于採用[大小](/windows/win32/api/windef/ns-windef-size)參數的[CRect：： operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add)版本。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>CSize：： operator-

這些運算子的前三個會將`CSize`此值減去參數的值。

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>備註

第四個運算子（一元減號）會變更`CSize`值的正負號。 請參閱下列個別運算子的說明：

- **operator -(** *size* **)**

  這種作業會`CSize`減去兩個值。

- **operator -(** *point* **)**

  這項作業會以這個`CSize`值的加總反向位移（移動）[點](/previous-versions/dd162805\(v=vs.85\))或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)值。 此`cx` `cy` `x`值的和會從`POINT`值的和`y`資料成員中扣除。 `CSize` 它類似于採用[大小](/windows/win32/api/windef/ns-windef-size)參數的[CPoint：： operator](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)版本。

- **operator -(** *lpRect* **)**

  這項作業會藉由此`CSize`值的加反轉來位移（移動）[矩形](/previous-versions/dd162897\(v=vs.85\))或[CRect](../../atl-mfc-shared/reference/crect-class.md)值。 此`cx` `cy` `left` `top`值的和成員`right`會從值`RECT`的、、和`bottom`資料成員中扣除。 `CSize` 它類似于採用[大小](/windows/win32/api/windef/ns-windef-size)參數的[CRect：： operator](../../atl-mfc-shared/reference/crect-class.md#operator_-)版本。

- **operator -()**

  這項作業會傳回此`CSize`值的加總。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint 類別](../../atl-mfc-shared/reference/cpoint-class.md)
