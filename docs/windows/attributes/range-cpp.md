---
title: range (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: d1221192eb1813d759f293fe5555d7aaa5b367ab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514149"
---
# <a name="range-c"></a>range (C++)

針對在執行時間設定其值的引數或欄位, 指定允許的值範圍。

## <a name="syntax"></a>語法

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>參數

*low*<br/>
低範圍的值。

*high*<br/>
最大範圍值。

## <a name="remarks"></a>備註

**Range** C++屬性的功能與[範圍](/windows/win32/Midl/range)MIDL 屬性相同。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_range.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面方法, 介面參數|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[資料成員屬性](data-member-attributes.md)