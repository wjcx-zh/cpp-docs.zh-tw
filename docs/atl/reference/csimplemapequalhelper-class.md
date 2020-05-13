---
title: C 簡單映射平等説明者類
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: d137a35a517ea93139f036f6e9a7a8de06d518a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330745"
---
# <a name="csimplemapequalhelper-class"></a>C 簡單映射平等説明者類

此類是[CSimpleMap](../../atl/reference/csimplemap-class.md)類的幫助程式。

## <a name="syntax"></a>語法

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>參數

*TKey*<br/>
關鍵元素。

*TVal*<br/>
值元素。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleMap平等説明者::是平等密鑰](#isequalkey)|(靜態)測試兩個鍵的相等性。|
|[CSimpleMap 等值説明者::等於值](#isequalvalue)|(靜態)測試兩個值的相等性。|

## <a name="remarks"></a>備註

此特徵類是對`CSimpleMap`類的補充。 它提供了比較兩`CSimpleMap`個物件元素(特別是鍵和值元件)的相等性的方法。 預設情況下,使用**運算符 _()** 比較鍵和值,但如果地圖包含缺少其自身相等運算符的複雜數據類型,則可以重寫此類以提供所需的額外功能。

## <a name="requirements"></a>需求

**標題:** atlsimpcoll.h

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a>CSimpleMap平等説明者::是平等密鑰

測試兩個鍵的相等性。

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>參數

*k1*<br/>
第一個鍵。

*k2*<br/>
第二個鍵。

### <a name="return-value"></a>傳回值

如果鍵相等,則返回 true,否則為 false。

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a>CSimpleMap 等值説明者::等於值

測試兩個值的相等性。

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>參數

*v1*<br/>
第一個值。

*v2*<br/>
第二個值。

### <a name="return-value"></a>傳回值

如果值相等,則返回 true,否則為 false。

## <a name="see-also"></a>另請參閱

[C 簡單映射平等説明者假類](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
