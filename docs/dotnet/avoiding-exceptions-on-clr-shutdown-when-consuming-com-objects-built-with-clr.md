---
title: 避免使用-clr 所建置的 COM 物件擲回的例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
ms.openlocfilehash: bafcfb4e8a8abfecc8491220202b63971bef1ac8
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749239"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>當使用以 /clr 建置的 COM 物件時防止 CLR 關閉之例外狀況

一旦 common language runtime (CLR) 會進入關機模式，原生函式具有有限存取權 CLR 服務。 COM 物件時嘗試呼叫版本上使用編譯 **/clr**CLR 會轉換成原生程式碼，再轉換回 iunknown:: Release 呼叫 （這定義在 managed 程式碼） 提供服務的 managed 程式碼。 CLR 可防止呼叫至 managed 程式碼，因為它是在關機模式。

若要解決此問題，請確定從發行方法呼叫的解構函式只能包含原生程式碼。

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
