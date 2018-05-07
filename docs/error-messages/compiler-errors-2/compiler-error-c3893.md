---
title: 編譯器錯誤 C3893 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3893
dev_langs:
- C++
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c95d44a90b9325a492a0f179c941d46ff24030c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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