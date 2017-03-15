---
title: "編譯器錯誤 C3828 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3828"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3828"
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C3828
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'object type'：建立 Managed 或 WinRT 類別的執行個體時，不允許位置引數  
  
 建立 Managed 類型或 Windows 執行階段類型的物件時，您無法使用運算子 [ref new, gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md) 或 [new](../../cpp/new-operator-cpp.md) 的位置形式。  
  
 下列範例會產生 C3828，並示範如何修正此問題：  
  
```  
// C3828a.cpp  
// compile with: /clr  
ref struct M {  
};  
  
ref struct N {  
   static array<char>^ bytes = gcnew array<char>(256);  
};  
  
int main() {  
   M ^m1 = new (&N::bytes) M();   // C3828  
   // The following line fixes the error.  
   // M ^m1 = gcnew M();  
}  
```