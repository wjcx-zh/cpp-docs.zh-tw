---
title: no_injected_text （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9289c1b8f28b90dd5a3a4a437d3e2a5870e8468
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790930"
---
# <a name="noinjectedtext"></a>no_injected_text

防止編譯器將程式碼，因為屬性使用。

## <a name="syntax"></a>語法

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>參數

*布林值*<br/>
（選擇性）**真**如果您想不要插入此項目，任何程式碼**false**讓插入的程式碼。 **true**是預設值。

## <a name="remarks"></a>備註

最常見的用法**no_injected_text** c + + 屬性是由[/Fx](../../build/reference/fx-merge-injected-code.md)編譯器選項，插入**no_injected_text**到.mrg 檔的屬性。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)  