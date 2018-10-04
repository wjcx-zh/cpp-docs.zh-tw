---
title: rdx （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.rdx
dev_langs:
- C++
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ffee10ea334c6c425aa5ecd81705ef1915dc80c0
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790650"
---
# <a name="rdx"></a>rdx

建立登錄機碼或修改現有的登錄機碼。

## <a name="syntax"></a>語法

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>參數

*key*<br/>
若要建立或開啟金鑰的名稱。

*valuename*<br/>
（選擇性）指定要設定的 [值] 欄位。 如果在索引鍵已經存在具有此名稱的值欄位，會將它加入。

*regtype*<br/>
要加入的登錄機碼的類型。 可以是下列其中之一： `text`， `dword`， `binary`，或`CString`。

## <a name="remarks"></a>備註

**Rdx** c + + 屬性建立或修改現有的登錄機碼的 COM 元件。 屬性會將 BEGIN_RDX_MAP 巨集將實作的目標成員的物件。 `RegistryDataExchange`插入 BEGIN_RDX_MAP 巨集，因為函式可以用來登錄和資料成員之間傳輸資料

這個屬性可以用於搭配[coclass](coclass.md)， [progid](progid.md)，或[vi_progid](vi-progid.md)屬性或其他屬性，表示其中一種。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**或是**struct**成員|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="example"></a>範例

下列程式碼會加入稱為 MyValue 系統描述 CMyClass COM 元件的登錄機碼。

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[registration_script](registration-script.md)  