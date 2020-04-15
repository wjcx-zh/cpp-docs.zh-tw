---
title: CAutoPtrList 類別
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: 48c7ad6fe13c5f5fbbe5829c25ce1c27896841be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318808"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList 類別

此類提供在構造智慧指標清單時有用的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>參數

*E*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAutoPtr 清單:CAutoPtr 清單](#cautoptrlist)|建構函式。|

## <a name="remarks"></a>備註

此類提供一個建構函數,並從[CAtlList](../../atl/reference/catllist-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)派生方法,以幫助創建儲存智慧指標的清單物件。 類[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)為陣列物件提供了類似的函數。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cautoptrlistcautoptrlist"></a><a name="cautoptrlist"></a>CAutoPtr 清單:CAutoPtr 清單

建構函式。

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
塊大小,預設值為 10。

### <a name="remarks"></a>備註

塊大小是需要新元素時分配的記憶體量的度量。 較大的塊大小減少了對記憶體分配例程的調用,但使用的資源更多。

## <a name="see-also"></a>另請參閱

[CAtlList 類別](../../atl/reference/catllist-class.md)<br/>
[CAutoPtr 元素類別](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
