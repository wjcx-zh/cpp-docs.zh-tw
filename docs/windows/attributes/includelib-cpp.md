---
title: includelib （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 4022a3f1f2d4ccaabe65c24065be8e1c846d604d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214837"
---
# <a name="includelib-c"></a>includelib (C++)

導致 .idl 或 .h 檔案包含在產生的 .idl 檔案中。

## <a name="syntax"></a>語法

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>參數

*名稱 .idl*<br/>
您想要包含在產生的 .idl 檔案中的 .idl 檔案名稱。

## <a name="remarks"></a>備註

**Includelib** C++屬性會使 .idl 或 .h 檔案包含在產生的 .idl 檔案中（在 `importlib` 語句之後）。

## <a name="example"></a>範例

下列程式碼會顯示在 .cpp 檔案中：

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
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)
