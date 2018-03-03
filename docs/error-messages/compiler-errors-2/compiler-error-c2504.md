---
title: "編譯器錯誤 C2504 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2504
dev_langs:
- C++
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7843d69b7238bedb58d0232d64ff2d0a826d07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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