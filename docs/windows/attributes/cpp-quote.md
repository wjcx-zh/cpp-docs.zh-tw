---
title: cpp_quote （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 451313b5bd1eb5011f1175de5c3bcfe6fb054299
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214912"
---
# <a name="cpp_quote"></a>cpp_quote

將指定的字串（不含引號字元）發出到產生的 .idl 檔案。

## <a name="syntax"></a>語法

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>參數

*陳述式*<br/>
C 指令。

## <a name="remarks"></a>備註

如果您想要將預處理器指示詞放在 .idl 檔案中， **cpp_quote** C++屬性會很有用。

您也可以使用**cpp_quote** ，並產生 .h 檔案做為 MIDL 編譯的一部分。 例如，如果您有使用C++ C++ IDL 屬性的標頭檔，但無法在某些工作中使用此檔案，則您可以編譯它來建立 MIDL 產生的 .h 檔案，您應該能夠使用該檔案。

**Cpp_quote**屬性具有與[cpp_quote](/windows/win32/Midl/cpp-quote) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需使用如何使用**cpp_quote**的範例，請參閱[雙重](dual.md)的範例。

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
