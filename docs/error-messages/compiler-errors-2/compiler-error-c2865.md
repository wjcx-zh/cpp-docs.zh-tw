---
title: 編譯器錯誤 C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: 38b7dd86a57c3cd89811c6489e51fb4271fd7b79
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769611"
---
# <a name="compiler-error-c2865"></a>編譯器錯誤 C2865

'function': handle_or_pointer 的非法比較

您可以比較參考[類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md)管理只會針對相等的參考類型，以查看它們是否參考相同的物件 （= =） 或不同的物件或 (！ =)。

您無法比較它們的順序，因為.NET 執行階段可能會移動受管理的物件，也可以隨時變更測試的結果。