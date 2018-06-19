---
title: 編譯器錯誤 C2365 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2365
dev_langs:
- C++
helpviewer_keywords:
- C2365
ms.assetid: 35839b0b-4055-4b79-8957-b3a0871bdd02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 952d1ea71f0388b26d72e3cbdcb10185813242e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33223631"
---
# <a name="compiler-error-c2365"></a>編譯器錯誤 C2365
'class member': 重複定義，先前的定義是 'class member'  
  
 您嘗試要重新定義類別成員。  
  
 下列範例會產生 C2365。  
  
```  
// C2365.cpp  
// compile with: /c  
class C1 {  
   int CFunc();  
   char *CFunc;   // C2365, already exists as a member function  
  
   int CMem;  
   char *CMem();   // C2365, already exists as a data member  
};  
```