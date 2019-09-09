---
title: 版本（C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: 9a432267632b1f2a716a833a485b182cd93a27e2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514884"
---
# <a name="version-c"></a>version (C++)

識別類別的多個版本之間的特定版本。

## <a name="syntax"></a>語法

```cpp
[ version("version") ]
```

### <a name="parameters"></a>參數

*version*<br/>
的版本號碼`coclass`。 如果未指定，1.0 將會放在 .idl 檔案中。

## <a name="remarks"></a>備註

**Version** C++屬性與[版本](/windows/win32/Midl/version)MIDL 屬性具有相同的功能，而且會傳遞至產生的 .idl 檔案。

## <a name="example"></a>範例

如需**版本**的範例用法，請參閱可系結[的範例。](bindable.md)

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|**coclass**|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[類別屬性](class-attributes.md)