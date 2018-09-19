---
title: 編譯器錯誤 C2692 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03a9006889c5853e77b5603484ea9d18f2474241
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088367"
---
# <a name="compiler-error-c2692"></a>編譯器錯誤 C2692

'function_name': 完整函式原型中使用的 C 編譯器需要 '/ /clr' 選項

當編譯.net managed 程式碼時，C 編譯器會需要 ANSI 函式宣告。 此外，如果函式會不接受任何參數，它必須明確宣告`void`做為參數類型。