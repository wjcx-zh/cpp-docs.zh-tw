---
title: CSimplearray 平等説明者假類
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 5eca3145d64895e34b599fbf83834af142b65973
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330888"
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimplearray 平等説明者假類

此類是[CSimpleArray](../../atl/reference/csimplearray-class.md)類的幫助程式。

## <a name="syntax"></a>語法

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>參數

*T*<br/>
派生類。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimplearray 平等説明者False::是平等的](#isequal)|(靜態)返回 false。|

## <a name="remarks"></a>備註

此特徵類是對類的補充`CSimpleArray`。 它總是返回 false,此外,如果引用 false,則`ATLASSERT`調用 false。 在相等性測試定義不充分的情況下,此類允許包含元素的陣列對大多數方法正確運行,但對於依賴於[CSimplearray::find](../../atl/reference/csimplearray-class.md#find)等方法,以定義良好的方式失敗。

## <a name="requirements"></a>需求

**標題:** atlsimpcoll.h

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimplearray 平等説明者False::是平等的

傳回 false。

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>傳回值

傳回 false。

### <a name="remarks"></a>備註

此方法始終返回 false,如果引用`ATLASSERT`, 則調用 false 參數。 目的是`CSimpleArrayEqualHelperFalse::IsEqual`在未充分定義相等性測試時,強制使用比較的方法以定義明確的方式失敗。

## <a name="see-also"></a>另請參閱

[CSimplearray 平等説明者類](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
