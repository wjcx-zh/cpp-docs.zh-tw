---
title: 'no_injected_text (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: ab718376d5da7214813d5ab2e0caaa7bbccd077b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844076"
---
# <a name="no_injected_text"></a>no_injected_text

防止編譯器將程式碼插入為屬性使用的結果。

## <a name="syntax"></a>語法

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>參數

*boolean*<br/>
**`true`** 如果您不想要插入程式碼， (選擇性的) ， **`false`** 允許插入程式碼。 **`true`** 是預設值。

## <a name="remarks"></a>備註

**No_injected_text** c + + 屬性最常見的用法是使用[/fx](../../build/reference/fx-merge-injected-code.md)編譯器選項，它會將**no_injected_text**屬性插入 .mrg 檔案中。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|任何位置|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)
