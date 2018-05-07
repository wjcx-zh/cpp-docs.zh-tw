---
title: 編譯器錯誤 C2492 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68b3d769c5b86be172a0a27828fb1dc3905959d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2492"></a>編譯器錯誤 C2492
'*變數*': 具有執行緒儲存期的資料可能不會有 dll 介面    
  
 變數宣告與[執行緒](../../cpp/thread.md)屬性，並使用的 DLL 介面。 位址`thread`變數未知到執行階段，讓它無法連結至 DLL 匯入或匯出。  
  
 下列範例會產生 C2492:  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```