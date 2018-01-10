---
title: "編譯器錯誤 C3283 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3283
dev_langs: C++
helpviewer_keywords: C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c58f8b41a521388d1eab6e03b76646785a9239d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3283"></a>編譯器錯誤 C3283
'type': 介面不能有執行個體建構函式  
  
 CLR [介面](../../windows/interface-class-cpp-component-extensions.md) 不能有執行個體建構函式。  允許靜態建構函式。  
  
 下列範例會產生 C3283：  
  
```  
// C3283.cpp  
// compile with: /clr  
interface class I {  
   I();   // C3283  
};  
```  
  
 可能的解決方式：  
  
```  
// C3283b.cpp  
// compile with: /clr /c  
interface class I {  
   static I(){}  
};  
```