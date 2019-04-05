---
title: 包含 （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: d9c68601bea4cecd92b371dada5fb086aeb7657f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033693"
---
# <a name="include-c"></a>include (C++)

指定要包含在產生的.idl 檔案中的一或多個標頭檔。

## <a name="syntax"></a>語法

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>參數

*header_file*<br/>
您想要包含在產生的.idl 檔案中的檔案名稱。

## <a name="remarks"></a>備註

**包括**c + + 屬性會造成`#include`陳述式置於以下`import "docobj.idl"`產生的.idl 檔案中的陳述式。

**包括**c + + 屬性具有相同的功能[包含](/windows/desktop/Midl/include)MIDL 屬性。

## <a name="example"></a>範例

下列程式碼示範如何使用**包含**。 例如，檔案 include.h 只包含`#include`陳述式。

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