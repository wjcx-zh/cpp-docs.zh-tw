---
title: 嚴重錯誤 C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: 9ea97bef16bebb8fc0e765ed708e54baee9a64de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220336"
---
# <a name="fatal-error-c1026"></a>嚴重錯誤 C1026

剖析器堆疊溢位，程式太複雜

剖析程式所需的空間導致編譯器堆疊溢位。

藉由下列方式減少運算式的複雜度：

- 減少和語句中的嵌套 **`for`** **`switch`** 。 將更深入的嵌套語句放在不同的函式中。

- 中斷牽涉到逗號運算子或函式呼叫的長運算式。
