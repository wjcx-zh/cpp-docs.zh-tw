---
title: "編譯器錯誤 C3492 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3492
dev_langs:
- C++
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: ff183b8a5171bc3849c4e8dd132dce6d75323f4e
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3492"></a>編譯器錯誤 C3492
'var': 您無法擷取匿名等位的成員  
  
 您無法擷取未命名等位的成員。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   為等位命名，並將完整的等位結構傳遞至 Lambda 運算式的擷取清單。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3492，因為它會擷取匿名等位的成員：  
  
```  
// C3492a.cpp  
  
int main()  
{  
   union  
   {  
      char ch;  
      int x;  
   };  
  
   ch = 'y';  
   [&x](char ch) { x = ch; }(ch); // C3492  
}  
```  
  
## <a name="example"></a>範例  
 下列範例透過為等位命名，並將完整的等位結構傳遞至 Lambda 運算式的擷取清單，來解決 C3492：  
  
```  
// C3492b.cpp  
  
int main()  
{  
   union  
   {  
      char ch;  
      int x;  
   } u;  
  
   u.ch = 'y';  
   [&u](char ch) { u.x = ch; }(u.ch);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
