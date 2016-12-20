---
title: "編譯器錯誤 C3162 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3162"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3162"
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3162
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 是參考型別，具有無法用做靜態資料成員 'member' 之型別的解構函式 \(Destructor\)  
  
 當類別也包含靜態成員函式時，Common Language Runtime 無法得知何時執行使用者定義的解構函式。  
  
 除非明確地刪除物件，否則將永遠無法執行解構函式。  
  
 如需詳細資訊，請參閱：  
  
-   [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C\+\+ 64 位元移轉時常見的問題](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## 範例  
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