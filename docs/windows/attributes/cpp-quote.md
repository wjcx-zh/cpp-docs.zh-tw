---
title: cpp_quote (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 378435ced5a541785b7b32bc9d2f408034d5a2d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148233"
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

**Cpp_quote** C++屬性才有用，如果您想要將前置處理器指示詞放在.idl 檔中。

您也可以使用**cpp_quote**和的 MIDL 編譯時產生的.h 檔案。 例如，如果您有C++使用的標頭檔C++然後 IDL 屬性，但是不能使用這個檔案針對某些工作，您可以編譯它來建立 MIDL 產生的.h 檔案，您應該能夠使用。

**Cpp_quote**屬性有相同的功能[cpp_quote](/windows/desktop/Midl/cpp-quote) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[雙重](dual.md)如需範例使用 使用方式**cpp_quote**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)