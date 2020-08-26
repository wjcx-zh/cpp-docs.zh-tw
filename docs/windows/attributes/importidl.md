---
title: 'importidl (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 8f3c2c5c67ac216d096d1082814c561698f3f732
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842243"
---
# <a name="importidl"></a>importidl

將指定的 .idl 檔案插入產生的 .idl 檔案。

## <a name="syntax"></a>語法

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>參數

*idl_file*<br/>
識別您想要與將為應用程式產生的 .idl 檔案合併的 .idl 檔名稱。

## <a name="remarks"></a>備註

**Importidl** c + + 屬性會將*idl_file*) 中的程式庫區塊 (放在程式產生的 .idl 檔案中，而程式庫區段 (*idl_file*) 至程式產生的 .idl 檔案的 [程式庫] 區段。

例如，您可以使用 **importidl**，例如，如果您想要搭配產生的 .idl 檔案使用手動編碼的 .idl 檔案。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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

[編譯器屬性](compiler-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[包括](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
