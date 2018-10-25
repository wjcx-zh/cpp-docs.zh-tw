---
title: 匯入 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 046a6eb0d1033efb44dd9f34806e747e1fafd700
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071111"
---
# <a name="import"></a>import

指定另一個.idl、.odl 或標頭檔包含您想要從您主要的 IDL 中參考的定義。

## <a name="syntax"></a>語法

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>參數

*idl_file*<br/>
您要匯入類型程式庫目前專案的.idl 檔案的名稱。

## <a name="remarks"></a>備註

**匯入**c + + 屬性會造成`#import`陳述式置於以下`import "docobj.idl"`產生的.idl 檔案中的陳述式。 **匯入**屬性有相同的功能[匯入](/windows/desktop/Midl/import)MIDL 屬性。

**匯入**屬性只會將指定的檔案放入您的專案; 將產生的.idl 檔案**匯入**屬性不會讓您指定的檔案中的建構呼叫從來源程式碼在您的專案。  若要從原始碼專案中，在指定的檔案呼叫建構，請使用[#import](../../preprocessor/hash-import-directive-cpp.md)並`embedded_idl`屬性，或者您可以包含的.h 檔案*idl_file*.h 檔案存在，則。

## <a name="example"></a>範例

下列程式碼範例：

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

會產生下列程式碼產生的.idl 檔案中：

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
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)