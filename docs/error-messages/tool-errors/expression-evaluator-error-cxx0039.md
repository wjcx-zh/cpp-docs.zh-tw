---
title: 運算式評估工具錯誤 CXX0039 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5397426618c5dfcbaa6307105781ff2e6f2eb97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048327"
---
# <a name="expression-evaluator-error-cxx0039"></a>運算式評估工具錯誤 CXX0039

符號是模稜兩可

C 運算式評估工具無法判斷哪一個執行個體，在運算式中使用的符號。 符號，就會發生在繼承樹狀結構中的一次以上。

您必須使用範圍解析運算子 (`::`) 來明確指定要在運算式中使用的執行個體。

此錯誤是與 can0039 相同。