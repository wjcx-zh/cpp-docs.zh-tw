---
title: requires_category （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.requires_category
dev_langs:
- C++
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61743dfdb5eb684cbf09705ace4ce2531c292ff4
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790671"
---
# <a name="requirescategory"></a>requires_category

指定目標類別的必要的元件類別目錄。

## <a name="syntax"></a>語法

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>參數

*requires_category*<br/>
所需的類別目錄的識別碼。

## <a name="remarks"></a>備註

**Requires_category** c + + 屬性會指定目標類別所需的元件類別。 如需詳細資訊，請參閱 < [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category)。

此屬性需要[coclass](coclass.md)， [progid](progid.md)，或[vi_progid](vi-progid.md)屬性 （或其中一種表示另一個屬性） 也套用至相同的項目。

## <a name="example"></a>範例

下列程式碼需要的物件實作的控制項類別。

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
class CMyClass {};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|一或多個項目： `coclass`， `progid`，或`vi_progid`。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[implements_category](implements-category.md)  