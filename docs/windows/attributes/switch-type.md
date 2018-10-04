---
title: switch_type （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d8ba772b03399b820a04c4f2601f2ab5b357a63f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791027"
---
# <a name="switchtype"></a>switch_type

識別做為等位的判別變數的型別。

## <a name="syntax"></a>語法

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>參數

*type*<br/>
參數型別可以是整數、 字元、 布林值或列舉類型。

## <a name="remarks"></a>備註

**Switch_type** c + + 屬性具有相同的功能[switch_type](/windows/desktop/Midl/switch-type) MIDL 屬性。

不支援 c + + 屬性[封裝等位](/windows/desktop/Midl/encapsulated-unions)。 [Nonencapsulated 等位](/windows/desktop/Midl/nonencapsulated-unions)只支援下列格式：

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>範例

請參閱[案例](case-cpp.md)的範例使用的範例**switch_type**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**typedef**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)  