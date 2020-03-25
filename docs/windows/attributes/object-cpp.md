---
title: object （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 4545d899c13a1eabf8ea5fb6fe3918fb5f05b626
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214651"
---
# <a name="object-c"></a>object (C++)

識別自訂介面。

## <a name="syntax"></a>語法

```cpp
[object]
```

## <a name="remarks"></a>備註

在介面定義前面時，**物件** C++屬性會使介面放在 .idl 檔案中，做為自訂介面。

任何以物件標記的介面都必須繼承自 `IUnknown`。 如果有任何基底介面繼承自 `IUnknown`，就會滿足這種情況。 如果沒有基底介面繼承自 `IUnknown`，編譯器會導致以**物件**標記的介面衍生自 `IUnknown`。

## <a name="example"></a>範例

如需如何使用**物件**的範例，請參閱[nonbrowsable](nonbrowsable.md) 。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
