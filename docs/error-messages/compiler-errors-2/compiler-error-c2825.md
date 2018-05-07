---
title: 編譯器錯誤 C2825 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2825
dev_langs:
- C++
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5352901d50e011229ed9aa4715923881c26a8fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2825"></a>編譯器錯誤 C2825
var： 必須是類別或命名空間後面所接 ':: '  
  
 若要形成完整的名稱已嘗試失敗。  
  
 例如，請確定您的程式碼不包含函式宣告的函式名稱會開頭::。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2825:  
  
```  
// C2825.cpp  
typedef int i;  
int main() {  
   int* p = new int;  
   p->i::i();   // C2825  
   // try the following line instead  
   // p->i::~i();  
}  
```