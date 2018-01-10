---
title: "嚴重錯誤 C1022 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1022
dev_langs: C++
helpviewer_keywords: C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dfa41aad6cb03840d0fa4c6a6ee9622d5f5c57e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1022"></a>嚴重錯誤 C1022
需要對應的 #endif  
  
 `#if`、 `#ifdef`或 `#ifndef` 指示詞沒有相符的 `#endif` 指示詞。 每個 `#if`、 `#ifdef`或 `#ifndef` 務必要有相符的 `#endif`。  
  
 下列範例會產生 C1022：  
  
```  
// C1022.cpp  
#define true 1  
  
#if (true)  
#else   
#else    // C1022  
```  
  
 可能的解決方式：  
  
```  
// C1022b.cpp  
// compile with: /c  
#define true 1  
  
#if (true)  
#else   
#endif  
```