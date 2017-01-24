---
title: "編譯器錯誤 C2217 | Microsoft Docs"
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
  - "C2217"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2217"
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2217
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute1' 需要有 'attribute2'  
  
 第一個函式屬性需要第二個屬性。  
  
### 若要修正，請檢查下列可能原因  
  
1.  插斷 \(`__interrupt`\) 函式宣告為 `near`。  插斷函式必須為 `far`。  
  
2.  插斷函式以 `__stdcall` 或 `__fastcall` 來宣告。  插斷函式必須使用 C 呼叫慣例 \(Calling Convention\)。  
  
## 範例  
 如果您嘗試將委派繫結至可接受變動數目之引數的 CLR 函式，也可能會發生 C2217。  如果此函式也有 e param 陣列多載，請改用此陣列多載。  下列範例會產生 C2217。  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```