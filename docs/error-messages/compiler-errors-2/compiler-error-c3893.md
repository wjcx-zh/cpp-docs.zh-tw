---
title: "編譯器錯誤 C3893 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3893
dev_langs:
- C++
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 49097d988175e7571c5825b4d54e1dd496fb2ba7
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3893"></a>編譯器錯誤 C3893
'var': initonly 資料成員的左值使用只允許用於 'type_name' 類別的執行個體建構函式  
  
 靜態[initonly](../../dotnet/initonly-cpp-cli.md)資料成員只能有靜態的建構函式中使用其位址。  
  
 執行個體 （非靜態） initonly 資料成員只能有執行個體 （非靜態） 建構函式中使用其位址。  
  
 下列範例會產生 C3893:  
  
```  
// C3893.cpp  
// compile with: /clr  
ref struct Y1 {  
   Y1() : data_var(0) {  
      int% i = data_var;   // OK  
   }  
   initonly int data_var;  
};  
  
int main(){  
   Y1^ y= gcnew Y1;  
   int% i = y->data_var;   // C3893  
}  
```
