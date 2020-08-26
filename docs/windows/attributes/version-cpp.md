---
title: 'c + + COM 屬性 (版本) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: 7d21761a556455cec27087896984bdc721841d9d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832941"
---
# <a name="version-c"></a>version (C++)

識別類別之多個版本之間的特定版本。

## <a name="syntax"></a>語法

```cpp
[ version("version") ]
```

### <a name="parameters"></a>參數

*version*<br/>
`coclass` 的版本號碼。 如果未指定，則會將1.0 放在 .idl 檔案中。

## <a name="remarks"></a>備註

**Version** c + + 屬性的功能與[版本](/windows/win32/Midl/version)MIDL 屬性相同，而且會傳遞至產生的 .idl 檔案。

## <a name="example"></a>範例

如需**版本**的範例用法，請參閱可系[結範例。](bindable.md)

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|**coclass**|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[類別屬性](class-attributes.md)
