---
title: 'nonbrowsable (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonbrowsable
helpviewer_keywords:
- nonbrowsable attribute
ms.assetid: e71a98e7-4b65-454a-9829-342b9f2a84be
ms.openlocfilehash: 561622cc30573ace606eccb6aa7b5f2dfd188dfe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836100"
---
# <a name="nonbrowsable"></a>nonbrowsable

表示介面成員不應顯示在屬性瀏覽器中。

## <a name="syntax"></a>語法

```cpp
[nonbrowsable]
```

## <a name="remarks"></a>備註

**Nonbrowsable** c + + 屬性具有與[nonbrowsable](/windows/win32/Midl/nonbrowsable) MIDL 屬性相同的功能。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_nonbrowsable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, helpstring("help string"), helpstringcontext(1),
uuid="11111111-1111-1111-1111-111111111111"]
__interface IMyI
{
   [nonbrowsable] HRESULT xx();
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)
