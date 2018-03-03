---
title: "嚴重錯誤 C1019 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1019
dev_langs:
- C++
helpviewer_keywords:
- C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 77374884efcb7aee367e436f9dc07c8df9c398d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1019"></a>嚴重錯誤 C1019
未預期的 #else  
  
 `#else` 指示詞出現在 `#if`、 `#ifdef`或 `#ifndef` 建構外部。 請僅在其中一個建構內使用 `#else` 。  
  
 下列範例會產生 C1019：  
  
```  
// C1019.cpp  
#else   // C1019  
#endif  
  
int main() {}  
```  
  
 可能的解決方式：  
  
```  
// C1019b.cpp  
#if 1  
#else  
#endif  
  
int main() {}  
```