---
title: "編譯器錯誤 C2019 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2019
dev_langs: C++
helpviewer_keywords: C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 93c91bccf1b9bc709d006696b22e0e8c2febb713
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2019"></a>編譯器錯誤 C2019
必須是前置處理器指示詞，但找到 'character'  
  
 字元後面接著`#`符號，但它不是前置處理器指示詞的第一個字母。  
  
 下列範例會產生 C2019:  
  
```  
// C2019.cpp  
#!define TRUE 1   // C2019  
```  
  
 可能的解決方式：  
  
```  
// C2019b.cpp  
// compile with: /c  
#define TRUE 1  
```