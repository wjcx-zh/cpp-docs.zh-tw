---
title: 編譯器錯誤 C3213 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3213
dev_langs:
- C++
helpviewer_keywords:
- C3213
ms.assetid: 1f079e36-b3e9-40f8-8e95-08eeba3adc82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbfdbb3554aad858cf412ace7709bbf63b3ae311
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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