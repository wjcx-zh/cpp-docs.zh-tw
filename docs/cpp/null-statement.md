---
title: "Null 陳述式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ecaa8d968efa9a3cd8c700d3d4dfe4cae0f0dd53
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="null-statement"></a>Null 陳述式
「 Null 陳述式 」 是運算式的陳述式與*運算式*遺失。 它對於呼叫陳述式，但是不進行運算式評估的語言語法相當實用。 它是由一個分號所構成。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [運算陳述式](../cpp/expression-statement.md)