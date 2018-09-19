---
title: 編譯器錯誤 C2097 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2da955f5382a1ebacdb507a69ed02627b11462e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021859"
---
# <a name="compiler-error-c2097"></a>編譯器錯誤 C2097

不合法的初始化

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 初始化變數，使用非常數的值。

1. 簡短的位址與一長串位址來初始化。

1. 初始化本機結構、 等位或陣列進行編譯時是非常數運算式 **/Za**。

1. 包含逗號運算子的運算式進行初始化。

1. 不是常數或符號的運算式進行初始化。