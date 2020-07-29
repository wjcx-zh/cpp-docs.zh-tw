---
title: case （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: 23330b7b220873725dc566df947f3f3596160029
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232803"
---
# <a name="case-c"></a>case (C++)

與中的[switch_type](switch-type.md)屬性搭配使用 **`union`** 。

## <a name="syntax"></a>語法

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>參數

*value*<br/>
您想要提供處理的可能輸入值。 **值**的類型可以是下列其中一種類型：

- **`int`**

- **`char`**

- `boolean`

- **`enum`**

或這類類型的識別碼。

## <a name="remarks"></a>備註

**Case** c + + 屬性的功能與**case** MIDL 屬性相同。 這個屬性只會與[switch_type](switch-type.md)屬性搭配使用。

## <a name="example"></a>範例

下列程式碼顯示**case**屬性的用法：

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|或的成員 **`class`****`struct`**|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)
