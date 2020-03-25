---
title: helpstringdll （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 4ec0d959b2fc10fc34bfc7050a1970359dae5bbc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168118"
---
# <a name="helpstringdll"></a>helpstringdll

指定要用來執行檔字串查閱（當地語系化）之 DLL 的名稱。

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
|**適用於**|**類別**，**介面**，介面方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)
