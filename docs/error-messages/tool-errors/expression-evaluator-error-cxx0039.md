---
title: 運算式評估工具錯誤 CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 5706d002eb3d566d05b059cb04b6b1626fdb3d33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185122"
---
# <a name="expression-evaluator-error-cxx0039"></a>運算式評估工具錯誤 CXX0039

符號不明確

C 運算式評估工具無法判斷要在運算式中使用的符號實例。 符號在繼承樹狀結構中出現一次以上。

您必須使用範圍解析運算子（`::`）明確地指定要在運算式中使用的實例。

此錯誤與 CAN0039 相同。
