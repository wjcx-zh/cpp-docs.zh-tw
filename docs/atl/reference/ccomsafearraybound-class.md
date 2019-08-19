---
title: CComSafeArrayBound 類別
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
ms.openlocfilehash: bd77c2a788e769c74518d73b45c3c05ff27b3f58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496903"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound 類別

這個類別是[SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-tagsafearraybound)結構的包裝函式。

## <a name="syntax"></a>語法

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|建構函式。|
|[GetCount](#getcount)|呼叫這個方法, 以傳回元素的數目。|
|[GetLowerBound](#getlowerbound)|呼叫這個方法, 以傳回下限。|
|[GetUpperBound](#getupperbound)|呼叫這個方法, 以傳回上限。|
|[SetCount](#setcount)|呼叫這個方法來設定元素的數目。|
|[SetLowerBound](#setlowerbound)|呼叫這個方法以設定下限。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](#operator_eq)|將設定`CComSafeArrayBound`為新的值。|

## <a name="remarks"></a>備註

這個類別是`SAFEARRAYBOUND` [CComSafeArray](../../atl/reference/ccomsafearray-class.md)所使用之結構的包裝函式。 它會提供方法來查詢和設定`CComSafeArray`物件的單一維度上限和下限, 以及它所包含的元素數目。 多維度`CComSafeArrayBound`物件使用物件的陣列, 每個維度各一個。 `CComSafeArray` 因此, 使用[GetCount](#getcount)之類的方法時, 請注意, 這個方法不會傳回多維陣列中的元素總數。

**標頭︰** atlsafe.h

## <a name="requirements"></a>需求

**標頭︰** atlsafe.h

##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

建構函式。

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>參數

*ulCount*<br/>
陣列中的項目數。

*lLowerBound*<br/>
陣列的數位下限。

### <a name="remarks"></a>備註

如果要從C++程式存取陣列, 建議您將下限定義為0。 如果陣列要與其他語言搭配使用, 例如 Visual Basic, 最好使用不同的下限值。

##  <a name="getcount"></a>CComSafeArrayBound:: GetCount

呼叫這個方法, 以傳回元素的數目。

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回元素的數目。

### <a name="remarks"></a>備註

如果相關聯`CComSafeArray`的物件代表多維陣列, 這個方法只會傳回最右邊維度中的元素總數。 請使用[CComSafeArray:: GetCount](../../atl/reference/ccomsafearray-class.md#getcount)取得元素的總數。

##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound

呼叫這個方法, 以傳回下限。

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>傳回值

傳回`CComSafeArrayBound`物件的下限。

##  <a name="getupperbound"></a>CComSafeArrayBound:: System.array.getupperbound

呼叫這個方法, 以傳回上限。

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>傳回值

傳回`CComSafeArrayBound`物件的上限。

### <a name="remarks"></a>備註

上限取決於元素的數目和下限值。 例如, 如果下限為 0, 而元素數目為 10, 則上限會自動設定為9。

##  <a name="operator_eq"></a>CComSafeArrayBound:: operator =

將設定`CComSafeArrayBound`為新的值。

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>參數

*限制*<br/>
          `CComSafeArrayBound` 物件。

*ulCount*<br/>
元素數。

### <a name="return-value"></a>傳回值

傳回`CComSafeArrayBound`物件的指標。

### <a name="remarks"></a>備註

物件可以使用現有`CComSafeArrayBound`的來指派, 或藉由提供專案數目, 在這種情況下, 下限預設會設定為0。 `CComSafeArrayBound`

##  <a name="setcount"></a>CComSafeArrayBound::SetCount

呼叫這個方法來設定元素的數目。

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>參數

*ulCount*<br/>
元素數。

### <a name="return-value"></a>傳回值

傳回`CComSafeArrayBound`物件中的元素數目。

##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound

呼叫這個方法以設定下限。

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>參數

*lLowerBound*<br/>
下限。

### <a name="return-value"></a>傳回值

傳回`CComSafeArrayBound`物件的新下限。

### <a name="remarks"></a>備註

如果要從視覺效果C++程式存取陣列, 建議您將下限定義為0。 如果陣列要與其他語言搭配使用, 例如 Visual Basic, 最好使用不同的下限值。

上限取決於元素的數目和下限值。 例如, 如果下限為 0, 而元素數目為 10, 則上限會自動設定為9。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
