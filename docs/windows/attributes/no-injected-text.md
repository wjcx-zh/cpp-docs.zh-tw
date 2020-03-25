---
title: no_injected_text （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 5f98be3478b2e1eeb4b464f1784f3f4ece22d8a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166610"
---
# <a name="no_injected_text"></a>no_injected_text

防止編譯器插入程式碼做為屬性使用的結果。

## <a name="syntax"></a>語法

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>參數

*boolean*<br/>
選擇性如果您不想插入程式碼，則為**true** ，否則為**false** ，表示允許插入程式碼。 預設值為**true** 。

## <a name="remarks"></a>備註

**No_injected_text** C++屬性最常見的用法是[/fx](../../build/reference/fx-merge-injected-code.md)編譯器選項，它會將**no_injected_text**屬性插入 .mrg 檔案中。

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
