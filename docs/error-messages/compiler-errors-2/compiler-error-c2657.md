---
title: 編譯器錯誤 C2657 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2657
dev_langs:
- C++
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70814ce7423bee3147f68d6298babc10eeac56fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231367"
---
# <a name="compiler-error-c2657"></a>編譯器錯誤 C2657
' 類別:: *' 陳述式開頭找到 （您是否忘記指定類型？）  
  
 行開頭的成員指標的識別項。  
  
 這個錯誤可能被因成員指標的宣告中遺漏類型規範。  
  
 下列範例會產生 C2657:  
  
```  
// C2657.cpp  
class C {};  
int main() {  
   C::* pmc1;        // C2657  
   int C::* pmc2;   // OK  
}  
```