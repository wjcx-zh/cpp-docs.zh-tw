---
title: 'cpp_quote (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 27be83d123b5433f79c4c8a702197fc6f9f1a753
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833162"
---
# <a name="cpp_quote"></a>cpp_quote

將沒有引號字元的指定字串發出至產生的 .idl 檔案。

## <a name="syntax"></a>語法

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>參數

*陳述式*<br/>
C 指令。

## <a name="remarks"></a>備註

如果您想要將預處理器指示詞放在 .idl 檔中， **cpp_quote** c + + 屬性會很有用。

您也可以使用 **cpp_quote** ，並在 MIDL 編譯中產生 .h 檔案。 例如，如果您有一個使用 c + + IDL 屬性的 c + + 標頭檔，但無法在某些工作中使用此檔案，則您可以將它編譯以建立 MIDL 產生的 .h 檔案，您應該能夠使用它。

**Cpp_quote**屬性具有與[cpp_quote](/windows/win32/Midl/cpp-quote) MIDL 屬性相同的功能。

## <a name="example"></a>範例

請參閱 [雙重](dual.md) 範例中的範例，以瞭解如何使用 **cpp_quote**的範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|任何位置|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)
