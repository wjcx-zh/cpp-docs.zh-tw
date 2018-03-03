---
title: "編譯器警告 （層級 1） C4042 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0801b3fb34b85a6b07127111b38a35ee826028c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4042"></a>編譯器警告 （層級 1） C4042
'identifier': 具有錯誤的儲存類別  
  
 指定的儲存類別不能與這個識別碼在此內容中。 編譯器會改為使用預設的儲存類別：  
  
-   `extern`如果*識別碼*是函式。  
  
-   **自動**，如果*識別碼*是型式參數或區域變數。  
  
-   任何存放裝置類別，如果*識別碼*是全域變數。  
  
 此警告可能因以外指定儲存類別**註冊**參數宣告中。  
  
 下列範例會產生 C4042  
  
```  
// C4042.cpp  
// compile with: /W1 /LD  
int func2( __declspec( thread ) int tls_i )    // C4042  
// try the following line instead  
// int func2( int tls_i )  
{  
   return tls_i;  
}  
```