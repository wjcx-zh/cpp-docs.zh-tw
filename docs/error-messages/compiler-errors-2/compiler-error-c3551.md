---
title: "編譯器錯誤 C3551 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 450bd97efc9cfbf07eac84a3e6a693af698fc64f
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3551"></a>編譯器錯誤 C3551
"必須是晚期指定的傳回類型"  
  
 如果您使用 `auto` 關鍵字作為函式之傳回類型的預留位置，則必須提供晚期指定的傳回類型。 在下列範例中， `myFunction` 函式的晚期指定的傳回類型是一個指標，而這個指標指向類型 `int`之四個項目的陣列。  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## <a name="see-also"></a>另請參閱  
 [auto](../../cpp/auto-cpp.md)
