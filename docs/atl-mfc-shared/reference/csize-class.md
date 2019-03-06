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
ms.openlocfilehash: 36da88a49e7d0e648d44b0798e108a60abb935d9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415145"
---
# <a name="csize-class"></a>CSize 類別

類似於實作相對座標或位置的 Windows [SIZE](/windows/desktop/api/windef/ns-windef-tagsize) 結構。

## <a name="syntax"></a>語法

```
class CSize : public tagSIZE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSize::CSize](#csize)|建構 `CSize` 物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSize::operator-](#operator_-)|減去兩個大小。|
|[CSize::operator !=](#operator_neq)|檢查相等`CSize`和大小。|
|[CSize::operator +](#operator_add)|新增兩個大小。|
|[CSize::operator +=](#operator_add_eq)|將大小`CSize`。|
|[CSize::operator -=](#operator_-_eq)|減去大小`CSize`。|
|[CSize::operator ==](#operator_eq_eq)|檢查是否相等`CSize`和大小。|

## <a name="remarks"></a>備註

此類別衍生自`SIZE`結構。 這表示您可以傳遞`CSize`中的參數，呼叫`SIZE`且的資料成員`SIZE`結構是否可存取資料成員`CSize`。

`cx`並`cy`的成員`SIZE`(和`CSize`) 都是公用的。 颾魤 ㄛ`CSize`實作成員函式來操作`SIZE`結構。

> [!NOTE]
> 如需有關共用 公用程式類別 (例如`CSize`)，請參閱 <<c2> [ 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagSIZE`

`CSize`

## <a name="requirements"></a>需求

**標頭：** atltypes.h

##  <a name="csize"></a>  CSize::CSize

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
設定組`cx`成員`CSize`。

*initCY*<br/>
設定組`cy`成員`CSize`。

*initSize*<br/>
[大小](/windows/desktop/api/windef/ns-windef-tagsize)結構或`CSize`物件，用來初始化`CSize`。

*initPt*<br/>
[點](/windows/desktop/api/windef/ns-windef-tagpoint)結構或`CPoint`物件，用來初始化`CSize`。

*dwSize*<br/>
DWORD 用來初始化`CSize`。 低序位字`cx`成員與高序位文字是`cy`成員。

### <a name="remarks"></a>備註

如果指定沒有引數`cx`和`cy`初始化為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CSize::operator = =

這兩個大小相等檢查。

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>備註

傳回非零值，如果大小相等的 otherwize 0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>  CSize::operator ！ =

這兩個大小相等檢查。

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>備註

傳回非零值，如果大小不相等，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CSize::operator + =

將大小加入至這個`CSize`。

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CSize::operator -=

減去大小，以從這個`CSize`。

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>  CSize::operator +

這些運算子將此新增`CSize`值參數的值。

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>備註

請參閱下列說明的個別運算子：

- **operator +(** *size* **)**

  這項作業會加入兩個`CSize`值。

- **operator +(** *point* **)**

  這項作業的位移 （移動）[點](/previous-versions/dd162805\(v=vs.85\))(或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) 值，這個`CSize`值。 `cx`並`cy`這個成員`CSize`值新增至`x`並`y`的資料成員`POINT`值。 它相當於新版[CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)採用[大小](/windows/desktop/api/windef/ns-windef-tagsize)參數。

- **operator +(** *lpRect* **)**

   這項作業的位移 （移動） [RECT](/previous-versions/dd162897\(v=vs.85\)) (或[CRect](../../atl-mfc-shared/reference/crect-class.md)) 值，這個`CSize`值。 `cx`並`cy`這個成員`CSize`值新增至`left`， `top`， `right`，以及`bottom`資料成員的`RECT`值。 它相當於新版[CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add)採用[大小](/windows/desktop/api/windef/ns-windef-tagsize)參數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>  CSize::operator-

這些運算子的前三個減去此`CSize`值參數的值。

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>備註

第四個運算子，也就是一元減號，變更的正負號`CSize`值。 請參閱下列說明的個別運算子：

- **operator -(** *size* **)**

  這項作業，減去兩個`CSize`值。

- **operator -(** *point* **)**

  這項作業的位移 （移動）[點](/previous-versions/dd162805\(v=vs.85\))或是[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)加法反元素，這個值`CSize`值。 `cx`並`cy`這個`CSize`值減去`x`並`y`的資料成員`POINT`值。 它相當於新版[CPoint::operator-](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)採用[大小](/windows/desktop/api/windef/ns-windef-tagsize)參數。

- **operator -(** *lpRect* **)**

  這項作業的位移 （移動） [RECT](/previous-versions/dd162897\(v=vs.85\))或是[CRect](../../atl-mfc-shared/reference/crect-class.md)加法反元素，這個值`CSize`值。 `cx`並`cy`這個成員`CSize`值減去`left`， `top`， `right`，以及`bottom`資料成員的`RECT`值。 它相當於新版[CRect::operator-](../../atl-mfc-shared/reference/crect-class.md#operator_-)採用[大小](/windows/desktop/api/windef/ns-windef-tagsize)參數。

- **operator -()**

  此操作會傳回這個加法反元素`CSize`值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint 類別](../../atl-mfc-shared/reference/cpoint-class.md)

