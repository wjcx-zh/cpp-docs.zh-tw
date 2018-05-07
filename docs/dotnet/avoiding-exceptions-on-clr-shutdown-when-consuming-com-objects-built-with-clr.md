---
title: 避免使用 clr 所建置的 COM 物件擲回的例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0efd2af7eb4bf8a70bff983d627f802f1976c6ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>當使用以 /clr 建置的 COM 物件時防止 CLR 關閉之例外狀況
Common language runtime (CLR) 進入關機模式，一旦原生函式具有有限的 CLR 服務的存取權。 COM 物件時嘗試呼叫版本上使用編譯 **/clr**、 CLR 轉換為原生程式碼，然後再轉換回服務 （這定義在 managed 程式碼） Iunknown 呼叫 managed 程式碼。 CLR 會防止回 managed 程式碼呼叫，因為它是在關機模式。  
  
 若要解決此問題，請從發行方法呼叫的解構函式只能包含原生程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)