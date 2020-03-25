---
title: 選擇性（C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.optional
helpviewer_keywords:
- optional attribute
ms.assetid: 86656a66-8e11-4589-8e30-9b0f34eeed03
ms.openlocfilehash: 6a4fdcd0b8466d2dbf2c034fc4a3ee9ae2df8d0a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214648"
---
# <a name="optional-c"></a>optional (C++)

指定成員函式的選擇性參數。

## <a name="syntax"></a>語法

```cpp
[optional]
```

## <a name="remarks"></a>備註

**選擇性** C++屬性的功能與[選擇性](/windows/win32/Midl/optional)的 MIDL 屬性相同。

## <a name="example"></a>範例

下列程式碼顯示可能使用**選擇性**的方式：

```cpp
// cpp_attr_ref_optional.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)
