---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 7a1d9bd64a28fa7c08477c6011dc0e8236b7bcf6
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521248"
---
# <a name="custom-c"></a>custom (C++)

在類型程式庫中定義物件的中繼資料。

## <a name="syntax"></a>語法

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>參數

*uuid*<br/>
唯一 ID。

*value*<br/>
可以放入 variant 中的值。

## <a name="remarks"></a>備註

**自訂**c + + 屬性會導致資訊放入類型程式庫中。 您將需要一個從型別程式庫讀取自訂值的工具。

**自訂**屬性的功能與[自訂](/windows/win32/Midl/custom)MIDL 屬性相同。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

- **適用**于：非 COM `interface` 、 `idl_module` 方法、介面成員、介面參數、、、、 **`typedef`** **`class`** **`enum`** **`union`** 和 **`struct`** 類型。
- 可**重複**：是。
- **必要的屬性**： **coclass** （在類別上使用時）。
- **不正確屬性**： None。

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[介面屬性](interface-attributes.md)
