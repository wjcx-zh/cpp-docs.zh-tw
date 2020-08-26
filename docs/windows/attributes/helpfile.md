---
title: " (c + + COM 屬性) 的説明"
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 385c6da6a432f0954e62c9f16a22f0b70b73b317
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845233"
---
# <a name="helpfile"></a>helpfile

設定類型程式庫的說明檔名稱。

## <a name="syntax"></a>語法

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>參數

*filename*<br/>
包含說明主題的檔案名。

## <a name="remarks"></a>備註

[功能 **説明** + +] 屬性與 [功能 [説明](/windows/win32/Midl/helpfile) ] MIDL 屬性具有相同的功能。

## <a name="example"></a>範例

如需**如何使用 [** 提供] 的範例，請參閱[模組](module-cpp.md)的範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**interface**、 **`typedef`** 、 **`class`** 、方法、 **`property`**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
