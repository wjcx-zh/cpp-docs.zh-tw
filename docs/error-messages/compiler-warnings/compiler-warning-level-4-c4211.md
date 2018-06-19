---
title: 編譯器警告 （層級 4） C4211 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4211
dev_langs:
- C++
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8112927940e5e2f17a4e74e2855a035bc7d5e5cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292343"
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
  
## <a name="see-also"></a>另請參閱  


