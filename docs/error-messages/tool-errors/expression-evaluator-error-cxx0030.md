---
title: 運算式評估工具錯誤 CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 1e52b238905fba5c310a89377b81548a1c6b5784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500343"
---
# <a name="expression-evaluator-error-cxx0030"></a>運算式評估工具錯誤 CXX0030

無法評估運算式

寫入偵錯工具的運算式評估工具無法取得運算式的值。 一個可能的原因是此運算式會參考外部程式的位址空間的記憶體 （正在取值 null 指標是一個例子）。 Windows 不允許存取程式的位址空間之外的記憶體。

若要重新撰寫運算式，利用括號控制評估的順序。

此錯誤是與 can0030 相同。