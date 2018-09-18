---
title: 嚴重錯誤 C1013 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1013
dev_langs:
- C++
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33c10062cac83984fb1c68835780497b89c4cbc1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050505"
---
# <a name="fatal-error-c1013"></a>嚴重錯誤 C1013

編譯器限制 : 左括號太多，請簡化運算式或分為數個陳述式

運算式中包含對單一運算式而言太多的括弧層級。 請簡化運算式，或將它切為多個陳述式。

在 Visual C++ 6.0 Service Pack 3 之前，對於單一運算式中的巢狀括弧限制是 59。 目前巢狀括弧的限制為 256。