---
title: 讀取範圍 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76530dfdac917dfbde50bc3fb1b17a3c31178729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030234"
---
# <a name="reading-ranges"></a>讀取範圍

**ANSI 4.9.6.2**：解譯虛線 (-) 字元，該字元不是 `fscanf` 函式中 % [ 轉換之 scanlist 中的第一個字元，也不是最後一個字元

下面這行

```
fscanf( fileptr, "%[A-Z]", strptr);
```

會將範圍 A-Z 中任何數目的字元讀取到 `strptr` 所指向的字串中。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)