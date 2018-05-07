---
title: 編譯器錯誤 C3539 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3539
dev_langs:
- C++
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f704bd283ab5228a8988d587707e978aa5b49e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3539"></a>編譯器錯誤 C3539
'type': 樣板引數不能包含 'auto' 的類型  
  
 指定的範本引數類型不能包含的使用量`auto`關鍵字。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  未指定樣板引數與`auto`關鍵字。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3539。  
  
```  
// C3539.cpp  
// Compile with /Zc:auto  
template<class T> class C{};  
int main()  
{  
   C<auto> c;   // C3539  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)