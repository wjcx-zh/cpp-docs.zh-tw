---
title: 物件 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14bb20cae26ecb012362b65f86aae5e422170a1a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790674"
---
# <a name="object-c"></a>object (C++)

識別自訂的介面。

## <a name="syntax"></a>語法

```cpp
[object]
```

## <a name="remarks"></a>備註

上述介面定義，當**物件**c + + 屬性會將介面放在.idl 檔中，做為自訂的介面。

任何標示為物件的介面必須繼承自`IUnknown`。 此條件成立，如果任何基底介面繼承自`IUnknown`。 如果沒有基底介面繼承自`IUnknown`，編譯器會以標記的介面**物件**衍生自`IUnknown`。

## <a name="example"></a>範例

請參閱[nonbrowsable](nonbrowsable.md)如需如何使用的範例**物件**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)  