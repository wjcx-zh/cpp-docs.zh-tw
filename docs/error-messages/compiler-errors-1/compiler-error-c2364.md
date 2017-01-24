---
title: "編譯器錯誤 C2364 | Microsoft Docs"
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
  - "C2364"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2364"
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2364
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 自訂屬性的型別不合法  
  
 自訂屬性的具名引數僅限於編譯時期常數。  例如，整數類資料型別 \(Integral Type，如 int、char 等\)、System::TYpe^ 和 System::Object^。  
  
## 範例  
 下列範例會產生 C2364。  
  
```  
// c2364.cpp  
// compile with: /clr /c  
using namespace System;  
  
[attribute(AttributeTargets::All)]  
public ref struct ABC {  
public:  
   // Delete the following line to resolve.  
   ABC( Enum^ ) {}   // C2364  
   ABC( int ) {}   // OK  
};  
```