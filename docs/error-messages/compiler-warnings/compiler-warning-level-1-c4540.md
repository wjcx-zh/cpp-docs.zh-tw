---
title: 編譯器警告 （層級 1） C4540 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3939ad2bbcba1ab3b492d83bdbb8f7076c2c5f2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283058"
---
# <a name="compiler-warning-level-1-c4540"></a>編譯器警告 (層級 1) C4540
用來將轉換成無法存取或模稜兩可的基底; dynamic_cast執行階段測試將會失敗 ('type1' 到 'type2')  
  
 您使用`dynamic_cast`到另一種類型的轉換。 編譯器會決定轉型永遠會失敗 (傳回**NULL**) 因為無法存取基底類別 (`private`、 執行個體) 或模稜兩可 （例如，類別階層架構中出現超過一次）。  
  
 以下顯示此警告的範例。 類別**B**衍生自類別**A**。程式會使用`dynamic_cast`轉換自類別**B** （在衍生的類別） 類別**A**，這一律都會失敗，因為類別**B**是`private`，因此無法存取。 變更的存取權**A**至**公用**會解決這個警告。  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```