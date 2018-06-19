---
title: 編譯器警告 （層級 2） C4302 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4302
dev_langs:
- C++
helpviewer_keywords:
- C4302
ms.assetid: f5e1c939-e134-4cca-ba1e-9b15a81549ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f9a94e75b0d2ce522c2ec9f45d8a2386e85b136
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291800"
---
# <a name="compiler-warning-level-2-c4302"></a>編譯器警告 (層級 2) C4302
'conversion': 從 'type 1' 的截斷為 'type 2'  
  
 編譯器偵測到從較大的類型轉換為較小的類型。 資訊可能會遺失。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
 下列範例會產生 C4302:  
  
```  
// C4302.cpp  
// compile with: /W2  
#pragma warning(default : 4302)  
int main() {  
   int i;  
   char c = (char) &i;     // C4302  
   short s = (short) &i;   // C4302  
}  
```