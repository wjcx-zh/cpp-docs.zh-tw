---
title: 'iid_is (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 6a8fe8c7481cd251baff65293607733573f46ea6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832213"
---
# <a name="iid_is"></a>iid_is

指定介面指標所指向之 COM 介面的 IID。

## <a name="syntax"></a>語法

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>參數

*expression*<br/>
C 語言運算式，指定介面指標所指向之 COM 介面的 IID。

## <a name="remarks"></a>備註

**Iid_is** c + + 屬性具有與[iid_is](/windows/win32/Midl/iid-is) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼示範如何使用 **iid_is**：

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面參數，資料成員|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)
