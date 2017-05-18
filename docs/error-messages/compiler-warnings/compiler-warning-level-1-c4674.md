---
title: "編譯器警告 （層級 1） C4674 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
caps.latest.revision: 9
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ca99a22e6f91f44af58a1421d59151597017cddb
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4674"></a>編譯器警告 (層級 1) C4674
'method' 必須宣告為 'static'，而且只能有一個參數  
  
轉換運算子的簽章不正確。 此方法不會視為使用者定義的轉換。 如需有關定義操作員的詳細資訊，請參閱[使用者定義運算子 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)和[使用者定義轉換 (C + + /cli CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4674。  
  
```  
// C4674.cpp  
// compile with: /clr /WX /W1 /LD  
ref class G {  
   int op_Implicit(int i) {   // C4674  
      return 0;  
   }  
};  
```  

