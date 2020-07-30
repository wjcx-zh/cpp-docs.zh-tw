---
title: 將整數轉型為浮點值
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: b3c65beee0cef4eb74d1bad3c03e5a9c11efae27
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227916"
---
# <a name="casting-integers-to-floating-point-values"></a>將整數轉型為浮點值

**ANSI 3.2.1.3**：當整數轉換成無法正確地表示原始值的浮點數時，其截斷的方向

當整數轉型成無法正確地表示其值的浮點值時，會將其值捨入 (向上或向下捨入) 為最接近的適當值。

例如，將 **`unsigned long`** （具有32位有效位數）轉換為 **`float`** （其尾數具有23位精確度），會將數位四捨五入至最接近的256倍數。 **`long`** 值4294966913到4294967167會全部四捨五入到 **`float`** 值4294967040。

## <a name="see-also"></a>另請參閱

[浮點數學](../c-language/floating-point-math.md)
