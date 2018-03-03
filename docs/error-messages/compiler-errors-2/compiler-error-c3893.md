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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fee017305c90d9da69f5432815c0005eb84352c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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