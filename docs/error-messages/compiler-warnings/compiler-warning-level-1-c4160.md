---
title: "編譯器警告 （層級 1） C4160 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4160
dev_langs:
- C++
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6b35f0dbb5f8fbe65ab2e1b5c449176889a72f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4160"></a>編譯器警告 (層級 1) C4160
**#pragma**   
 ***pragma* (pop，...): 未發現之前推入的識別項 '**   
 ***識別項*'**  
  
 原始程式碼中的 pragma 陳述式嘗試快顯尚未推入的識別項。 若要避免這個警告，請確定已正確推入所快顯的識別項。  
  
 下列範例會產生 C4160：  
  
```  
// C4160.cpp  
// compile with: /W1  
#pragma pack(push)  
  
#pragma pack(pop, id)   // C4160  
// use identifier when pushing to resolve the warning  
// #pragma pack(push, id)  
  
int main() {  
}  
```