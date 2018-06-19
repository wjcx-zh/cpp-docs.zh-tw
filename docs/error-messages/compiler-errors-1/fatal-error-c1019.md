---
title: 嚴重錯誤 C1019 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1019
dev_langs:
- C++
helpviewer_keywords:
- C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 119ff2df1554467762c0b960e80ad4c241517628
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198673"
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