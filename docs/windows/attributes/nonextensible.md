---
title: nonextensible (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: f2947e223d068ea6cc92a41abe19cb7f920112b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514405"
---
# <a name="nonextensible"></a>nonextensible

`IDispatch`指定執行只包含介面描述中所列的屬性和方法, 而且無法在執行時間以其他成員擴充。

## <a name="syntax"></a>語法

```cpp
[nonextensible]
```

## <a name="remarks"></a>備註

**Nonextensible** C++屬性具有與[nonextensible](/windows/win32/Midl/nonextensible) MIDL 屬性相同的功能。

使用**nonextensible**也需要[oleautomation](oleautomation.md)屬性。

## <a name="example"></a>範例

下列程式碼顯示**nonextensible**屬性的一種用法:

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
|**必要屬性**|`dual`and `oleautomation`、or`dispinterface`|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)