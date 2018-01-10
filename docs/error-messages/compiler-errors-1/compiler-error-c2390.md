---
title: "編譯器錯誤 C2390 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2390
dev_langs: C++
helpviewer_keywords: C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 93d4cbd9de274d53fdc0369c2b85dbf2e97af48f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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