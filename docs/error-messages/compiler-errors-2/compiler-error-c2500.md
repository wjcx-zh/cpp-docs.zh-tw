---
title: 編譯器錯誤 C2500 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c05ffd59e415375dd3c7f94ae9bc377c0fc2b9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229218"
---
# <a name="compiler-error-c2500"></a>編譯器錯誤 C2500
'identifier1': 'identifier2' 已經是直接基底類別  
  
 類別或結構出現在基底類別清單中出現一次以上。  
  
 直接基底是其中一個基底清單中所述。 而間接基底是其中一個基底清單中的類別的基底類別。  
  
 類別不能指定直接基底類別為一次以上。 類別可以當做間接基底類別一次以上。  
  
 下列範例會產生 C2500:  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```