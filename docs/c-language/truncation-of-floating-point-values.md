---
title: 浮點值截斷 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, truncation
ms.assetid: 051a6e22-c636-4af8-9ac4-40160f4affca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b30700b52e7cbbbc295d6050b03283b4b45a0b08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103811"
---
# <a name="truncation-of-floating-point-values"></a>浮點值截斷

**ANSI 3.2.1.4** 將浮點數轉換為較小的浮點數時，截斷或進位的方向

發生反向溢位時，會將浮點變數的值向下捨入為零。 溢位可能會造成執行階段錯誤，或可能會因為所指定的最佳化而產生無法預期的值。

## <a name="see-also"></a>請參閱

[浮點數學](../c-language/floating-point-math.md)