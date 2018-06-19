---
title: 編譯器錯誤 C3162 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3162
dev_langs:
- C++
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1527e56bbd834f2ebea9c51f82bb55c05da52d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253796"
---
# <a name="compiler-error-c3162"></a>編譯器錯誤 C3162
'type': 具有解構函式的參考型別不能為靜態資料成員 'member' 的型別  
  
 Common language runtime 無法得知何時該類別也包含靜態成員函式時執行使用者定義解構函式。  
  
 永遠不會執行解構函式，除非明確地刪除物件。  
  
 如需詳細資訊，請參閱：  
  
-   [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C++ 64 位元移轉時常見的問題](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>範例  
 下列範例會產生 C3162。  
  
```  
// C3162.cpp  
// compile with: /clr /c  
ref struct A {  
   ~A() { System::Console::WriteLine("in destructor"); }  
   static A i;   // C3162  
   static A^ a = gcnew A;   // OK  
};  
  
int main() {  
   A ^ a = gcnew A;  
   delete a;  
}  
```