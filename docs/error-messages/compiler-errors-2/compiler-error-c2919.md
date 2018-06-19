---
title: 編譯器錯誤 C2919 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5e2eb2a32f1a906814f5b347ba1ebf13eba71ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245798"
---
# <a name="compiler-error-c2919"></a>編譯器錯誤 C2919
type'：運算子不能用在 WinRT 類型的已發行介面上  
  
 Windows 執行階段類型系統不支援已發行類型介面中的運算子成員函式。 這是因為並非所有語言都可以使用運算子成員函式。 您可以建立私用或內部運算子成員函式，可從相同類別或編譯單位中的 C++ 程式碼中呼叫。  
  
 若要修正此問題，請從公用介面移除運算子成員函式，或將它變更為已命名的成員函式。 例如，現在您必須將成員函式命名 `Equals`，而不是 `operator==`。