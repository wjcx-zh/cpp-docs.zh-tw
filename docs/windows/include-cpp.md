---
title: 包含 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 617747a9eda77d8dc2ba21006b649daead9546d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419317"
---
# <a name="include-c"></a>include (C++)

指定要包含在產生的.idl 檔案中的一或多個標頭檔。

## <a name="syntax"></a>語法

```cpp
[ include(
   header_file
) ];
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
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)<br/>
[獨立屬性](../windows/stand-alone-attributes.md)<br/>
[import](../windows/import.md)<br/>
[importidl](../windows/importidl.md)<br/>
[includelib](../windows/includelib-cpp.md)<br/>
[importlib](../windows/importlib.md)  