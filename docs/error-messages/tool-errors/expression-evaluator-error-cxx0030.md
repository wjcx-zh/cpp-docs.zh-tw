---
title: 運算式評估工具錯誤 CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 477ec31d18924e91baf2d8b7b732bc7a50eee53b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195613"
---
# <a name="expression-evaluator-error-cxx0030"></a>運算式評估工具錯誤 CXX0030

運算式未 evaluatable

偵錯工具的運算式評估工具無法以寫入的方式取得運算式的值。 其中一個可能的原因是運算式參考到程式的位址空間以外的記憶體（例如，將 null 指標取值為一個範例）。 Windows 不允許存取位於程式位址空間以外的記憶體。

您可能想要使用括弧來重寫運算式，以控制評估的順序。

此錯誤與 CAN0030 相同。
