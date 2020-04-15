---
title: C介面清單類別
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 0a7fd781c63e4ea084cf078e49fc9efb9cfa2d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326784"
---
# <a name="cinterfacelist-class"></a>C介面清單類別

此類提供了構造 COM 介面指標清單時有用的方法。

## <a name="syntax"></a>語法

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[C介面清單:C介面清單](#cinterfacelist)|介面清單的構造函數。|

## <a name="remarks"></a>備註

此類提供用於創建 COM 介面指標清單的建構函數和派生方法。 當需要陣列時,請使用[CInterfaceArray。](../../atl/reference/cinterfacearray-class.md)

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a>C介面清單:C介面清單

介面清單的構造函數。

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
塊大小,預設值為 10。

### <a name="remarks"></a>備註

塊大小是需要新元素時分配的記憶體量的度量。 較大的塊大小減少了對記憶體分配例程的調用,但使用的資源更多。

## <a name="see-also"></a>另請參閱

[CAtlList 類別](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr 類別](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtr 元素類別](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
