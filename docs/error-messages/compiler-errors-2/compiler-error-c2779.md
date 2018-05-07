---
title: 編譯器錯誤 C2779 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2779
dev_langs:
- C++
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1f16bd0e756895b0da98fd43d0d6b2fdee6e8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2779"></a>編譯器錯誤 C2779
'declaration': 只能和非靜態資料成員相關聯的屬性方法  
  
 `property`擴充的屬性不正確地套用至靜態資料成員。  
  
 下列範例會產生 C2779:  
  
```  
// C2779.cpp  
struct A {  
   static __declspec(property(put=PutProp))  
   // try the following line instead  
   __declspec(property(put=PutProp))  
      int prop;   // C2779  
   int PutProp(void);  
};  
```