---
title: '物件 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0c0ff552d8a33ebe70f56b9b186e963cc8e9b3d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843101"
---
# <a name="object-c"></a>object (C++)

識別自訂介面。

## <a name="syntax"></a>語法

```cpp
[object]
```

## <a name="remarks"></a>備註

在介面定義前面時， **object** c + + 屬性會導致將介面放在 .idl 檔中做為自訂介面。

任何標記有物件的介面都必須繼承自 `IUnknown` 。 如果任何基底介面繼承自，就會滿足這個條件 `IUnknown` 。 如果沒有繼承自的基底介面 `IUnknown` ，編譯器將會造成標記有 **物件** 的介面衍生自 `IUnknown` 。

## <a name="example"></a>範例

如需如何使用**物件**的範例，請參閱[nonbrowsable](nonbrowsable.md) 。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**interface**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[自 定義](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
