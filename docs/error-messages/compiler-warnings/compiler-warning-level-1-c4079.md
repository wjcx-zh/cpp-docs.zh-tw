---
title: "編譯器警告 (層級 1) C4079 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4079"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4079"
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4079
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非預期的語彙基元 'token'  
  
 未預期的分隔符號語彙基元 \(Token\) 發生在 pragma 引數清單。  忽略 pragma 的其餘部分。  
  
 下列範例會產生 C4079：  
  
```  
// C4079.cpp  
// compile with: /W1  
#pragma warning(disable : 4081)  
#pragma pack(c,16)   // C4079  
  
int main() {  
}  
```