---
title: 編譯器錯誤 C2803 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51cf2a8b38a86fcd97ab693b3853fe25527a0bb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236219"
---
# <a name="compiler-error-c2803"></a>編譯器錯誤 C2803
'operator operator' 必須至少一個類別類型的型式參數  
  
 多載的運算子的類別類型的參數。  
  
 您必須以傳址方式 (不使用指標，而使用參考) 或傳值方式傳遞至少一個參數，才能寫入 "a < b" (a 和 b 屬於類別 A 類型)。  
  
 如果這兩個參數都是指標，它將純的比較的指標位址，且不會使用使用者定義的轉換。  
  
 下列範例會產生 C2803:  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```