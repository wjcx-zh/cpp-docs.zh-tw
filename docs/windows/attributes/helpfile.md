---
title: 説明 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 538cdbb38ac525cfee03a641f3e62e22a69f8e2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501544"
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

[ C++提供人員] 屬性的功能與 [[説明](/windows/win32/Midl/helpfile)] MIDL 屬性相同。

## <a name="example"></a>範例

如需如何使用「**説明**」的範例, 請參閱[module](module-cpp.md)的範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**、 **typedef**、**類別**、方法、**屬性**|
|**可重複**|否|
|**必要屬性**|無|
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