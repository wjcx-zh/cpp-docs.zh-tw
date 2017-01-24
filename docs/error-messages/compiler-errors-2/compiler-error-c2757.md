---
title: "編譯器錯誤 C2757 | Microsoft Docs"
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
  - "C2757"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2757"
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2757
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol': 已經有使用此名稱的符號，因此無法使用此名稱當做命名空間名稱  
  
 目前編譯中用來做為命名空間 \(Namespace\) 識別項的符號已經用在參考的組譯碼 \(Assembly\) 上。  
  
 下列範例會產生 C2757：  
  
```  
// C2757a.cpp  
// compile with: /clr /LD  
public ref class Nes {};  
```  
  
 然後，  
  
```  
// C2757b.cpp  
// compile with: /clr /c  
#using <C2757a.dll>  
  
namespace Nes {    // C2757  
// try the following line instead  
// namespace Nes2 {  
   public ref class X {};  
}  
```  
  
 下列範例會產生 C2757：  
  
```  
// C2757c.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
public __gc class Nes {};  
```  
  
 然後，  
  
```  
// C2757d.cpp  
// compile with: /clr:oldSyntax /c  
#using <C2757c.dll>  
#using <mscorlib.dll>  
  
namespace Nes {    // C2757  
// try the following line instead  
// namespace Nes2 {  
   public __gc class X {};  
}  
```