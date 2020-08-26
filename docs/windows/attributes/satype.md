---
title: 'satype (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 16da256f491dbb0002d92cadaceda14a49eb2192
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842776"
---
# <a name="satype"></a>satype

指定結構的資料類型 `SAFEARRAY` 。

## <a name="syntax"></a>語法

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>參數

*data_type*<br/>
以 `SAFEARRAY` 參數形式傳遞至介面方法之資料結構的資料類型。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面參數，介面方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|None|

## <a name="remarks"></a>備註

**Satype** c + + 屬性會指定的資料類型 `SAFEARRAY` 。

> [!NOTE]
> 從產生的 .idl 檔案中的指標卸載的間接取值層級，是 `SAFEARRAY` 在 .cpp 檔案中宣告的方式。

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

[編譯器屬性](compiler-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[id](id.md)
