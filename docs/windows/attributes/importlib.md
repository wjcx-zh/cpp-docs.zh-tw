---
title: importlib （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd43dd8a0fb4660cbe0c631bcb3477ef3d26f0f6
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790986"
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

**Importlib** c + + 屬性會導致`importlib`放在產生的.idl 檔的程式庫區塊的陳述式。 **Importlib**屬性有相同的功能[importlib](/windows/desktop/Midl/importlib) MIDL 屬性。

## <a name="example"></a>範例

下列程式碼示範如何使用**importlib**:

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

如需詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)