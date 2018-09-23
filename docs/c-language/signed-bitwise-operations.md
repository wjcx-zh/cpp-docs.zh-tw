---
title: 帶正負號的位元運算 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184fd5a0e6c12cb58e9fed759459e7b8172896f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038291"
---
# <a name="signed-bitwise-operations"></a>帶正負號的位元運算

**ANSI 3.3**：帶正負號整數位元運算的結果

帶正負號整數的位元運算運作方式，與不帶正負號整數的位元運算相同。 例如，`-16 & 99` 可以用二進位運算式表示為

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

位元 AND 的結果為 96。

## <a name="see-also"></a>請參閱

[整數](../c-language/integers.md)