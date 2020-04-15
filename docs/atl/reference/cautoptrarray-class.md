---
title: CAutoPtrarray 類別
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 93fc5cfea4ea655e57e785ca234df59fe10d6570
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318888"
---
# <a name="cautoptrarray-class"></a>CAutoPtrarray 類別

此類提供了在構造智慧指標陣列時有用的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>參數

*E*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAutoPtrarray:CAutoPtrarray](#cautoptrarray)|建構函式。|

## <a name="remarks"></a>備註

此類提供構造函數,並從[CAtlArray](../../atl/reference/catlarray-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)派生方法,以幫助創建儲存智慧指標的集合類物件。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a>CAutoPtrarray:CAutoPtrarray

建構函式。

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>備註

初始化智能指標陣列。

## <a name="see-also"></a>另請參閱

[CAtlarray 類別](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtr 元素類別](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList 類別](../../atl/reference/cautoptrlist-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
