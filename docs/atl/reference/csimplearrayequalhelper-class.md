---
title: CSimplearray 平等説明者類
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 386b005777b3e31dd74916a41bc5af2ab82df210
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330875"
---
# <a name="csimplearrayequalhelper-class"></a>CSimplearray 平等説明者類

此類是[CSimpleArray](../../atl/reference/csimplearray-class.md)類的幫助程式。

## <a name="syntax"></a>語法

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>參數

*T*<br/>
派生類。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimplearray 平等説明者::是相等的](#isequal)|(靜態)測試兩`CSimpleArray`個物件元素的相等性。|

## <a name="remarks"></a>備註

此特徵類是對`CSimpleArray`類的補充。 它提供了一種比較存儲在物件中的兩個`CSimpleArray`元素的方法。 預設情況下,使用**運算符 _()** 比較元素,但如果陣列包含缺少其自身相等運算符的複雜數據類型,則需要重寫此類。

## <a name="requirements"></a>需求

**標題:** atlsimpcoll.h

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a>CSimplearray 平等説明者::是相等的

測試兩`CSimpleArray`個物件元素的相等性。

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>參數

*t1*<br/>
類型  的物件。

*t2*<br/>
類型  的物件。

### <a name="return-value"></a>傳回值

如果元素相等,則返回 true,否則為 false。

## <a name="see-also"></a>另請參閱

[CSimplearray 類別](../../atl/reference/csimplearray-class.md)<br/>
[CSimplearray 平等説明者假類](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
