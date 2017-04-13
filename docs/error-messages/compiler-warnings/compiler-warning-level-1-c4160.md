---
title: "編譯器警告 （層級 1） C4160 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4160
dev_langs:
- C++
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: e8662a40b81a18ab4eed2fe50467977879762371
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4160"></a>編譯器警告 (層級 1) C4160
**#pragma**   
 ***pragma* (pop，...): 未發現之前推入的識別項 '**   
 ***識別項*'**  
  
 原始程式碼中的 pragma 陳述式嘗試快顯尚未推入的識別項。 若要避免這個警告，請確定已正確推入所快顯的識別項。  
  
 下列範例會產生 C4160：  
  
```  
// C4160.cpp  
// compile with: /W1  
#pragma pack(push)  
  
#pragma pack(pop, id)   // C4160  
// use identifier when pushing to resolve the warning  
// #pragma pack(push, id)  
  
int main() {  
}  
```
