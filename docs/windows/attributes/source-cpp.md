---
title: 來源 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: 699ea64de49a4383bc8fb62b2f3b2133d7c496c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407181"
---
# <a name="source-c"></a>source (C++)

在類別上，指定連接點的 COM 物件的來源介面。 在屬性或方法中，表示成員傳回的物件或變數，是事件來源。

## <a name="syntax"></a>語法

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>參數

*interfaces*<br/>
一或多個介面，指定當您將套用的來源屬性的類別。 未在來源套用至屬性或方法時，會使用此參數。

## <a name="remarks"></a>備註

**來源**C++屬性具有相同的功能[來源](/windows/desktop/Midl/source)MIDL 屬性。

您可以使用[預設](default-cpp.md)屬性來指定預設來源介面的物件。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**， **struct**，**介面**|
|**可重複**|否|
|**必要屬性**|`coclass` （當套用至類別或結構）|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[coclass](coclass.md)