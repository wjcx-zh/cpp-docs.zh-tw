---
title: importidl （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 6e41a98bef079c92b6df6e7eff203301aa9ceae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166818"
---
# <a name="importidl"></a>importidl

將指定的 .idl 檔案插入產生的 .idl 檔案。

## <a name="syntax"></a>語法

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>參數

*idl_file*<br/>
識別要與將為應用程式產生之 .idl 檔案合併的 .idl 檔案名稱。

## <a name="remarks"></a>備註

**Importidl** C++屬性會將該區段放在程式庫區塊的外部（在*idl_file*中），並將其產生的 .idl 檔案和程式庫區段（在*idl_file*中）放置到程式產生的 .idl 檔案的 [程式庫] 區段中。

例如，如果您想要在產生的 .idl 檔案中使用手動編碼的 .idl 檔案，您可能會想要使用**importidl**。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
