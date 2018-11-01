---
title: helpstring （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 12707dde61013caa1ed9feb1d0daa74cbb7b9d9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591369"
---
# <a name="helpstring"></a>helpstring

指定用來描述所套用之項目的字元字串。

## <a name="syntax"></a>語法

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>參數

*string*<br/>
[說明] 字串文字。

## <a name="remarks"></a>備註

**Helpstring** c + + 屬性具有相同的功能[helpstring](/windows/desktop/Midl/helpstring) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[defaultvalue](defaultvalue.md)如需如何使用的範例**helpstring**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**， **typedef**，**類別**、 方法、 屬性|
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
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)