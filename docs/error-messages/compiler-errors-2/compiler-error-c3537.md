---
title: 編譯器錯誤 C3537 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3537
dev_langs:
- C++
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f03f02062e61e4034f0a809784ba571ce532e07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3537"></a>編譯器錯誤 C3537
'type': 您無法轉換成此型別包含 'auto'  
  
 您無法轉換為指定類型的變數，因為類型包含`auto`關鍵字和預設[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)作用中時，編譯器選項。  
  
## <a name="example"></a>範例  
 下列程式碼會產生 C3537，因為變數會轉換成此型別包含`auto`關鍵字。  
  
```  
// C3537.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int value = 123;  
   auto(value);                        // C3537  
   (auto)value;                        // C3537  
   auto x1 = auto(value);              // C3537  
   auto x2 = (auto)value;              // C3537  
   auto x3 = static_cast<auto>(value); // C3537  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)