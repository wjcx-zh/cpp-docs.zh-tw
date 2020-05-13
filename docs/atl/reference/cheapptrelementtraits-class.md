---
title: CHeapPtr 元素類別
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: f09da968b264463eba759372e4e0756397e9978e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326881"
---
# <a name="cheapptrelementtraits-class"></a>CHeapPtr 元素類別

此類提供在創建堆指標集合時有用的方法、靜態函數和 typedef。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合類中的物件類型。

*配置器*<br/>
要使用的記憶體分配類。 預設值為[CCRT 分配器](../../atl/reference/ccrtallocator-class.md)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CHeapPtr元素::INARGTYPE](#inargtype)|用於向集合類物件添加元素的數據類型。|
|[CHeapPtr元素::OUTARGTYPE](#outargtype)|用於從集合類物件檢索元素的數據類型。|

## <a name="remarks"></a>備註

此類提供用於幫助創建包含堆指標的集合類物件的方法、靜態函數和 typedef。 類別`CHeapPtrList`的類別`CHeapPtrElementTraits`。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[C 預設比較特徵](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素庫](../../atl/reference/celementtraitsbase-class.md)

[CDefault 元素](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cheapptrelementtraitsinargtype"></a><a name="inargtype"></a>CHeapPtr元素::INARGTYPE

用於向集合類物件添加元素的數據類型。

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

## <a name="cheapptrelementtraitsoutargtype"></a><a name="outargtype"></a>CHeapPtr元素::OUTARGTYPE

用於從集合類物件檢索元素的數據類型。

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementtraits 類別](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CComHeapPtr 類別](../../atl/reference/ccomheapptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
