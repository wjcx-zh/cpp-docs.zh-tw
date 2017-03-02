---
title: "編譯器警告 （層級 1） C4838 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4838
dev_langs:
- C++
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 227af1840fe5aee63545e35456fe09749f00de1d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4838"></a>編譯器警告 （層級 1） C4838
從 'type_1' 轉換為 'type_2' 需要縮小轉換  
  
 使用彙總或清單初始化時，找不到隱含的縮小轉換。  
  
 C 語言允許在指派和初始化時，隱含的縮小轉換和 c + + 坐，即使意外縮小是造成許多程式碼錯誤的原因。 若要讓程式碼更安全，c + + 標準初始設定清單中的縮小轉換發生時需要診斷訊息。 在 Visual c + + 中，是診斷[編譯器錯誤 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md)時使用支援從 Visual Studio 2015 中的一致的初始化語法。 編譯器會產生警告 C4838 時使用的清單或 Visual Studio 2013 所支援的彙總初始化語法。  
  
 當您知道目標所能容納的轉換值的可能範圍縮小轉換可以是沒問題。 在此情況下，您知道之外，編譯器會完成。 如果您刻意進行縮小轉換，讓您自己的意願明確使用靜態轉型。 否則，這則警告訊息通常表示程式碼中有錯誤。 您可以藉由確認您初始化的物件有夠大，無法處理輸入的型別來修正它。  
  
 下列範例會產生 C4838，並示範一種方法來修正此問題︰  
  
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
