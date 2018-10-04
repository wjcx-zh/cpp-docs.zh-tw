---
title: 大小寫 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89a8479564048ec7313fee17a444f3e8d34443b0
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790970"
---
# <a name="case-c"></a>case (C++)

搭配[switch_type](switch-type.md)屬性中**聯集**。

## <a name="syntax"></a>語法

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>參數

*值*<br/>
可能的輸入的值，您要提供處理。 型別**值**可以是下列類型之一：

- `int`

- `char`

- `boolean`

- `enum`

或此型別的識別項。

## <a name="remarks"></a>備註

**案例**c + + 屬性具有相同的功能**案例**MIDL 屬性。 這個屬性只能搭配[switch_type](switch-type.md)屬性。

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
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)  