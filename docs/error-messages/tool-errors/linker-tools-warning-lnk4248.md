---
title: 連結器工具警告 LNK4248 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4248
dev_langs:
- C++
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3b67661d1ad260f388f8425420711ae2f708ce3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302629"
---
# <a name="linker-tools-warning-lnk4248"></a>連結器工具警告 LNK4248
無法解析的 typeref 語彙基元 (token) 的 'type';映像可能無法執行  
  
 類型沒有定義 MSIL 中繼資料中。  
  
 向前宣告 MSIL 模組中的型別時，可能會發生 LNK4248 (編譯 **/clr**)，將會在 MSIL 模組中，參考的型別，而其中 MSIL 模組與原生模組已定義的連結型別。  
  
 在此情況下，連結器會提供 MSIL 中繼資料的原生型別定義，這可能會提供正確的行為。  
  
 不過，如果 CLR 型別轉送類型宣告，然後連結器的原生類型定義可能不正確  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  提供的 MSIL 模組的類型定義。  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK4248。 定義結構 A，解決問題。  
  
```  
// LNK4248.cpp  
// compile with: /clr /W1  
// LNK4248 expected  
struct A;  
void Test(A*){}  
  
int main() {  
   Test(0);  
}  
```  
  
## <a name="example"></a>範例  
 下列範例已轉送的類型定義。  
  
```  
// LNK4248_2.cpp  
// compile with: /clr /c  
class A;   // provide a definition for A here to resolve  
A * newA();  
int valueA(A * a);  
  
int main() {  
   A * a = newA();  
   return valueA(a);  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK4248。  
  
```  
// LNK4248_3.cpp  
// compile with: /c  
// post-build command: link LNK4248_2.obj LNK4248_3.obj  
class A {  
public:   
   int b;  
};  
  
A* newA() {  
   return new A;  
}  
  
int valueA(A * a) {  
   return (int)a;  
}  
```