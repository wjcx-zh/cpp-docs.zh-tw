---
title: case （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: da72fff3bb600b5db2fba0ecdfe9c6a768836f3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167328"
---
# <a name="case-c"></a>case (C++)

與聯**集**內的[switch_type](switch-type.md)屬性搭配使用。

## <a name="syntax"></a>語法

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>參數

*value*<br/>
您想要提供處理的可能輸入值。 **值**的類型可以是下列其中一種類型：

- `int`

- `char`

- `boolean`

- `enum`

或這類類型的識別碼。

## <a name="remarks"></a>備註

**Case** C++屬性的功能與**case** MIDL 屬性相同。 這個屬性只會與[switch_type](switch-type.md)屬性搭配使用。

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
|**適用於**|**類別**或**結構**的成員|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)
