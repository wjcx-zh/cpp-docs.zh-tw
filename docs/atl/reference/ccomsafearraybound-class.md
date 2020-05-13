---
title: CComSafeArray綁定類
ms.date: 05/06/2019
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: 2c2f8b787e5366ec893538a88049f6f53dc35caf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327388"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArray綁定類

此類是[SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound)結構的包裝器。

## <a name="syntax"></a>語法

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CComSafeArray綁定](#ccomsafearraybound)|建構函式。|
|[GetCount](#getcount)|調用此方法以返回元素數。|
|[取得下限](#getlowerbound)|調用此方法以返回下限。|
|[取得上部](#getupperbound)|調用此方法以返回上限。|
|[設定計數](#setcount)|調用此方法以設置元素數。|
|[設定下限](#setlowerbound)|調用此方法以設置下限。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算符 |](#operator_eq)|將`CComSafeArrayBound`設為新值。|

## <a name="remarks"></a>備註

此類是[CComSafeArray](../../atl/reference/ccomsafearray-class.md)`SAFEARRAYBOUND`使用的結構的包裝器。 它提供了查詢和設置`CComSafeArray`物件單個維度的上限和下限及其包含的元素數的方法。 多維`CComSafeArray`物件`CComSafeArrayBound`使用 物件陣列,每個維度一個。 因此,當使用[GetCount](#getcount)等方法時,請注意此方法不會返回多維陣列中的元素總數。

**標頭︰** atlsafe.h

## <a name="requirements"></a>需求

**標頭︰** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a>CComSafeArray綁定::CcomSafearray綁定

建構函式。

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>參數

*ulCount*<br/>
陣列中的項目數。

*lLowerBound*<br/>
對陣列進行編號的下限。

### <a name="remarks"></a>備註

如果要從C++程序訪問陣列,建議將下限定義為 0。 如果陣列要與其他語言(如 Visual Basic)一起使用,則最好使用不同的下限值。

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a>CComSafeArray綁定::取得計數

調用此方法以返回元素數。

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>傳回值

返回元素數。

### <a name="remarks"></a>備註

如果關聯的`CComSafeArray`物件表示多維陣列,則此方法將僅返回最右側維度中的元素總數。 使用[CComSafeArray:getCount](../../atl/reference/ccomsafearray-class.md#getcount)獲取元素的總數。

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a>CComSafeArray綁定::獲取下限

調用此方法以返回下限。

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>傳回值

返回`CComSafeArrayBound`物件的下限。

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a>CComSafeArray綁定::獲取上部

調用此方法以返回上限。

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>傳回值

返回`CComSafeArrayBound`物件的上限。

### <a name="remarks"></a>備註

上限取決於元素數和下限值。 例如,如果下限為 0,元素數為 10,則上限將自動設置為 9。

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a>CComSafeArray綁定::操作員 |

將`CComSafeArrayBound`設為新值。

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>參數

*綁定*<br/>
`CComSafeArrayBound` 物件。

*ulCount*<br/>
項目的數目。

### <a name="return-value"></a>傳回值

返回指向對象`CComSafeArrayBound`的指標。

### <a name="remarks"></a>備註

可以使用`CComSafeArrayBound`現有`CComSafeArrayBound`分配物件,也可以通過提供元素數來分配該物件,在這種情況下,默認情況下下限設置為 0。

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a>CComSafeArray綁定::設定計數

調用此方法以設置元素數。

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>參數

*ulCount*<br/>
項目的數目。

### <a name="return-value"></a>傳回值

返回`CComSafeArrayBound`物件中的元素數。

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a>CComSafeArray綁定::設定下限

調用此方法以設置下限。

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>參數

*lLowerBound*<br/>
下限。

### <a name="return-value"></a>傳回值

返回`CComSafeArrayBound`物件的新下限。

### <a name="remarks"></a>備註

如果要從 Visual C++ 程式訪問陣列,建議將下限定義為 0。 如果陣列要與其他語言(如 Visual Basic)一起使用,則最好使用不同的下限值。

上限取決於元素數和下限值。 例如,如果下限為 0,元素數為 10,則上限將自動設置為 9。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
