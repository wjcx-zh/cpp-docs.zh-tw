---
title: _variant_t 類別
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: e11d31904fd8e54049f69ee4f6530d511c8c7f4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187748"
---
# <a name="_variant_t-class"></a>_variant_t 類別

**Microsoft 專屬**

**_Variant_t**物件會封裝 `VARIANT` 的資料類型。 類別會管理資源配置和解除配置，並視需要對 `VariantInit` 和 `VariantClear` 進行函式呼叫。

### <a name="construction"></a>建築業

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|結構 **_variant_t**物件。|

### <a name="operations"></a>作業

|||
|-|-|
|[附加](../cpp/variant-t-attach.md)|將 `VARIANT` 物件附加至 **_variant_t**物件。|
|[Clear](../cpp/variant-t-clear.md)|清除封裝的 `VARIANT` 物件。|
|[ChangeType](../cpp/variant-t-changetype.md)|將 **_variant_t**物件的類型變更為指定的 `VARTYPE`。|
|[卸離](../cpp/variant-t-detach.md)|從這個 **_variant_t**物件卸離封裝的 `VARIANT` 物件。|
|[SetString](../cpp/variant-t-setstring.md)|將字串指派給這個 **_variant_t**物件。|

### <a name="operators"></a>操作員

|||
|-|-|
|[Operator =](../cpp/variant-t-operator-equal.md)|將新值指派給現有的 **_variant_t**物件。|
|[operator = =、！ =](../cpp/variant-t-relational-operators.md)|比較兩個 **_variant_t**的物件是否相等或不相等。|
|[擷取器](../cpp/variant-t-extractors.md)|從封裝的 `VARIANT` 物件中解壓縮資料。|

**END Microsoft 特定的**

## <a name="requirements"></a>需求

**標頭：** \<comutil.h. h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （請參閱[/zc： Wchar_t （Wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)以取得詳細資訊）

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)
