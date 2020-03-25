---
title: 編譯器警告 (層級 1 和 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 7e39e8c837d94776a804da2bf38643b453edb949
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198038"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>編譯器警告 (層級 1 和 4) C4115

'type': 括弧中未命名類型的定義

這個指定的符號可用來定義括弧運算式內的結構、等位或列舉類型。 定義的範圍可能不如預期。

在 C 函式呼叫中，此定義具有全域範圍。 在 C++ 呼叫中，此定義與正在呼叫之函式的範圍相同。

這個警告也可能是由括弧內不是括號運算式的宣告子 (例如原型) 所造成。

在 ANSI 相容性 (/Za) 下所編譯的 C++ 和 C 程式中，這是層級 1 警告。 其他情況下則為層級 3。
