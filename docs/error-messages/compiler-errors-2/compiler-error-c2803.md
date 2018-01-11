---
title: "編譯器錯誤 C2803 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2803
dev_langs: C++
helpviewer_keywords: C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2472c0e1182ad11f5ea95e3411649e6214b110ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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