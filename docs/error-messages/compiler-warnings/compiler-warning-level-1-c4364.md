---
title: "編譯器警告 (層級 1) C4364 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4364"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4364"
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4364
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

組件 'file' 的 \#using 先前在 location\(line\_number\) 看到，沒有 as\_friend 屬性；未套用 as\_friend  
  
 `#using` 指示詞為指定的中繼檔案重複，但是未在第一次出現時使用 `as_friend` 限定詞；編譯器將忽略第二個 `as_friend`。  
  
 如需詳細資訊，請參閱[Friend 組件 \(C\+\+\)](../../dotnet/friend-assemblies-cpp.md)。  
  
## 範例  
 下列範例會建立元件。  
  
```  
// C4364.cpp  
// compile with: /clr /LD  
ref class A {};  
```  
  
## 範例  
 下列範例會產生 C4364。  
  
```  
// C4364_b.cpp  
// compile with: /clr /W1 /c  
#using " C4364.dll"  
#using " C4364.dll" as_friend   // C4364  
```