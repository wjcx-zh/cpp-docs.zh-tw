---
title: "編譯器錯誤 C3353 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3353
dev_langs:
- C++
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01f21bfce44b124955d84c7298cdcb6885ef87ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3353"></a>編譯器錯誤 C3353
'delegate'：只能從全域函式或 Managed 或 WinRT 類型的成員函式建立委派  
  
 以宣告的委派，[委派](../../windows/delegate-cpp-component-extensions.md)關鍵字，只能在全域範圍宣告。  
  
 下列範例會產生 C3353：  
  
```  
// C3353.cpp  
// compile with: /clr  
delegate int f;   // C3353  
```