---
title: 編譯器警告 （層級 1） C4838 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C4838
dev_langs:
- C++
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1327ed8869c17701c6aa0a6ce2e3479b6109b8cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283841"
---
# <a name="compiler-warning-level-1-c4838"></a>編譯器警告 （層級 1） C4838
從 'type_1' 轉換為 'type_2' 必須是縮小轉換  
  
 使用彙總或清單初始設定時，找不到隱含的縮小轉換。  
  
 C 語言允許在指派和初始化時，隱含的縮小轉換和 c + + 坐，即使未預期的縮小是許多程式碼錯誤的原因。 若要讓程式碼更安全，c + + 標準初始設定清單中的縮小轉換發生時需要診斷訊息。 在 Visual c + + 中，是診斷[編譯器錯誤 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md)使用統一初始化語法支援從 Visual Studio 2015 開始時。 編譯器會產生警告 C4838 時使用的清單或 Visual Studio 2013 所支援的彙總初始化語法。  
  
 當您知道目標所能容納轉換值的可能範圍時，可以是可以縮小轉換。 在此情況下，您知道編譯器會以上。 如果您刻意進行縮小轉換，您要的情況明確使用進行靜態轉型。 否則，這則警告訊息幾乎都表示程式碼中有錯誤。 您可以藉由確定您初始化的物件具有值大到足以處理輸入的類型來修正此問題。  
  
 下列範例會產生 C4838，並示範修正此問題的一種方法：  
  
```  
// C4838.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C4838.cpp  
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C4838(double d1) {  
    double ad[] = { 1, d1 }; // OK  
    int ai[] = { 1, d1 };    // warning C4838  
    S1 s11 = { 1, 2, d1 };   // OK  
    S1 s12 { d1, 2, 3 };     // warning C4838  
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838  
}  
```