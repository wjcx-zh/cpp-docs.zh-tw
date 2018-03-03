---
title: "編譯器錯誤 C3195 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3195
dev_langs:
- C++
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 840aa93a7955c6eda2720da8457624e00fe97fca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3195"></a>編譯器錯誤 C3195
'operator': 已被保留，不能做為 ref 類別或實值型別的成員。 必須使用 'operator' 關鍵字定義 CLR 或 WinRT 運算子  
  
編譯器偵測到使用 Managed Extensions for C++ 語法的運算子定義。 您必須使用 c + + 語法的運算子。  
  
下列範例會產生 C3195，並示範如何修正此問題：  
  
```  
// C3195.cpp  
// compile with: /clr /LD  
#using <mscorlib.dll>  
value struct V {  
   static V op_Addition(V v, int i);   // C3195  
   static V operator +(V v, char c);   // OK for new C++ syntax   
};  
```