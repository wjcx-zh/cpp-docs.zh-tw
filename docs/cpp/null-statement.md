---
title: "Null 陳述式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "運算式 [C++], null"
  - "null 陳述式"
  - "null 值, 運算式"
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Null 陳述式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「null 陳述式」是一個不含「運算式」的運算陳述式。  它對於呼叫陳述式，但是不進行運算式評估的語言語法相當實用。  它是由一個分號所構成。  
  
 null 陳述式通常用來做為反覆項目陳述式中的預留位置，或做為在複合陳述式或函式的結尾放置一個標籤的陳述式。  
  
 下列程式碼片段顯示如何將某個字串複製到另一個字串，以及合併 null 陳述式：  
  
```  
// null_statement.cpp  
char *myStrCpy( char *Dest, const char *Source )  
{  
    char *DestStart = Dest;  
  
    // Assign value pointed to by Source to  
    // Dest until the end-of-string 0 is  
    // encountered.  
    while( *Dest++ = *Source++ )  
        ;   // Null statement.  
  
    return DestStart;  
}  
  
int main()  
{  
}  
```  
  
## 請參閱  
 [運算陳述式](../cpp/expression-statement.md)