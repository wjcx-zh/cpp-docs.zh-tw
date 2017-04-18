---
title: "編譯器錯誤 C2012 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2012
dev_langs:
- C++
helpviewer_keywords:
- C2012
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
caps.latest.revision: 7
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
ms.openlocfilehash: abd50581ebfadb732055d54a5ba6c55e40386aa9
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2012"></a>編譯器錯誤 C2012
'<' 之後遺漏名稱  
  
 `#include` 指示詞缺少必要的檔名。  
  
 下列範例會產生 C2012：  
  
```  
// C2012.cpp  
#include <   // C2012 include the filename to resolve  
```  
  
 可能的解決方式：  
  
```  
// C2012b.cpp  
// compile with: /c  
#include <stdio.h>  
```
