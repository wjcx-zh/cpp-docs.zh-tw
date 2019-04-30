---
title: no_injected_text (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 354643020e704a87daa2e56e923b6a0a704bf0b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409287"
---
# <a name="noinjectedtext"></a>no_injected_text

防止編譯器將程式碼，因為屬性使用。

## <a name="syntax"></a>語法

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>參數

*boolean*<br/>
（選擇性）**真**如果您想不要插入此項目，任何程式碼**false**讓插入的程式碼。 **true**是預設值。

## <a name="remarks"></a>備註

最常見的用法**no_injected_text** C++屬性是由[/Fx](../../build/reference/fx-merge-injected-code.md)編譯器選項，插入**no_injected_text**到.mrg 檔的屬性。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)