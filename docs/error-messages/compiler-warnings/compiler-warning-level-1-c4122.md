---
title: 編譯器警告 (層級 1) C4122
ms.date: 11/04/2016
f1_keywords:
- C4122
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
ms.openlocfilehash: bb5016bbf323057822c89a74001c75ab1855542c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490333"
---
# <a name="compiler-warning-level-1-c4122"></a>編譯器警告 (層級 1) C4122

'function': alloc_text 僅適用使用 C 連結的函式

**alloc_text** pragma 只適用於以 **extern c**宣告的函式。 它不能搭配外部 C++ 函式使用。

忽略 pragma。