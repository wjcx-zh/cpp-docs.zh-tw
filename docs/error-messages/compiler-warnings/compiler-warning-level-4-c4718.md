---
title: 編譯器警告 （層級 4） C4718 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4718
dev_langs:
- C++
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8736902f4c3a1cfac7313806fde65d1b253716b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054229"
---
# <a name="compiler-warning-level-4-c4718"></a>編譯器警告 (層級 4) C4718

'function call': 遞迴呼叫沒有副作用，正在刪除

函式包含遞迴呼叫，但沒有副作用。 正在刪除對此函式的呼叫。 程式的正確性不受影響，但行為受影響。 因為保留呼叫可能會導致執行階段堆疊溢位的例外狀況，所以刪除該呼叫以排除這個可能性。