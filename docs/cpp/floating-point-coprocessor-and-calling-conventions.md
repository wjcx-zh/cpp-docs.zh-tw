---
title: 浮點常數副處理器和呼叫慣例
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 09358ee36da7e5a86c214789fa7fd0687e9b8825
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231191"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮點常數副處理器和呼叫慣例

如果您要撰寫浮點副處理器的元件常式，必須保留浮點控制字組並清除副處理器堆疊，除非您要傳回 **`float`** 或 **`double`** 值（您的函式應該會在 ST （0）中傳回）。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)
