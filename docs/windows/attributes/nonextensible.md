---
title: 'nonextensible (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: 01f89c4a06a8e90fd6a539fa5a5a85ebb8067d40
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833032"
---
# <a name="nonextensible"></a>nonextensible

指定 `IDispatch` 執行只包含介面描述中所列出的屬性和方法，而且在執行時間無法以其他成員擴充。

## <a name="syntax"></a>語法

```cpp
[nonextensible]
```

## <a name="remarks"></a>備註

**Nonextensible** c + + 屬性具有與[nonextensible](/windows/win32/Midl/nonextensible) MIDL 屬性相同的功能。

使用 **nonextensible** 也需要 [oleautomation](oleautomation.md) 屬性。

## <a name="example"></a>範例

下列程式碼示範如何使用 **nonextensible** 屬性：

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**interface**|
|**重複**|否|
|**必要的屬性**|`dual` and `oleautomation` 、or `dispinterface`|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)
