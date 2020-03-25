---
title: include （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 39f991bb036dce1c50a9d2ee800d3fec65af7c55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166779"
---
# <a name="include-c"></a>include (C++)

指定要包含在產生的 .idl 檔案中的一或多個標頭檔。

## <a name="syntax"></a>語法

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>參數

*header_file*<br/>
您想要包含在產生的 .idl 檔案中的檔案名。

## <a name="remarks"></a>備註

**Include** C++屬性會導致 `#include` 語句放在產生的 .idl 檔案中的 `import "docobj.idl"` 語句之下。

**Include** C++屬性的功能與[include](/windows/win32/Midl/include) MIDL 屬性相同。

## <a name="example"></a>範例

下列程式碼顯示如何使用**include**的範例。 在此範例中，檔案包含 .h 只包含 `#include` 語句。

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)
