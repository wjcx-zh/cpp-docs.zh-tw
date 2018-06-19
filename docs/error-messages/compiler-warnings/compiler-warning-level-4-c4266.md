---
title: 編譯器警告 （層級 4） C4266 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4266
dev_langs:
- C++
helpviewer_keywords:
- C4266
ms.assetid: 90ec5f5b-3451-4c16-bb1b-c30a626bdaa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecbf7326b79cd22cdff6c094d8dc0c7f9113deb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294556"
---
# <a name="compiler-warning-level-4-c4266"></a>編譯器警告 (層級 4) C4266
'function': 沒有覆寫的基底 'type'; 虛擬成員函式函式已隱藏  
  
 在衍生的類別不會覆寫虛擬函式的所有多載。  
  
 此警告預設為關閉。  如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
 下列範例會產生 C4266:  
  
```  
// C4266.cpp  
// compile with: /W4 /c  
#pragma warning (default : 4266)  
class Engine {  
public:  
   virtual void OnException(int&,int);  
   virtual void OnException(int&,int&,int);  
};  
  
class LocalBinding : private Engine {  
   virtual void OnException(int&,int);  
};   // C4266  
```  
  
 可能的解決方式：  
  
```  
// C4266b.cpp  
// compile with: /W4 /c  
#pragma warning (default : 4266)  
class Engine {  
public:  
   virtual void OnException(int&,int);  
   virtual void OnException(int&,int&,int);  
};  
  
class LocalBinding : private Engine {  
   virtual void OnException(int&,int);  
   virtual void OnException(int&, int&, int);  
};  
```