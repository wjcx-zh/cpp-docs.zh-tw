---
title: "編譯器錯誤 C3895 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3895
dev_langs: C++
helpviewer_keywords: C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9343a7d6f85864de809aea5d83965e65e9f5b70b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3895"></a>編譯器錯誤 C3895
'var': 型別資料成員不可為 'volatile'  
  
 某些類型的資料成員，例如[常值](../../windows/literal-cpp-component-extensions.md)或[initonly](../../dotnet/initonly-cpp-cli.md)，不能[volatile](../../cpp/volatile-cpp.md)。  
  
 下列範例會產生 C3895:  
  
```  
// C3895.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly  
   volatile int data_var2;   // C3895  
};  
```