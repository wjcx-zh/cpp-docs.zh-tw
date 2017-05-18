---
title: "編譯器錯誤 C2492 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 54a650e967acb2ee0b6864780823111b4db9414c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/24/2017

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
