---
title: library_block （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 405cc1cd5af7dcd689e833764f3da2fdc6d5f703
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214769"
---
# <a name="library_block"></a>library_block

將結構放在 IDL 程式庫區塊內。

## <a name="syntax"></a>語法

```cpp
[library_block]
```

## <a name="remarks"></a>備註

當您將結構放在程式庫區塊內時，您可以確保它會傳遞至類型程式庫，不論是否被參考。 根據預設，只有由[coclass](coclass.md)、分配[介面](dispinterface.md)和[idl_module](idl-module.md)屬性所修改的結構才會放在程式庫區塊中。

## <a name="example"></a>範例

在下列程式碼中，會將自訂介面放在程式庫區塊內。

```cpp
// cpp_attr_ref_library_block.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib")];
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface IMyInterface {
   HRESULT f1();
};
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

[編譯器屬性](compiler-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)
