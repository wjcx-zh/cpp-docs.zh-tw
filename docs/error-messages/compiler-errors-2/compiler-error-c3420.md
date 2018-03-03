---
title: "編譯器錯誤 C3420 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3420
dev_langs:
- C++
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da0c47ccb08d1d4e9aa4c75fbce4d4fe8252a340
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3420"></a>編譯器錯誤 C3420
'finalizer'：完成項不可為虛擬  
  
 完成項不可為虛擬，否則無法從它的封入類型進行呼叫。 因此，宣告虛擬完成項會造成錯誤。  
  
 如需詳細資訊，請參閱[解構函式與完成項中如何： 定義和使用類別和結構 (C + + /CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3420：  
  
```  
// C3420.cpp  
// compile with: /clr /c  
ref class R {  
   virtual !R() {}   // C3420  
};  
```