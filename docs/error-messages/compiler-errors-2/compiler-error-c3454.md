---
title: "編譯器錯誤 C3454 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3454
dev_langs:
- C++
helpviewer_keywords:
- C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
caps.latest.revision: 6
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
ms.openlocfilehash: 68d0930b7c80dfa997eddb55b01f9d9c313b611e
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3454"></a>編譯器錯誤 C3454
類別宣告上不允許 [attribute]  
  
 必須定義類別，它才能是屬性。  
  
 如需詳細資訊，請參閱[屬性](../../windows/attribute.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3454。  
  
```  
// C3454.cpp  
// compile with: /clr /c  
using namespace System;  
  
[attribute]   // C3454  
ref class Attr1;  
  
[attribute]   // OK  
ref class Attr2 {};  
```
