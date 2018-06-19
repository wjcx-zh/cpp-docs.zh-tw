---
title: 編譯器錯誤 C2390 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a32a9ca77ba43e5f2866baed91b99103224dbc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198712"
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