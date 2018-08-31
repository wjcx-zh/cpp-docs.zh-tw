---
title: nonextensible |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f24aa8b1aa6b4e2e996ec22062263f785d730d0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222576"
---
# <a name="nonextensible"></a>nonextensible

指定`IDispatch`實作只包括屬性和方法介面描述中所列，而且無法在執行階段延伸與其他成員。

## <a name="syntax"></a>語法

```cpp
[nonextensible]
```

## <a name="remarks"></a>備註

**Nonextensible** c + + 屬性具有相同的功能[nonextensible](/windows/desktop/Midl/nonextensible) MIDL 屬性。

利用**nonextensible**也需要[oleautomation](../windows/oleautomation.md)屬性。

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

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[介面屬性](../windows/interface-attributes.md)  