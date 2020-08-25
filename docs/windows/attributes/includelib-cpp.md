---
title: 'includelib (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 30e84a6c82ec25e07ca0eb08f64c7aa5b560e9e7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830692"
---
# <a name="includelib-c"></a>includelib (C++)

使 .idl 或 .h 檔案包含在產生的 .idl 檔案中。

## <a name="syntax"></a>語法

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>參數

*名稱 .idl*<br/>
您要包含在產生的 .idl 檔案中的 .idl 檔案名。

## <a name="remarks"></a>備註

**Includelib** c + + 屬性會導致 .idl 或 .h 檔案包含在產生的 .idl 檔案中（在語句之後）。 `importlib`

## <a name="example"></a>範例

下列程式碼會顯示在 .cpp 檔案中：

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|任何位置|
|**重複**|是|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[包括](include-cpp.md)<br/>
[importlib](importlib.md)
