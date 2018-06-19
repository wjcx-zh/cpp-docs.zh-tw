---
title: 編譯器錯誤 C2555 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2d1a710177e2c8c72b0afeff662dddf1c22ef5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230579"
---
# <a name="compiler-error-c2555"></a>編譯器錯誤 C2555
'class1::function1': 覆寫虛擬函式傳回類型不同，而且不是從 'class2::function2' 的 covariant  
  
 虛擬函式和衍生的覆寫函式有相同的參數清單，但傳回型別不同。 在衍生類別中的覆寫函式不能從虛擬函式只能由其傳回類型的基底類別中的不同。  
  
 若要解決這個錯誤，將傳回值轉換的虛擬函式呼叫之後。  
  
 如果您以 /clr 編譯，您也可能會看到這個錯誤。   例如，Visual c + + 相當於下列 C# 宣告：  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 是  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 如需有關 C2555 的詳細資訊，請參閱知識庫文件 Q240862。  
  
 下列範例會產生 C2555:  
  
```  
// C2555.cpp  
// compile with: /c  
struct X {  
   virtual void func();  
};  
struct Y : X {  
   char func();  // C2555  
   void func2();   // OK  
};  
```