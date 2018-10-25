---
title: cpp_quote （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e67b839b487f7bb457eeadb0f4d0385b025ebc3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080594"
---
# <a name="cppquote"></a>cpp_quote

指定的字串，不能包含單引號字元，發出到產生的.idl 檔案。

## <a name="syntax"></a>語法

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>參數

*statement*<br/>
C 的指令。

## <a name="remarks"></a>備註

**Cpp_quote** c + + 屬性才有用，如果您想要將前置處理器指示詞放在.idl 檔中。

您也可以使用**cpp_quote**和的 MIDL 編譯時產生的.h 檔案。 比方說，如果您有使用 c + + IDL 屬性，但某些工作不能使用此檔案的 c + + 標頭檔，然後您可以編譯它來建立 MIDL 產生的.h 檔案，您應該能夠使用。

**Cpp_quote**屬性有相同的功能[cpp_quote](/windows/desktop/Midl/cpp-quote) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[雙重](dual.md)如需範例使用 使用方式**cpp_quote**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)