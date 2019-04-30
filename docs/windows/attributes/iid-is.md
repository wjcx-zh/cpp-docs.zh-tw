---
title: iid_is (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: b91fb7937bb0e20f2500eace9695bc0ddba21b26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409521"
---
# <a name="iidis"></a>iid_is

指定的介面指標所指向的 COM 介面的 IID。

## <a name="syntax"></a>語法

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>參數

*expression*<br/>
介面指標所指向的 C 語言運算式，指定 COM 介面的 IID。

## <a name="remarks"></a>備註

**Iid_is** C++屬性具有相同的功能[iid_is](/windows/desktop/Midl/iid-is) MIDL 屬性。

## <a name="example"></a>範例

下列程式碼示範如何使用**iid_is**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數，資料成員|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)