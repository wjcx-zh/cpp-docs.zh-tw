---
title: 浮點常數副處理器和呼叫慣例
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: c70dd3b049ca353acc8a504df52b2c61feaf1974
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188610"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮點常數副處理器和呼叫慣例

如果您要撰寫浮點副處理器的元件常式，必須保留浮點控制字組並清除副處理器堆疊，除非您要傳回**float**或**double**值（您的函式應該會在 ST （0）中傳回）。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)
