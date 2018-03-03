---
title: "編譯器錯誤 C2779 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2779
dev_langs:
- C++
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afae21cdd5f22d30da9702438e910cd1a8f0db2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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