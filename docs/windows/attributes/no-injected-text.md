---
title: no_injected_text （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 7e5c822c45888f41e8dd849f25658d0139e6fda0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201241"
---
# <a name="no_injected_text"></a>no_injected_text

防止編譯器插入程式碼做為屬性使用的結果。

## <a name="syntax"></a>語法

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>參數

*boolean*<br/>
（選擇性） **`true`** 如果您不想插入程式碼，則 **`false`** 允許插入程式碼。 **`true`** 是預設值。

## <a name="remarks"></a>備註

**No_injected_text** c + + 屬性最常見的用法是[/fx](../../build/reference/fx-merge-injected-code.md)編譯器選項，它會將**no_injected_text**屬性插入 .mrg 檔案中。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)
