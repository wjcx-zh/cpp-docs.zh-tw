---
title: helpstringcontext （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: d292dd53ff3009a571dd5b0a1ba102e75b648e4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533597"
---
# <a name="helpstringcontext"></a>helpstringcontext

指定.hlp 或.chm 檔案中的說明主題的識別碼。

## <a name="syntax"></a>語法

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>參數

*contextID*<br/>
在 32 位元說明內容識別碼**協助**檔案。

## <a name="remarks"></a>備註

**Helpstringcontext** c + + 屬性具有相同的功能[helpstringcontext](/windows/desktop/Midl/helpstringcontext) ODL 屬性。

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
|**適用於**|**類別**，**介面**，介面方法|
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