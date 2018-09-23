---
title: 字元順序 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cf3b52b8a4e76062d06b0b9ca3d4535b79595c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061509"
---
# <a name="character-sequences"></a>字元順序

**ANSI 3.8.2**：原始程式檔字元序列的對應

除了不支援逸出序列以外，前置處理器陳述式使用的字元集與原始程式檔陳述式使用的相同。

因此，若要指定 Include 檔案的路徑，則只需要使用一個反斜線：

```
#include "path1\path2\myfile"
```

在原始程式碼內必須使用兩個反斜線：

```
fil = fopen( "path1\\path2\\myfile", "rt" );
```

## <a name="see-also"></a>請參閱

[前置處理指示詞](../c-language/preprocessing-directives.md)