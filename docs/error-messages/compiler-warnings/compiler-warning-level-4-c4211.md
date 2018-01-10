---
title: "編譯器警告 （層級 4） C4211 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4211
dev_langs: C++
helpviewer_keywords: C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8967efb23a534f4d9d46b8e61f0045c4d1c5c3b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4211"></a>編譯器警告 (層級 4) C4211
使用非標準擴充： extern 重新定義為靜態  
  
 具有預設的 Microsoft 擴充功能 (/Ze) 中，您可以重新定義`extern`識別碼，則為**靜態**。  
  
## <a name="example"></a>範例  
  
```  
// C4211.c  
// compile with: /W4  
extern int i;  
static int i;   // C4211  
  
int main()  
{  
}  
```  
  
 這類重新定義不正確 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。  
  
## <a name="see-also"></a>請參閱  


