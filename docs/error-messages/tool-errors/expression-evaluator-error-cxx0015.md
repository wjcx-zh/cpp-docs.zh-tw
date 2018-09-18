---
title: 運算式評估工具錯誤 CXX0015 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa37a2cc7208063ce4cfa786de196842ab42b45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050812"
---
# <a name="expression-evaluator-error-cxx0015"></a>運算式評估工具錯誤 CXX0015

運算式太複雜 （堆疊溢位）

輸入的運算式是太複雜或巢狀層數太多量 C 運算式評估工具的可用儲存空間。

溢位，通常會發生因為太多暫止的計算。

重新排列的運算式，以便可以評估運算式的每個元件，會發現，而無需等待計算運算式的其他部分。

將運算式分割為多個命令。

此錯誤是與 can0015 相同。