---
title: "連結器工具錯誤 LNK2020 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2020
dev_langs: C++
helpviewer_keywords: LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 394cafe23851df5320a78a4e165a90422fc305de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2020"></a>連結器工具錯誤 LNK2020
無法解析語彙基元 'token'  
  
 類似於發生未定義的外部錯誤，不同之處在於會透過中繼資料的參考。 在中繼資料，就必須定義所有函式和資料。  
  
 若要解決：  
  
-   定義遺漏函式或資料，或  
  
-   包含物件的檔案或遺漏的函式或資料已經定義所在的程式庫。  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK2020。  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## <a name="example"></a>範例  
 如果您建立 managed 的範本類型的變數，但請勿也產生型別，也會發生 LNK2020。  
  
 下列範例會產生 LNK2020。  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```