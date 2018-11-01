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
ms.openlocfilehash: 69976cab9caed653a8278f80821569b613f690eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502735"
---
# <a name="variantt-class"></a>_variant_t 類別

**Microsoft 專屬**

A **_variant_t**物件會封裝`VARIANT`資料型別。 此類別管理資源配置和解除配置並函式呼叫`VariantInit`和`VariantClear`視情況。

### <a name="construction"></a>建構

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|建構 **_variant_t**物件。|

### <a name="operations"></a>作業

|||
|-|-|
|[Attach](../cpp/variant-t-attach.md)|附加`VARIANT`物件插入 **_variant_t**物件。|
|[清除](../cpp/variant-t-clear.md)|清除封裝`VARIANT`物件。|
|[ChangeType](../cpp/variant-t-changetype.md)|變更的型別 **_variant_t**指定的物件`VARTYPE`。|
|[Detach](../cpp/variant-t-detach.md)|中斷連結封裝`VARIANT`物件，這個 **_variant_t**物件。|
|[SetString](../cpp/variant-t-setstring.md)|將字串指派給這個 **_variant_t**物件。|

### <a name="operators"></a>運算子

|||
|-|-|
|[運算子 =](../cpp/variant-t-operator-equal.md)|將新的值指派給現有 **_variant_t**物件。|
|[運算子 = =、 ！ =](../cpp/variant-t-relational-operators.md)|比較兩個 **_variant_t**物件是否相等或不等比較。|
|[擷取器](../cpp/variant-t-extractors.md)|資料擷取封裝`VARIANT`物件。|

**結束 Microsoft 專屬**

## <a name="requirements"></a>需求

**標頭：** \<comutil.h >

**Lib:** comsuppw.lib 或 comsuppwd.lib (請參閱 < [/zc: wchar_t （wchar_t 是原生型別）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)