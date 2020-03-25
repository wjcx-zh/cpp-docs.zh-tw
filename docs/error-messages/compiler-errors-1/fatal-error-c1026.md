---
title: 嚴重錯誤 C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: a7c7a5da01c8b4a44c307a00f53530acb12a8009
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204649"
---
# <a name="fatal-error-c1026"></a>嚴重錯誤 C1026

剖析器堆疊溢位，程式太複雜

剖析程式所需的空間導致編譯器堆疊溢位。

藉由下列方式減少運算式的複雜度：

- 減少 `for` 和 `switch` 語句中的嵌套。 將更深入的嵌套語句放在不同的函式中。

- 中斷牽涉到逗號運算子或函式呼叫的長運算式。
