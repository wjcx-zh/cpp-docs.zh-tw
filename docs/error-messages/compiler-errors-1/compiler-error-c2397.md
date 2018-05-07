---
title: 編譯器錯誤 C2397 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9d080450368618cc874de0ae96209e547847f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2397"></a>編譯器錯誤 C2397
從 'type_1' 轉換為 'type_2' 必須是縮小轉換  
  
 使用統一初始設定時，找不到隱含的縮小轉換。  
  
 C 語言允許在指派和初始化時，隱含的縮小轉換和 c + + 坐，即使未預期的縮小是許多程式碼錯誤的原因。 若要讓程式碼更安全，c + + 標準初始設定清單中的縮小轉換發生時需要診斷訊息。 在 Visual c + + 中，診斷時，編譯器錯誤 C2397 統一初始設定的支援語法開始使用 Visual Studio 2015 中。 編譯器會產生[編譯器警告 （層級 1） C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)時使用的清單或 Visual Studio 2013 所支援的彙總初始化語法。  
  
 當您知道目標所能容納轉換值的可能範圍時，可以是可以縮小轉換。 在此情況下，您知道編譯器會以上。 如果您刻意進行縮小轉換，您要的情況明確使用進行靜態轉型。 否則，此錯誤訊息幾乎都表示程式碼中有錯誤。 您可以藉由確定您初始化的物件具有值大到足以處理輸入的類型來修正此問題。  
  
 下列範例會產生 C2397，並示範修正此問題的一種方法：  
  
```  
// C2397.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C2397.cpp  
#include <vector>   
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C2397(double d1) {  
    char c1 { 127 };          // OK  
    char c2 { 513 };          // error C2397  
  
    std::vector<S1> vS1;  
    vS1.push_back({ d1, 2, 3 }); // error C2397  
  
    // Possible fix if you know d1 always fits in an int  
    vS1.push_back({ static_cast<int>(d1), 2, 3 });   
}  
```