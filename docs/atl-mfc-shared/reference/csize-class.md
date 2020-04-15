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
ms.openlocfilehash: 6d1b82e3f60428e3a778709dc69de983a7f886bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317667"
---
# <a name="csize-class"></a>CSize 類別

類似於實作相對座標或位置的 Windows [SIZE](/windows/win32/api/windef/ns-windef-size) 結構。

## <a name="syntax"></a>語法

```
class CSize : public tagSIZE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[大小:大小](#csize)|建構 `CSize` 物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSize:運算子 -](#operator_-)|減去兩種大小。|
|[CSize::操作員!*](#operator_neq)|檢查大小之間的`CSize`不等式。|
|[CSize:運算符 |](#operator_add)|添加兩種大小。|
|[大小::操作員 |](#operator_add_eq)|新增大小`CSize`到 。|
|[大小::運算子 -*](#operator_-_eq)|從`CSize`中減去大小。|
|[大小::運算符 |](#operator_eq_eq)|檢查和大小之間的`CSize`相等性。|

## <a name="remarks"></a>備註

此類派生自結構`SIZE`。 這意味著您可以傳遞 調`CSize`用`SIZE`的參數`SIZE`,並且結構的數據成員`CSize`是 可訪問的數據成員。

和`CSize`(的成員 ) 是`cx``cy``SIZE`公開的。 此外,`CSize`實現成員函數來操作`SIZE`結構 。

> [!NOTE]
> 有關共用實用程式類的詳細資訊(如`CSize`),請參閱[共享類](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagSIZE`

`CSize`

## <a name="requirements"></a>需求

**標題:** atltype.h

## <a name="csizecsize"></a><a name="csize"></a>大小:大小

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
`cx`設定的成員`CSize`。

*因特西*<br/>
`cy`設定的成員`CSize`。

*initSize*<br/>
[用於](/windows/win32/api/windef/ns-windef-size)初始化`CSize``CSize`的 SIZE 結構或物件。

*initPt*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)用於初始化`CPoint``CSize`的 POINT 結構或物件。

*dwSize*<br/>
DWORD 用於初始`CSize`化 。 低階單詞是`cx`成員,高階單詞是`cy`成員。

### <a name="remarks"></a>備註

如果未給出參數,`cx``cy`並且 初始化為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a>大小::運算符 |

檢查兩種大小之間的相等性。

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>備註

如果大小相等,則返回非零,其他為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a>CSize::操作員!*

檢查兩種大小之間的不等式。

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>備註

如果大小不相等,則返回非零,否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a>大小::操作員 |

為此新增大小`CSize`。

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a>大小::運算子 -*

從中`CSize`減去大小。

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a>CSize:運算符 |

這些運算符將此值`CSize`添加到參數的值中。

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>備註

請參閱以下各個運算子的說明:

- **運算子 +(** *大小* **)**

  此操作將添加兩`CSize`個值。

- **運算子 +(***點***)**

  此操作按此值`CSize`偏移(移動[)POINT(](/previous-versions/dd162805\(v=vs.85\))或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) 值。 此值`cx``CSize`的`cy`和成員將添加到值`x``y`和資料成員`POINT`中。 它類似於[CPoint::運算符 *](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)的版本,它採用[SIZE](/windows/win32/api/windef/ns-windef-size)參數。

- **運算子 +(** *lpRect* **)**

   此操作按此值`CSize`偏移(移動[)RECT(](/previous-versions/dd162897\(v=vs.85\))或[CRect](../../atl-mfc-shared/reference/crect-class.md)) 值。 此值`cx``CSize``cy`的與成員將添加`RECT`到`left``top`值`right`的`bottom`、 資料成員中。 它類似於[CRect::運算符 *](../../atl-mfc-shared/reference/crect-class.md#operator_add)的版本,它採用[SIZE](/windows/win32/api/windef/ns-windef-size)參數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a>CSize:運算子 -

這些運算符的前三個將此值`CSize`減去參數的值。

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>備註

第四個運算符,一元減號,更改`CSize`值的符號。 請參閱以下各個運算子的說明:

- **運算子 ─(** *尺寸* **)**

  此操作減去兩`CSize`個值。

- **運算子 ─(***點***)**

  此操作按此值`CSize`的累加反反偏移(移動[)POINT](/previous-versions/dd162805\(v=vs.85\))或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)值。 此值`cx`的`cy``CSize`和將從`x``y``POINT`值和數據成員中減去。 它類似於[CPoint::運算子](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)的版本 - 它採用[SIZE](/windows/win32/api/windef/ns-windef-size)參數。

- 運算子 *-(lpRect)* **)** **operator -(**

  此操作通過此值`CSize`的累加反反偏移(移動[)RECT](/previous-versions/dd162897\(v=vs.85\))或[CRect](../../atl-mfc-shared/reference/crect-class.md)值。 此值`cx``CSize``cy`的和成員將`bottom``RECT`從值`left`的`top`、`right`資料成員中減去。 它類似於[CRect:::運算子](../../atl-mfc-shared/reference/crect-class.md#operator_-)的版本 - 它採用[SIZE](/windows/win32/api/windef/ns-windef-size)參數。

- **運算子 -()**

  此操作返回此值`CSize`的累加反數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint 類別](../../atl-mfc-shared/reference/cpoint-class.md)
