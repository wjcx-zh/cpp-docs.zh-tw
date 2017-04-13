---
title: "編譯器警告 （層級 1） C4794 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4794
dev_langs:
- C++
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 8f73e3da504960f737f175fff4c9d7b07084833a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4794"></a>編譯器警告 (層級 1) C4794
執行緒區域儲存區變數 'variable' 的區段已從 ''section name' 變更為 '.tls$'  
  
 您使用[#pragma data_seg](../../preprocessor/data-seg.md) tls 變數放入開頭不.tls$ 的區段中。  
  
 .Tls$*x* > 一節會存在於目的檔其中[__declspec （thread)](../../cpp/thread.md)變數所定義。 EXE 或 DLL 中的.tls 區段將會從這些區段產生。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4794：  
  
```  
// C4794.cpp  
// compile with: /W1 /c  
#pragma data_seg(".someseg")  
__declspec(thread) int i;   // C4794  
  
// OK  
#pragma data_seg(".tls$9")  
__declspec(thread) int j;  
```
