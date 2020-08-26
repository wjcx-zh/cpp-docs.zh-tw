---
title: '包含 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 6b75df74ee69ee4f89eb7bf18fb6bcd77d8a6284
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842191"
---
# <a name="include-c"></a>include (C++)

指定要包含在產生的 .idl 檔案中的一或多個標頭檔。

## <a name="syntax"></a>語法

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>參數

*header_file*<br/>
您要包含在產生的 .idl 檔案中的檔案名。

## <a name="remarks"></a>備註

**Include** c + + 屬性會將 `#include` 語句放在產生的 `import "docobj.idl"` .idl 檔案中的語句下方。

**Include** c + + 屬性具有與[include](/windows/win32/Midl/include) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示如何使用 **include**的範例。 在此範例中，檔案包含 .h 只包含 `#include` 語句。

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|任何位置|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)
