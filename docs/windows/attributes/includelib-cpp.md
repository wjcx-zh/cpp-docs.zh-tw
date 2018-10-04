---
title: includelib （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6be5bb96f819bf1f1b0ba90d345a3c2d312daeea
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791011"
---
# <a name="includelib-c"></a>includelib (C++)

會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。

## <a name="syntax"></a>語法

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>參數

*name.idl*<br/>
您想要產生的.idl 檔案的一部分的.idl 檔案的名稱。

## <a name="remarks"></a>備註

**Includelib** c + + 屬性會造成的.idl 或.h 檔案之後，在產生的.idl 檔案中，包含`importlib`陳述式。

## <a name="example"></a>範例

下列程式碼所示的.cpp 檔案：

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|是|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)  