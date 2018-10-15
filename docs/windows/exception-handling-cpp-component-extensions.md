---
title: 例外狀況處理 (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d070cc223f90f84bd52176ee7e50dbbfa441789
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328125"
---
# <a name="exception-handling--ccli-and-ccx"></a>例外狀況處理 (C + + /cli 和 C + + /CX)

應用程式編譯`/ZW`編譯器選項或`/clr`兩者都使用的編譯器選項*例外狀況*程式執行期間處理未預期的錯誤。 下列主題將討論 C++/CX 或 C++/CLI 應用程式中的例外狀況處理。

## <a name="in-this-section"></a>本節內容

[使用 Managed 例外狀況的基本概念](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
描述擲回例外狀況，並使用**嘗試**/**攔截**區塊。

[例外狀況處理行為 /clr 之下的差異](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
討論與標準 C++ 例外狀況處理行為的差異。

[finally](../dotnet/finally.md)<br/>
討論如何使用 finally 關鍵字。

[如何：定義與安裝全域例外狀況處理常式](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
示範如何擷取未處理的例外狀況。

[如何：攔截 MSIL 擲回之機器碼的例外狀況](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
討論如何攔截機器碼中的 CLR 和 C++ 例外狀況。

[如何：定義與安裝全域例外狀況處理常式](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
示範如何攔截所有未處理的例外狀況。

## <a name="related-sections"></a>相關章節

[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)<br/>
描述標準 c + + 例外的狀況處理。

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)