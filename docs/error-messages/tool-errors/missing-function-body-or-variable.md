---
title: 遺漏函式主體或變數 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54e2b8c5831eb6d487cf530df1b733b73580cbb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316721"
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
  
## <a name="see-also"></a>另請參閱  
 [連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)