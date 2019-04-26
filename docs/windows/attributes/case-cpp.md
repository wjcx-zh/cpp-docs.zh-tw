---
title: 案例 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: b3058f2fe6f35e1b11d4790780cb0fcdcaada706
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148432"
---
# <a name="case-c"></a>case (C++)

搭配[switch_type](switch-type.md)屬性中**聯集**。

## <a name="syntax"></a>語法

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>參數

*value*<br/>
可能的輸入的值，您要提供處理。 型別**值**可以是下列類型之一：

- `int`

- `char`

- `boolean`

- `enum`

或此型別的識別項。

## <a name="remarks"></a>備註

**案例**C++屬性具有相同的功能**案例**MIDL 屬性。 這個屬性只能搭配[switch_type](switch-type.md)屬性。

## <a name="example"></a>範例

下列程式碼範例將示範用法**案例**屬性：

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
|**適用於**|成員**類別**或**結構**|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)