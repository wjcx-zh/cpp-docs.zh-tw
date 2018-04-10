---
title: 避免使用 clr 所建置的 COM 物件擲回的例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 287c9831f8c604272b37ac85528d66fe640de557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>當使用以 /clr 建置的 COM 物件時防止 CLR 關閉之例外狀況
Common language runtime (CLR) 進入關機模式，一旦原生函式具有有限的 CLR 服務的存取權。 COM 物件時嘗試呼叫版本上使用編譯**/clr**、 CLR 轉換為原生程式碼，然後再轉換回服務 （這定義在 managed 程式碼） Iunknown 呼叫 managed 程式碼。 CLR 會防止回 managed 程式碼呼叫，因為它是在關機模式。  
  
 若要解決此問題，請從發行方法呼叫的解構函式只能包含原生程式碼。  
  
## <a name="see-also"></a>請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)