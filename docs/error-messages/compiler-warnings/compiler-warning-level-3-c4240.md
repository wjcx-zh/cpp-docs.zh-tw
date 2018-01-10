---
title: "編譯器警告 （層級 3） C4240 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4240
dev_langs: C++
helpviewer_keywords: C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 662aaeb3246fac20bd0ac9f3412424bfacac5698
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4240"></a>編譯器警告 (層級 3) C4240
使用非標準擴充： 存取 'classname' 現在已經定義為 '存取規範'，之前它定義為 '存取規範'  
  
 在 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，您無法將存取變更為巢狀類別。 在預設的 Microsoft 擴充功能 (/Ze) 中，您可以產生這則警告。  
  
## <a name="example"></a>範例  
  
```  
// C4240.cpp  
// compile with: /W3  
class X  
{  
private:  
   class N;  
public:  
   class N  
   {   // C4240  
   };  
};  
  
int main()  
{  
}  
```