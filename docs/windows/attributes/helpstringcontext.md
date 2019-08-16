---
title: helpstringcoNtext (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: ae48c6216b1f1d987b33eff50acf9d82dc551400
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501496"
---
# <a name="helpstringcontext"></a>helpstringcontext

在 .hlp 或 .chm 檔案中指定說明主題的識別碼。

## <a name="syntax"></a>語法

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>參數

*contextID*<br/>
說明檔中的32位說明內容識別碼 。

## <a name="remarks"></a>備註

**HelpstringcoNtext** C++屬性的功能與[helpstringcoNtext](/windows/win32/Midl/helpstringcontext) ODL 屬性相同。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**,**介面**, 介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[module](module-cpp.md)