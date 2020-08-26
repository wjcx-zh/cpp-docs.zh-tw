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
ms.openlocfilehash: 9adee1e8b6a46c239aaf6a3c404277b34efd00e2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834748"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound 類別

這個類別是 [SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound) 結構的包裝函式。

## <a name="syntax"></a>語法

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|函式|描述|
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|建構函式。|
|[GetCount](#getcount)|呼叫這個方法來傳回專案數。|
|[GetLowerBound](#getlowerbound)|呼叫這個方法以傳回下限。|
|[System.array.getupperbound](#getupperbound)|呼叫這個方法以傳回上限。|
|[SetCount](#setcount)|呼叫此方法以設定元素的數目。|
|[SetLowerBound](#setlowerbound)|呼叫這個方法來設定下限。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[運算子 =](#operator_eq)|將設定 `CComSafeArrayBound` 為新的值。|

## <a name="remarks"></a>備註

這個類別是 CComSafeArray 所使用之結構的包裝函式 `SAFEARRAYBOUND` 。 [CComSafeArray](../../atl/reference/ccomsafearray-class.md) 它會提供方法，以查詢和設定物件之單一維度的上限和下限 `CComSafeArray` ，以及它所包含的元素數目。 `CComSafeArray`多維度物件會使用物件的陣列 `CComSafeArrayBound` ，每個維度各一個。 因此，使用 [GetCount](#getcount)之類的方法時，請注意，這個方法不會傳回多維度陣列中的元素總數。

**標頭︰** atlsafe.h

## <a name="requirements"></a>規格需求

**標頭︰** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a> CComSafeArrayBound：： CComSafeArrayBound

建構函式。

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>參數

*ulCount*<br/>
陣列中的項目數。

*lLowerBound*<br/>
陣列的編號下限。

### <a name="remarks"></a>備註

如果要從 c + + 程式存取陣列，建議將下限定義為0。 如果陣列要與其他語言搭配使用，例如 Visual Basic，最好使用不同的下限值。

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a> CComSafeArrayBound：： GetCount

呼叫這個方法來傳回專案數。

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回元素的數目。

### <a name="remarks"></a>備註

如果相關聯的 `CComSafeArray` 物件表示多維陣列，這個方法只會傳回最右側維度中的元素總數。 使用 [CComSafeArray：： GetCount](../../atl/reference/ccomsafearray-class.md#getcount) 來取得元素總數。

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a> CComSafeArrayBound：： GetLowerBound

呼叫這個方法以傳回下限。

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>傳回值

傳回物件的下限 `CComSafeArrayBound` 。

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a> CComSafeArrayBound：： System.array.getupperbound

呼叫這個方法以傳回上限。

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>傳回值

傳回物件的上限 `CComSafeArrayBound` 。

### <a name="remarks"></a>備註

上限取決於元素數目和下限值。 例如，如果下限為0，而專案數為10，則上限會自動設定為9。

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a> CComSafeArrayBound：： operator =

將設定 `CComSafeArrayBound` 為新的值。

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

傳回物件的指標 `CComSafeArrayBound` 。

### <a name="remarks"></a>備註

您 `CComSafeArrayBound` 可以使用現有的 `CComSafeArrayBound` ，或藉由提供專案數來指派物件，在此情況下，預設會將下限設定為0。

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a> CComSafeArrayBound：： SetCount

呼叫此方法以設定元素的數目。

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>參數

*ulCount*<br/>
項目的數目。

### <a name="return-value"></a>傳回值

傳回物件中的元素數目 `CComSafeArrayBound` 。

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a> CComSafeArrayBound：： SetLowerBound

呼叫這個方法來設定下限。

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>參數

*lLowerBound*<br/>
下限。

### <a name="return-value"></a>傳回值

傳回物件的新下限 `CComSafeArrayBound` 。

### <a name="remarks"></a>備註

如果要從 Visual C++ 程式存取陣列，建議將下限定義為0。 如果陣列要與其他語言搭配使用，例如 Visual Basic，最好使用不同的下限值。

上限取決於元素數目和下限值。 例如，如果下限為0，而專案數為10，則上限會自動設定為9。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
