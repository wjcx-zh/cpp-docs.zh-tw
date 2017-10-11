---
title: "編譯器錯誤 C2390 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 37803b8eb5034fb3281dcea385b4a0fca462aaf0
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2390"></a>編譯器錯誤 C2390
'identifier': 不正確的儲存類別 'specifier'  
  
 儲存類別不是有效的全域範圍識別項。 預設的儲存類別用來取代無效的類別。  
  
 可能的解決方式：  
  
-   如果識別項是函數，將它與宣告`extern`儲存體。  
  
-   如果識別項是型式參數或區域變數，請將它宣告具有自動儲存。  
  
-   如果識別碼的全域變數，請將它宣告使用任何儲存類別 （自動儲存體）。  
  
## <a name="example"></a>範例  
  
-   下列範例會產生 C2390:  
  
```  
// C2390.cpp  
register int i;   // C2390  
  
int main() {  
   register int j;   // OK  
}  
```
