---
title: "編譯器錯誤 C3846 | Microsoft Docs"
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
  - "C3846"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3846"
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3846
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 無法從 'assembly2' 匯入符號：因為 'symbol' 已經從其他組件 'assembly1' 匯入  
  
 無法自參考組件匯入符號，因為它之前已自另一個參考組件匯入。  
  
 下列範例會產生 C3846：  
  
```  
// C3846a.cpp  
// compile with: /LD /clr  
public ref struct G  
{  
};  
```  
  
 然後編譯這個檔案：  
  
```  
// C3846b.cpp  
// compile with: /clr  
#using "c3846a.dll"  
#using "c3846a.obj"   // C3846  
  
int main()  
{  
}  
```  
  
 下列範例會產生 C3846：  
  
```  
// C3846c.cpp  
// compile with: /LD /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc struct G  
{  
};  
```  
  
 然後編譯這個檔案：  
  
```  
// C3846d.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
#using "c3846c.dll"  
#using "c3846c.obj"   // C3846  
  
int main()  
{  
}  
```