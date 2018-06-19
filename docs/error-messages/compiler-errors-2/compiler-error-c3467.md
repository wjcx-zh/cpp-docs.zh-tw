---
title: 編譯器錯誤 C3467 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3467
dev_langs:
- C++
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ea834ff01f228b9b30f8acdafb665dbba743517
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256218"
---
# <a name="compiler-error-c3467"></a>編譯器錯誤 C3467
'type': 這個類型已經轉送了  
  
 編譯器發現相同類型的多個轉送類型宣告。 每種類型只允許一個宣告。  
  
 如需詳細資訊，請參閱[類型轉送 (C + + /CLI)](../../windows/type-forwarding-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會建立元件。  
  
```  
// C3467.cpp  
// compile with: /LD /clr  
public ref class R {};  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3467。  
  
```  
// C3467_b.cpp  
// compile with: /clr /c  
#using "C3467.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467  
```