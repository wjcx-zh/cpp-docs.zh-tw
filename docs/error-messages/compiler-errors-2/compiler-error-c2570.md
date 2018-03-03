---
title: "編譯器錯誤 C2570 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2570
dev_langs:
- C++
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 873d71415e610ee1a7295cd425b9960360f8631f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2570"></a>編譯器錯誤 C2570
'identifier': 等位不能有基底類別  
  
 等位是衍生自類別、 結構或等位。 這是不允許的。 而是將衍生的型別宣告為類別或結構。  
  
 下列範例會產生 C2570:  
  
```  
// C2570.cpp  
// compile with: /c  
class base {};  
union hasPubBase : public base {};   // C2570  
union hasNoBase {};   // OK  
```