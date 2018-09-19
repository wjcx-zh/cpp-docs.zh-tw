---
title: 內嵌函式 | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 127438da4929e58e07e10701dd64869b084fe4c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078578"
---
# <a name="inline-functions"></a>內嵌函式

**Microsoft 專屬**

`__inline` 關鍵字會指示編譯器針對函式呼叫的每個執行個體，取代函式定義內的程式碼。 不過，編譯器會判斷是否進行替代。 例如，如果函式的位址已被佔用，或函式太大無法內嵌，則編譯器不會內嵌函式。

對於被視為內嵌候選項目的函式，它必須使用新樣式的函式定義。

請使用以下格式指定內嵌函式：

> **__inline** *type*<sub>opt</sub> *function-definition*

使用內嵌函式可產生較快速的程式碼，有時則會產生比下列對等函式呼叫所產生更小的程式碼，原因如下：

- 它可以節省執行函式呼叫所需的時間。

- 小型內嵌函式 (可能為三行或更少) 會建立比同等函式呼叫更少的程式碼，因為編譯器無法產生程式碼來處理引數和傳回值。

- 由於編譯器無法執行跨程序最佳化，所以函式產生的內嵌會受限於無法提供給一般函式使用的程式碼最佳化。

使用 `__inline` 的函式不應與內嵌組合語言程式碼混淆。 如需詳細資訊，請參閱[內嵌組合語言](../c-language/inline-assembler-c.md)。

**END Microsoft 特定的**

## <a name="see-also"></a>請參閱

[inline、__inline、\__forceinline](../cpp/inline-functions-cpp.md)

