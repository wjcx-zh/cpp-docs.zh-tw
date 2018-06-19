---
title: 編譯器錯誤 C3816 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3816
dev_langs:
- C++
helpviewer_keywords:
- C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be09db4d91b511583b3119f03df8abc61a0153e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269089"
---
# <a name="compiler-error-c3816"></a>編譯器錯誤 C3816
'declaration' 先前已宣告或定義使用不同的 managed 或 WinRTmodifier  
  
 向前宣告或實際宣告需要屬性宣告中沒有衝突和不一致。  
  
 下列範例會產生 C3816，並示範如何修正此問題：  
  
```  
// C3816a.cpp  
// compile with: /clr /c  
class C1;  
// try the following line instead  
// ref class C1;  
  
ref class C1{  // C3816, forward declaration does not use ref  
};  
```