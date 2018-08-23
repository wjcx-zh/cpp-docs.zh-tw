---
title: satype |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 462dba3caaef53e49203eab6d006ea59d7b23c0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590369"
---
# <a name="satype"></a>satype

指定的資料型別`SAFEARRAY`結構。

## <a name="syntax"></a>語法

```cpp
[ satype(
   data_type
) ]
```

### <a name="parameters"></a>參數

*data_type*  
資料型別`SAFEARRAY`做為參數傳遞至介面方法的資料結構。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數，介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

## <a name="remarks"></a>備註

**Satype** c + + 屬性指定的資料型別`SAFEARRAY`。

> [!NOTE]
> 從卸除的間接取值層級`SAFEARRAY`從它在.cpp 檔案中的宣告方式產生的.idl 檔案中的指標。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>另請參閱

[編譯器屬性](../windows/compiler-attributes.md)  
[參數屬性](../windows/parameter-attributes.md)  
[方法屬性](../windows/method-attributes.md)  
[id](../windows/id.md)  