---
title: nonextensible （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: 332f61148ccf8cb5816e8bd347181ac9d130a730
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512440"
---
# <a name="nonextensible"></a>nonextensible

指定`IDispatch`實作只包括屬性和方法介面描述中所列，而且無法在執行階段延伸與其他成員。

## <a name="syntax"></a>語法

```cpp
[nonextensible]
```

## <a name="remarks"></a>備註

**Nonextensible** c + + 屬性具有相同的功能[nonextensible](/windows/desktop/Midl/nonextensible) MIDL 屬性。

利用**nonextensible**也需要[oleautomation](oleautomation.md)屬性。

## <a name="example"></a>範例

下列程式碼顯示的其中一種用法**nonextensible**屬性：

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|`dual` 和`oleautomation`，或 `dispinterface`|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)