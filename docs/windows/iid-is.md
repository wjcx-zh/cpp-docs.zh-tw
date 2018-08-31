---
title: iid_is |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 597d4c2e6fa9904906c2971c3c442a9f26779834
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215074"
---
# <a name="iidis"></a>iid_is

指定的介面指標所指向的 COM 介面的 IID。

## <a name="syntax"></a>語法

```cpp
[ iid_is(
   "expression"
) ]
```

### <a name="parameters"></a>參數

*運算式*  
介面指標所指向的 C 語言運算式，指定 COM 介面的 IID。

## <a name="remarks"></a>備註

**Iid_is** c + + 屬性具有相同的功能[iid_is](/windows/desktop/Midl/iid-is) MIDL 屬性。

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
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[參數屬性](../windows/parameter-attributes.md)  