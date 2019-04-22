---
title: 物件 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0f544e84e5110761dfd01e25abef4352f055ff5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022355"
---
# <a name="object-c"></a>object (C++)

識別自訂的介面。

## <a name="syntax"></a>語法

```cpp
[object]
```

## <a name="remarks"></a>備註

上述介面定義，當**物件**C++屬性會將介面放在.idl 檔中，做為自訂的介面。

任何標示為物件的介面必須繼承自`IUnknown`。 此條件成立，如果任何基底介面繼承自`IUnknown`。 如果沒有基底介面繼承自`IUnknown`，編譯器會以標記的介面**物件**衍生自`IUnknown`。

## <a name="example"></a>範例

請參閱[nonbrowsable](nonbrowsable.md)如需如何使用的範例**物件**。

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