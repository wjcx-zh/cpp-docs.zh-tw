---
title: "編譯器錯誤 C2919 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a70b679d4add5fa4ad2904e3c0d103e1c8881280
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2919"></a>編譯器錯誤 C2919
type'：運算子不能用在 WinRT 類型的已發行介面上  
  
 Windows 執行階段類型系統不支援已發行類型介面中的運算子成員函式。 這是因為並非所有語言都可以使用運算子成員函式。 您可以建立私用或內部運算子成員函式，可從相同類別或編譯單位中的 C++ 程式碼中呼叫。  
  
 若要修正此問題，請從公用介面移除運算子成員函式，或將它變更為已命名的成員函式。 例如，現在您必須將成員函式命名 `Equals`，而不是 `operator==`。
