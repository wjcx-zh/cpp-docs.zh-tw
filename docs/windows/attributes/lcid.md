---
title: 'lcid (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: 7533cd9b269a879c5c2f061dcdfc632b1b27c871
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834176"
---
# <a name="lcid"></a>lcid

可讓您將地區設定識別碼傳遞至函式。

## <a name="syntax"></a>語法

```cpp
[lcid]
```

## <a name="remarks"></a>備註

**Lcid** c + + 屬性會實作為[lcid](/windows/win32/Midl/lcid) MIDL 屬性的功能。 如果您想要執行程式庫區塊的地區設定，請對 module 屬性使用**lcid =** `lcid` 參數。 [module](module-cpp.md)

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_lcid.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];
typedef long HRESULT;

[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]
__interface IStatic {
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面參數|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)
