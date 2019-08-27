---
title: helpstringdll (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 8d6dddef666f074a57f54b8c9447847ff56d26fd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501472"
---
# <a name="helpstringdll"></a>helpstringdll

指定要用來執行檔字串查閱 (當地語系化) 之 DLL 的名稱。

## <a name="syntax"></a>語法

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>參數

*string*<br/>
要用來執行檔字串查詢的 DLL。

## <a name="remarks"></a>備註

**Helpstringdll** C++屬性具有與[helpstringdll](/windows/win32/Midl/helpstringdll) MIDL 屬性相同的功能。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
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
[方法屬性](method-attributes.md)