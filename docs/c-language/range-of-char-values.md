---
title: char 值的範圍 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b45d828cecb5908742a193c8836bc4b565a6498
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110688"
---
# <a name="range-of-char-values"></a>char 值的範圍

**ANSI 3.2.1.1**："plain" **char** 的值範圍是否與 **signed char** 或 `unsigned char` 相同

從 -128 到 127 的範圍中所有帶正負號的字元值。 從 0 到 255 的範圍中所有不帶正負號的字元值。

/J 編譯器選項將預設值從 **signed** 變更為 `unsigned`。

## <a name="see-also"></a>請參閱

[字元](../c-language/characters.md)