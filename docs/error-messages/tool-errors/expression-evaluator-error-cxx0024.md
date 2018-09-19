---
title: 運算式評估工具錯誤 CXX0024 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2816be7bb1d33757d9722d605d461ac6fb34fadd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118189"
---
# <a name="expression-evaluator-error-cxx0024"></a>運算式評估工具錯誤 CXX0024

需要值 （l-value） 的作業

運算式未評估為左值，指定作業需要左值。

左值 （因此稱為 「 因為它出現在指派陳述式左邊 」） 是指記憶體位置的運算式。

比方說，`buffer[count]`是有效的左值，因為它會指向特定記憶體位置。 邏輯比較`zed != 0`不是有效的左值，因為其評估結果為 TRUE 或 FALSE，未為記憶體位址。

此錯誤是與 can0024 相同。