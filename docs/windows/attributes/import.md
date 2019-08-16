---
title: import (C++ COM 屬性)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: f9ed80bdcc04302c0dee85935f377c8e3dbfd37f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514628"
---
# <a name="import"></a>import

指定另一個 .idl、odl 或標頭檔, 其中包含您想要從主要 IDL 參考的定義。

## <a name="syntax"></a>語法

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>參數

*idl_file*<br/>
您要匯入至目前專案之類型程式庫的 .idl 檔案名稱。

## <a name="remarks"></a>備註

`import "docobj.idl"` **Import** C++屬性會使語句放在產生的.idl檔案中的語句底下。`#import` 匯**入**屬性的功能與匯[入](/windows/win32/Midl/import)MIDL 屬性相同。

匯**入**屬性只會將指定的檔案放入要由專案產生的 .idl 檔案中;匯**入**屬性不允許您從專案中的原始程式碼呼叫指定檔案中的結構。  若要從專案中的原始程式碼呼叫指定檔案中的結構, 請使用[#import](../../preprocessor/hash-import-directive-cpp.md)和`embedded_idl`屬性, 如果 .h 檔案存在, 則可以包含*idl_file*的 .h 檔案。

## <a name="example"></a>範例

下列程式碼範例：

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

會在產生的 .idl 檔案中產生下列程式碼:

```
import "docobj.idl";
import "import.idl";

[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]
library MyLib {
   importlib("stdole2.tlb");
   importlib("olepro32.dll");
...
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)