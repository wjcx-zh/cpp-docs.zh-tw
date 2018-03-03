---
title: "編譯器錯誤 C3238 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3238
dev_langs:
- C++
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e729e0da83638c93dd7e79a55bc0960590f93f08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3238"></a>編譯器錯誤 C3238
'type': 具有這個名稱的類型已轉送至組件 'assembly'  
  
 在用戶端應用程式定義的類型，也透過類型轉送語法定義在參考的組件中。 在應用程式範圍內，無法定義這兩種類型。  
  
 請參閱[類型轉送 (C + + /CLI)](../../windows/type-forwarding-cpp-cli.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會建立組件，其中所包含的類型是從另一個組件轉送過來。  
  
```  
// C3238.cpp  
// compile with: /clr /LD  
public ref class R {};  
```  
  
## <a name="example"></a>範例  
 下列範例會建立包含類型定義的組件，而不只是包含類型轉送語法。  
  
```  
// C3238_b.cpp  
// compile with: /clr /LD  
#using "C3238.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3238：  
  
```  
// C3238_c.cpp  
// compile with: /clr /c  
// C3238 expected  
// Delete the following line to resolve.  
#using "C3238_b.dll"  
public ref class R {};  
```