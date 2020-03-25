---
title: MixIn 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: b302d6e08e401a24b465508d5ddabcae8b16bd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213690"
---
# <a name="mixin-structure"></a>MixIn 結構

確保執行階段類別衍生自 Windows 執行階段介面 (若有的話)，然後才是傳統 COM 介面。

## <a name="syntax"></a>語法

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>參數

*源于*<br/>
衍生自[Implements](implements-structure.md)結構的類型。

*MixInType*<br/>
基底類型。

*hasImplements*<br/>
如果*MixInType*衍生自目前的實作為基底型別，則**為 true** ;否則**為 false** 。

## <a name="remarks"></a>備註

如果類別衍生自 Windows 執行階段和類別 COM 介面，則類別宣告清單必須先列出任何 Windows 執行階段介面，然後是任何傳統的 COM 介面。 **MixIn**可確保以正確的順序指定介面。

## <a name="inheritance-hierarchy"></a>繼承階層

`MixIn`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)
