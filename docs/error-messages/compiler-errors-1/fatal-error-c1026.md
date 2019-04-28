---
title: 嚴重錯誤 C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: b1a659967a9a62cb79e1084f7d1fa1729bae14da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347125"
---
# <a name="fatal-error-c1026"></a>嚴重錯誤 C1026

剖析器堆疊溢位，程式太複雜

剖析程式所需的空間會造成編譯器堆疊溢位。

減少複雜度的運算式：

- 減少在巢狀`for`和`switch`陳述式。 將更深的巢狀陳述式放在個別的函式。

- 拆解長涉及逗號運算子或函式呼叫的運算式。