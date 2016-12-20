---
title: "編譯器警告 C4355 | Microsoft Docs"
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
  - "C4355"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4355"
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4355
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'this' : 在基底成員初始設定式清單中使用  
  
 **this** 指標只能在非靜態成員函式內使用。  它無法在基底類別的初始設定式清單中使用。  
  
 基底類別建構函式及類別成員建構函式在 **this** 建構式之前被呼叫。  實際上，您已將指向尚未建構物件的指標傳送到其他建構函式。  如果其他建構函式在此存取任何成員或呼叫成員函式，結果會是未定義的。  直到所有建構完成為止，您都不可使用 **this** 指標。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4355：  
  
```  
// C4355.cpp  
// compile with: /w14355 /c  
#include <tchar.h>  
  
class CDerived;  
class CBase {  
public:  
   CBase(CDerived *derived): m_pDerived(derived) {};  
   ~CBase();  
   virtual void function() = 0;  
  
   CDerived * m_pDerived;  
};  
  
class CDerived : public CBase {  
public:  
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor  
   virtual void function() {};  
};  
  
CBase::~CBase() {  
   m_pDerived -> function();  
}  
  
int main() {  
   CDerived myDerived;  
}  
```