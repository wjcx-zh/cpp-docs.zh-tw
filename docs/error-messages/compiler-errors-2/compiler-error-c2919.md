---
title: 編譯器錯誤 C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: ab11226c8cc4629a265dd182d5f882f6b3be7e5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160846"
---
# <a name="compiler-error-c2919"></a>編譯器錯誤 C2919

' type':運算子不能用在 WinRT 類型的已發行介面上

Windows 執行階段類型系統不支援已發行類型介面中的運算子成員函式。 這是因為並非所有語言都可以使用運算子成員函式。 您可以建立私用或內部運算子成員函式，可從相同類別或編譯單位中的 C++ 程式碼中呼叫。

若要修正此問題，請從公用介面移除運算子成員函式，或將它變更為已命名的成員函式。 例如，現在您必須將成員函式命名 `Equals`，而不是 `operator==`。