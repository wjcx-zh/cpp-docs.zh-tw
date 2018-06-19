---
title: 編譯器錯誤 C3353 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3353
dev_langs:
- C++
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47c9d1dd8c21e56613b9da00fc2bf4f7fbeafcca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253901"
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