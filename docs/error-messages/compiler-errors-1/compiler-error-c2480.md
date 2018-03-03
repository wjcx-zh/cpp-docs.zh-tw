---
title: "編譯器錯誤 C2480 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2480
dev_langs:
- C++
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b8b350c8f9098c56c503041614a4e68c780af5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2480"></a>編譯器錯誤 C2480
'identifier': 'thread' 只是對靜態延伸的資料項目有效  
  
 您無法使用`thread`自動變數、 非靜態資料成員、 函式參數或函式宣告或定義的屬性。  
  
 使用`thread`全域變數、 靜態資料成員和靜態區域變數只屬性。  
  
 下列範例會產生 C2480:  
  
```  
// C2480.cpp  
// compile with: /c  
__declspec( thread ) void func();   // C2480  
__declspec( thread ) static int i;   // OK  
```