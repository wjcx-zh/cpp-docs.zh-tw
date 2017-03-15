---
title: "編譯器錯誤 C3734 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3734
dev_langs:
- C++
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: f63bb40c55298a5fd3b61b12aa5b3ddff2591b65
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3734"></a>編譯器錯誤 C3734
'class'：Managed 或 WinRT 類別不能是 coclass  
  
 [Coclass](../../windows/coclass.md)屬性不能與受管理或 WinRT 類別。  
  
 下列範例會產生 C3734，並示範如何修正此問題：  
  
```  
// C3734.cpp  
// compile with: /clr /c  
[module(name="x")];  
  
[coclass]  
ref class CMyClass {   // C3734 remove the ref keyword to resolve  
};  
```  

