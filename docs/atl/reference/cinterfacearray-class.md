---
title: C 介面陣列類別
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: e6efe31989b06f0977ecff156a8f64053dc64ad1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326791"
---
# <a name="cinterfacearray-class"></a>C 介面陣列類別

此類提供了構造 COM 介面指標陣列時有用的方法。

## <a name="syntax"></a>語法

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>參數

*I.*<br/>
指定要儲存的指標類型的 COM 介面。

*皮伊德*<br/>
指向*I*的 IID 的指標。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 介面陣列:C 介面陣列](#cinterfacearray)|介面陣列的構造函數。|

## <a name="remarks"></a>備註

此類提供了用於創建 COM 介面指標數位的建構函數和派生方法。 當需要清單時,請使用[CInterfaceList。](../../atl/reference/cinterfacelist-class.md)

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cinterfacearraycinterfacearray"></a><a name="cinterfacearray"></a>C 介面陣列:C 介面陣列

建構函式。

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>備註

初始化智能指標陣列。

## <a name="see-also"></a>另請參閱

[CAtlarray 類別](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr 類別](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtr 元素類別](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
