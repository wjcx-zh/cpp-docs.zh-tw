---
title: "編譯器錯誤 C2397 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 31f2b548fd13bc7702d44ef4a6d5dc5c34a5eb3c
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2397"></a>編譯器錯誤 C2397
從 'type_1' 轉換為 'type_2' 需要縮小轉換  
  
 使用一致的初始化時，找不到隱含的縮小轉換。  
  
 C 語言允許在指派和初始化時，隱含的縮小轉換和 c + + 坐，即使意外縮小是造成許多程式碼錯誤的原因。 若要讓程式碼更安全，c + + 標準初始設定清單中的縮小轉換發生時需要診斷訊息。 Visual c + + 中，診斷時，編譯器錯誤 C2397 Visual Studio 2015 中使用一致的初始化支援語法開頭。 編譯器會產生[編譯器警告 （層級 1） C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)時使用的清單或 Visual Studio 2013 所支援的彙總初始化語法。  
  
 當您知道目標所能容納的轉換值的可能範圍縮小轉換可以是沒問題。 在此情況下，您知道之外，編譯器會完成。 如果您刻意進行縮小轉換，讓您自己的意願明確使用靜態轉型。 否則，此錯誤訊息幾乎都表示程式碼中有錯誤。 您可以藉由確認您初始化的物件有夠大，無法處理輸入的型別來修正它。  
  
 下列範例會產生 C2397，並示範一種方法來修正此問題︰  
  
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
