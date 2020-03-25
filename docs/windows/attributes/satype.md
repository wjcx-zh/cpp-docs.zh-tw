---
title: satype （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 4619deec6d5e4e9083fbc7bcab53caee0101285c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166272"
---
# <a name="satype"></a>satype

指定 `SAFEARRAY` 結構的資料類型。

## <a name="syntax"></a>語法

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>參數

*data_type*<br/>
當做參數傳遞至介面方法之 `SAFEARRAY` 資料結構的資料類型。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數，介面方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

## <a name="remarks"></a>備註

**Satype** C++屬性會指定 `SAFEARRAY`的資料類型。

> [!NOTE]
> 從產生的 .idl 檔案中的 `SAFEARRAY` 指標卸載一層間接取值，從該檔案在 .cpp 檔案中的宣告方式。

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
