---
title: 'rdx (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: f61eaf535102c8885e828176434acf221dfe2457
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836877"
---
# <a name="rdx"></a>rdx

建立登錄機碼或修改現有的登錄機碼。

## <a name="syntax"></a>語法

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>參數

*key*<br/>
要建立或開啟之索引鍵的名稱。

*valuename*<br/>
 (選擇性) 指定要設定的值欄位。 如果索引鍵中沒有這個名稱的值欄位，就會加入該欄位。

*regtype*<br/>
要加入的登錄機碼型別。 可以是下列其中一項： `text` 、 `dword` 、 `binary` 或 `CString` 。

## <a name="remarks"></a>備註

**Rdx** c + + 屬性會針對 COM 元件建立或修改現有的登錄機碼。 屬性會將 BEGIN_RDX_MAP 宏加入至實目標成員的物件。 `RegistryDataExchange`，當做 BEGIN_RDX_MAP 宏的結果插入的函式，可用來在登錄和資料成員之間傳輸資料。

這個屬性可以搭配 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性，或其他表示其中一項的屬性使用。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`** 或 **`struct`** 成員|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="example"></a>範例

下列程式碼會將名為 MyValue 的登錄機碼新增至描述 CMyClass COM 元件的系統中。

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
