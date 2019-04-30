---
title: 唯讀 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.readonly
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
ms.openlocfilehash: 7eea071b62130c65fbb46ebc8827fc2b428c4c0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407337"
---
# <a name="readonly-c"></a>readonly (C++)

禁止指派給資料成員。

## <a name="syntax"></a>語法

```cpp
[readonly]
```

## <a name="remarks"></a>備註

**readonly** C++ 屬性的功能與 [readonly](/windows/desktop/Midl/readonly) MIDL 屬性相同。

如果您想要禁止修改方法參數，則請使用 [in](in-cpp.md) 屬性。

## <a name="example"></a>範例

下列程式碼示範 **readonly** 屬性的用法：

```cpp
// cpp_attr_ref_readonly.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]
__interface IFireTabCtrl
{
   [readonly, id(1)] int i();
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[資料成員屬性](data-member-attributes.md)