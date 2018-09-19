---
title: 運算式評估工具錯誤 CXX0030 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2921013d116b7d8f02e1e29380ca3cd14086b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102804"
---
# <a name="expression-evaluator-error-cxx0030"></a>運算式評估工具錯誤 CXX0030

無法評估運算式

寫入偵錯工具的運算式評估工具無法取得運算式的值。 一個可能的原因是此運算式會參考外部程式的位址空間的記憶體 （正在取值 null 指標是一個例子）。 Windows 不允許存取程式的位址空間之外的記憶體。

若要重新撰寫運算式，利用括號控制評估的順序。

此錯誤是與 can0030 相同。