---
title: "編譯器錯誤 C3551 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3551
dev_langs:
- C++
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
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
ms.openlocfilehash: f9acd3751e5024cd3abb93496ef8ff2ea4322e8d
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3551"></a>編譯器錯誤 C3551
"必須是晚期指定的傳回類型"  
  
 如果您使用 `auto` 關鍵字作為函式之傳回類型的預留位置，則必須提供晚期指定的傳回類型。 在下列範例中， `myFunction` 函式的晚期指定的傳回類型是一個指標，而這個指標指向類型 `int`之四個項目的陣列。  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## <a name="see-also"></a>另請參閱  
 [auto](../../cpp/auto-cpp.md)
