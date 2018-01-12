---
title: "編譯器錯誤 C2062 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2062
dev_langs: C++
helpviewer_keywords: C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4a006bed55f16e6ed94c3b5ed9415320acb86fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2062"></a>編譯器錯誤 C2062
類型 'type' 未預期  
  
 編譯器未預期的型別名稱。  
  
 下列範例會產生 C2062:  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 C2062 也可能是因為編譯器的方式建構函式的參數清單中的控制代碼未定義的類型。 如果編譯器遇到未定義 （拼字錯誤？） 的型別，則會假設建構函式是一個運算式，並發出 C2062。 若要解決，只使用定義的型別建構函式參數清單中。