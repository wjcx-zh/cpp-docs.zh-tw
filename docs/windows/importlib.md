---
title: importlib |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 3df5a1893567b54337a5c3807fcace6a02154670
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416002"
---
# <a name="importlib"></a>importlib

讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。

## <a name="syntax"></a>語法

```cpp
[ importlib(
   "tlb_file"
) ];
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

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](../windows/compiler-attributes.md)<br/>
[獨立屬性](../windows/stand-alone-attributes.md)<br/>
[import](../windows/import.md)<br/>
[importidl](../windows/importidl.md)<br/>
[include](../windows/include-cpp.md)<br/>
[includelib](../windows/includelib-cpp.md)