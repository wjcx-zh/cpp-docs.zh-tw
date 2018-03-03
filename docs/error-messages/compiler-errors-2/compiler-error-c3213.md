---
title: "編譯器錯誤 C3213 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3213
dev_langs:
- C++
helpviewer_keywords:
- C3213
ms.assetid: 1f079e36-b3e9-40f8-8e95-08eeba3adc82
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 593e967d944f4a29371469c69d80605e3e2579ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3213"></a>編譯器錯誤 C3213
基底類別 'base_type' 比 'derived_type' 更難以存取  
  
 要從組件顯示的類型必須使用公用可見的基底類別。  
  
 下列範例會產生 C3213：  
  
```  
// C3213.cpp  
// compile with: /clr  
private ref struct privateG {  
public:  
   int i;  
};  
  
public ref struct publicG {  
public:  
   int i;  
};  
  
public ref struct V : public privateG {   // C3213  
public:  
   int j;  
};  
  
public ref struct W: public publicG {   // OK  
public:  
   int j;  
};  
```