---
title: < > helpstring （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: d22ecf5a7131a1368abf2b1fbd8261ec6195b51e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166961"
---
# <a name="helpstring"></a>helpstring

指定用來描述所套用之項目的字元字串。

## <a name="syntax"></a>語法

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>參數

*string*<br/>
說明字串的文字。

## <a name="remarks"></a>備註

**< > Helpstring** C++屬性具有與[< > helpstring](/windows/win32/Midl/helpstring) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何使用 **< > helpstring**的範例，請參閱[defaultvalue](defaultvalue.md)的範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**、 **typedef**、**類別**、方法、屬性|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)
