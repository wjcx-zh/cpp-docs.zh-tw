---
title: "編譯器錯誤 C3817 | Microsoft Docs"
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
  - "C3817"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3817"
ms.assetid: c6dbb57a-c65e-4040-8dd2-85bd9d4fd337
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3817
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaration' : 屬性只可以套用至函式  
  
 [property](../../misc/property.md) 關鍵字只可套用至函式定義。  
  
 C3817 只能透過 **\/clr:oldSyntax** 取得。  
  
 下列範例會產生 C3817：  
  
```  
// C3817.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc class G {  
      __property int x;   // C3817  
   };  
  
// the following class defines a property  
__gc class X {  
public:  
   __property int get_N( int i ) {  
      Console::WriteLine( L"int" );  
      return m_val[i];  
   }  
  
   __property void set_N( int i, int val ) {  
      m_val[i] = val;  
   }  
  
private:  
   int m_val[10];  
};  
  
int main() {  
}  
```