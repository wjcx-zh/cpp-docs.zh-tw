---
title: "遺漏函式主體或變數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 356d0f0a71feccee953a0b1bd7dc54bc64a0e233
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="missing-function-body-or-variable"></a>遺漏函式主體或變數
只要函式原型，編譯器可以繼續執行而沒有錯誤，但連結器無法解析位址的呼叫，因為沒有任何函式程式碼或變數保留的空間。 建立連結器必須解析的函式呼叫之前，將不會看到這個錯誤。  
  
## <a name="example"></a>範例  
 在 main 函式呼叫會產生 LNK2019，因為此原型可讓編譯器在認為有的函式。  連結器會尋找它不會。  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## <a name="example"></a>範例  
 在 c + +，請確定您在類別定義中包含類別，並不只是原型的特定函式的實作。 如果您正在定義的類別標頭檔之外，務必要包含在函式之前的類別名稱 (`Classname::memberfunction`)。  
  
```  
// LNK2019_MFBV_2.cpp  
// LNK2019 expected  
struct A {  
   static void Test();  
};  
  
// Should be void A::Test() {}  
void Test() {}  
  
int main() {  
   A AObject;  
   AObject.Test();  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)