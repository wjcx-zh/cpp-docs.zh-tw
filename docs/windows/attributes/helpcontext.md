---
title: 'helpcoNtext (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 60e6bf66e088872a357751e4a7b7e043cd9b4dfc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845246"
---
# <a name="helpcontext"></a>helpcontext

指定內容識別碼，讓使用者可在說明檔中查看此 **元素的相關** 資訊。

## <a name="syntax"></a>語法

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>參數

*id*<br/>
說明主題的內容識別碼。 如需內容識別碼的詳細資訊，請參閱 [HTML 說明：程式的即時線上說明](../../mfc/html-help-context-sensitive-help-for-your-programs.md) 。

## <a name="remarks"></a>備註

**HelpcoNtext** c + + 屬性具有與[helpcoNtext](/windows/win32/Midl/helpcontext) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何使用**helpcoNtext**的範例，請參閱[defaultvalue](defaultvalue.md)範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**interface**、 **`typedef`** 、 **`class`** 、method、property|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
