---
title: 編譯器錯誤 C2062 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11151a8e842796e4a5a8d45956782421daa1c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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