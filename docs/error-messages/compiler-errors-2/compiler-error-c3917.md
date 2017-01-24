---
title: "編譯器錯誤 C3917 | Microsoft Docs"
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
  - "C3917"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3917"
ms.assetid: a24cd0c9-262f-46e5-9488-1c01f945933d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3917
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'property': 過時的 construct 宣告樣式  
  
 屬性或事件定義使用了舊版的語法。  
  
 如果您要使用舊版的語法，請使用 [\/clr:oldSyntax](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 如需詳細資訊，請參閱[屬性](../../windows/property-cpp-component-extensions.md)。  
  
## 範例  
  
```  
// C3917.cpp  
// compile with: /clr /c  
public ref class  C {  
private:  
   int m_length;  
public:  
   C() {  
      m_length = 0;  
   }  
  
   property int get_Length();   // C3917  
  
   // The correct property definition:  
   property int Length {  
      int get() {  
         return m_length;  
      }  
  
      void set( int i ) {  
         m_length = i;  
      }  
   }  
};  
```