---
title: 浮點常數副處理器和呼叫慣例
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 7e9184d66bde26ab0e2b345f8f10c2e28619fd2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625104"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮點常數副處理器和呼叫慣例

如果您要為浮點常式點副處理器撰寫組件，您必須保留浮點控制字詞並清除副處理器堆疊，除非您要傳回**浮點數**或是**double**值 （也就您的函式應在 ST(0 中傳回。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)