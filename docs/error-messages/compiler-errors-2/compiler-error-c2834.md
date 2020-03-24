---
title: 編譯器錯誤 C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: a6a7bc0591fd51c808c303e94eeaaffd6111ffcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201895"
---
# <a name="compiler-error-c2834"></a>編譯器錯誤 C2834

' operator operator ' 必須是全域限定的

`new` 和 `delete` 運算子會系結至其所在的類別。 範圍解析不能用來從不同的類別中選取 `new` 或 `delete` 的版本。 若要執行多個形式的 `new` 或 `delete` 運算子，請使用額外的型式參數建立運算子的版本。
