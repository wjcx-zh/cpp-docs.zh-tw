---
title: C 簡單映射平等説明者假類
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: b6bf1d4e3be849004e13e593fb5f4b5cb87f8123
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330732"
---
# <a name="csimplemapequalhelperfalse-class"></a>C 簡單映射平等説明者假類

此類是[CSimpleMap](../../atl/reference/csimplemap-class.md)類的幫助程式。

## <a name="syntax"></a>語法

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 簡單映射平等説明者False::是平等密鑰](#isequalkey)|(靜態)測試兩個鍵的相等性。|
|[C 簡單映射等值説明者False::等於值](#isequalvalue)|(靜態)返回 false。|

## <a name="remarks"></a>備註

此特徵類是對`CSimpleMap`類的補充。 它提供了一種比較`CSimpleMap`物件中包含的兩個元素的方法,特別是兩個值元素或兩個鍵元素。

值比較將始終返回 false,此外,如果引用該`ATLASSERT`參數 ,則調用該參數為 false。 在相等性測試定義不充分的情況下,此類允許包含鍵/值對的映射在大多數方法中正常運行,但對於依賴於[CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval)等方法,以定義良好的方式失敗。

## <a name="requirements"></a>需求

**標題:** atlsimpcoll.h

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>C 簡單映射平等説明者False::是平等密鑰

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

### <a name="remarks"></a>備註

此方法呼叫[CSimplearray 平等說明器](../../atl/reference/csimplearrayequalhelper-class.md)。

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>C 簡單映射等值説明者False::等於值

傳回 false。

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>傳回值

傳回 false。

### <a name="remarks"></a>備註

此方法始終返回 false,如果引用`ATLASSERT`它 ,則調用 false 參數。 目的是`CSimpleMapEqualHelperFalse::IsEqualValue`在未充分定義相等性測試時,強制使用比較的方法以定義明確的方式失敗。

## <a name="see-also"></a>另請參閱

[C 簡單映射平等説明者類](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
