---
title: 運算式評估工具錯誤 CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 053e57a21f0cb75cbd96732edb6812b3557bcd50
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396973"
---
# <a name="expression-evaluator-error-cxx0039"></a>運算式評估工具錯誤 CXX0039

符號是模稜兩可

C 運算式評估工具無法判斷哪一個執行個體，在運算式中使用的符號。 符號，就會發生在繼承樹狀結構中的一次以上。

您必須使用範圍解析運算子 (`::`) 來明確指定要在運算式中使用的執行個體。

此錯誤是與 can0039 相同。