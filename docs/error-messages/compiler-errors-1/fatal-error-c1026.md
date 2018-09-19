---
title: 嚴重錯誤 C1026 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db9167383df48dad274ef8941defaa53f51d3bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068984"
---
# <a name="fatal-error-c1026"></a>嚴重錯誤 C1026

剖析器堆疊溢位，程式太複雜

剖析程式所需的空間會造成編譯器堆疊溢位。

減少複雜度的運算式：

- 減少在巢狀`for`和`switch`陳述式。 將更深的巢狀陳述式放在個別的函式。

- 拆解長涉及逗號運算子或函式呼叫的運算式。