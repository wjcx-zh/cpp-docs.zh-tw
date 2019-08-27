---
title: importlib (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: 92cf335e5c4754595f2c7af2e1aef30d309d2f5f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514604"
---
# <a name="importlib"></a>importlib

讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。

## <a name="syntax"></a>語法

```cpp
[ importlib("tlb_file") ];
```

### <a name="parameters"></a>參數

*tlb_file*<br/>
您要匯入目前專案之類型程式庫中的 .tlb 檔案名稱 (加上引號)。

## <a name="remarks"></a>備註

C++ Importlib`importlib`屬性會將語句放在產生的 .idl 檔案的程式庫區塊中。 **Importlib**屬性具有與[importlib](/windows/win32/Midl/importlib) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示如何使用**importlib**的範例:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
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

[編譯器屬性](compiler-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)