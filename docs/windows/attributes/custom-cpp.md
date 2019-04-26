---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 227e67696e679452a9c6c0e18c04e3d918f7a93f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148170"
---
# <a name="custom-c"></a>custom (C++)

類型程式庫中定義物件之中繼資料。

## <a name="syntax"></a>語法

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>參數

*uuid*<br/>
唯一 ID。

*value*<br/>
值，這個值可以放入變數。

## <a name="remarks"></a>備註

**自訂**C++屬性會放入類型程式庫的資訊。 您必須讀取類型程式庫中的自訂值的工具。

**自訂**屬性有相同的功能[自訂](/windows/desktop/Midl/custom)MIDL 屬性。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|非 COM**介面**，**類別**， **enum**s`idl_module`方法、 介面成員、 介面參數**typedef**s，**union**s**結構**s|
|**可重複**|是|
|**必要屬性**|**coclass** （當使用類別上）|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[介面屬性](interface-attributes.md)