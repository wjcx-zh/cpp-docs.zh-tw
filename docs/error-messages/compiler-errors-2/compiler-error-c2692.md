---
title: 編譯器錯誤 C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: c469f4944417c9116c7316b01642dd4b370b8c4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611155"
---
# <a name="compiler-error-c2692"></a>編譯器錯誤 C2692

'function_name': 完整函式原型中使用的 C 編譯器需要 '/ /clr' 選項

當編譯.net managed 程式碼時，C 編譯器會需要 ANSI 函式宣告。 此外，如果函式會不接受任何參數，它必須明確宣告`void`做為參數類型。