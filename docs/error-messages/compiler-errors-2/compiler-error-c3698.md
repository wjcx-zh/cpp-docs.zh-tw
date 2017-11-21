---
title: "編譯器錯誤 C3698 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3698
dev_langs: C++
helpviewer_keywords: C3698
ms.assetid: 3c02fb08-7ba4-4637-a06f-19926cb2b5f1
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d49234a7fa0f607877482709c6629ba77cd31806
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3698"></a>編譯器錯誤 C3698
'type': 無法使用此類型為 'operator' 的引數  
  
 受管理的物件宣告不正確。  
  
 下列範例會產生 C3698:  
  
```  
// C3698.cpp  
// compile with: /clr  
  
int main() {  
   array<int>^a = new array<int>^(20);   // C3698  
   array<int>^a2 = gcnew array<int>(20);   // OK  
}  
```