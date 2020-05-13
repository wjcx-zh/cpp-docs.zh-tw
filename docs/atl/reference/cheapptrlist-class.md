---
title: CHeapPtrList 類別
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 0500ab8f76049aeaf1c89355ea5450a93243b734
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326865"
---
# <a name="cheapptrlist-class"></a>CHeapPtrList 類別

此類提供構造堆指標清單時有用的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>參數

*E*<br/>
要存儲在集合類中的物件類型。

*配置器*<br/>
要使用的記憶體分配類。 預設值為[CCRT 分配器](../../atl/reference/ccrtallocator-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHeapPtr 清單:CHeapPtrList](#cheapptrlist)|建構函式。|

## <a name="remarks"></a>備註

此類提供一個構造函數,並從[CAtlList](../../atl/reference/catllist-class.md)和[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)派生方法,以幫助創建記憶體指標的集合類物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cheapptrlistcheapptrlist"></a><a name="cheapptrlist"></a>CHeapPtr 清單:CHeapPtrList

建構函式。

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

塊大小是需要新元素時分配的記憶體量的度量。 較大的塊大小減少了對記憶體分配例程的調用,但使用的資源更多。

## <a name="see-also"></a>另請參閱

[CAtlList 類別](../../atl/reference/catllist-class.md)<br/>
[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtr 元素類別](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
