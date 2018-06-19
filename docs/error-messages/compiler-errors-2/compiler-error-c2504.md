---
title: 編譯器錯誤 C2504 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2504
dev_langs:
- C++
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bac0f8f28955af172590535568289182c3489d6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229512"
---
# <a name="compiler-error-c2504"></a>編譯器錯誤 C2504
'class': 基底類別未定義  
  
 基底類別已宣告但永遠不會定義。  可能的原因：  
  
1.  遺漏 include 檔案。  
  
2.  外部的基底類別未宣告與[extern](../../cpp/using-extern-to-specify-linkage.md)。  
  
 下列範例會產生 C2504:  
  
```  
// C2504.cpp  
// compile with: /c  
class A;  
class B : public A {};   // C2504  
```  
  
 [確定]  
  
```  
class C{};  
class D : public C {};  
```