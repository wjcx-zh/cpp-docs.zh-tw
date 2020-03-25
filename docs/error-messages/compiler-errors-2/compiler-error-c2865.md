---
title: 編譯器錯誤 C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: dd4374c1a577c4c39c5dec107ed5025d7cdc79c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201692"
---
# <a name="compiler-error-c2865"></a>編譯器錯誤 C2865

' function '： handle_or_pointer 的不合法比較

您可以比較[類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md)或受管理的參考型別的參考，只是為了相等，以查看它們是否參考相同的物件（= =）或不同的物件（！ =）。

您無法比較它們以進行排序，因為 .NET 執行時間可能會隨時移動受管理的物件，並變更測試的結果。
