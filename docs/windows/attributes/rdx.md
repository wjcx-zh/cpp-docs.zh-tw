---
title: rdx （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: f0140b759b1d78eb1284213a0dc47d9600b2a83b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214626"
---
# <a name="rdx"></a>rdx

建立登錄機碼或修改現有的登錄機碼。

## <a name="syntax"></a>語法

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>參數

*key*<br/>
要建立或開啟之金鑰的名稱。

*valuename*<br/>
選擇性指定要設定的值欄位。 如果具有此名稱的值欄位尚未存在於索引鍵中，則會加入。

*regtype*<br/>
要新增之登錄機碼的類型。 可以是下列其中一項： `text`、`dword`、`binary`或 `CString`。

## <a name="remarks"></a>備註

**Rdx** C++屬性會建立或修改 COM 元件現有的登錄機碼。 屬性會將 BEGIN_RDX_MAP 宏加入至執行目標成員的物件。 `RegistryDataExchange`，插入做為 BEGIN_RDX_MAP 宏結果的函式，可用來在登錄和資料成員之間傳輸資料。

這個屬性可以與[coclass](coclass.md)、 [progid](progid.md)或[vi_progid](vi-progid.md)屬性或其他隱含其中一項的屬性搭配使用。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**或**結構**成員|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="example"></a>範例

下列程式碼會將名為 MyValue 的登錄機碼新增至描述 CMyClass COM 元件的系統。

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
