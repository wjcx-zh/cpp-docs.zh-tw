---
title: helpcontext (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 22023b4087c67b62d540d021fa06fd3582c7e4e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409664"
---
# <a name="helpcontext"></a>helpcontext

指定的內容識別碼，可讓使用者檢視中此項目相關的資訊**協助**檔案。

## <a name="syntax"></a>語法

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>參數

*id*<br/>
說明主題的內容識別碼。 請參閱[HTML 說明：您的程式的即時線上說明](../../mfc/html-help-context-sensitive-help-for-your-programs.md)如需有關內容識別碼。

## <a name="remarks"></a>備註

**Helpcontext** C++屬性具有相同的功能[helpcontext](/windows/desktop/Midl/helpcontext) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[defaultvalue](defaultvalue.md)如需如何使用的範例**helpcontext**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**， **typedef**，**類別**、 方法、 屬性|
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
[helpstring](helpstring.md)