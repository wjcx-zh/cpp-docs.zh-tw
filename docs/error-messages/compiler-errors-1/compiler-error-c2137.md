---
title: "編譯器錯誤 C2137 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2137
dev_langs: C++
helpviewer_keywords: C2137
ms.assetid: 984687ee-7766-4f6b-ae15-0c9a010e2366
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d91420979ca9a7d2c3667aa7fa4664f09543ea8f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2137"></a>編譯器錯誤 C2137
空白的字元常數  
  
 不允許空白的字元常數 ( ' ' )。  
  
 下列範例會產生 C2137：  
  
```  
// C2137.cpp  
int main() {  
   char c = '';   // C2137  
   char d = ' ';   // OK  
}  
```