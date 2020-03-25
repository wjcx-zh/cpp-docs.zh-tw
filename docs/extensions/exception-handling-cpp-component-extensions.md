---
title: 例外狀況處理 (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
ms.openlocfilehash: 9f5662bb9e744b5db3b0ab25ac4230b2f67016bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182119"
---
# <a name="exception-handling--ccli-and-ccx"></a>例外狀況處理 (C++/CLI 和 C++/CX)

使用 `/ZW` 編譯器選項或 `/clr` 編譯器選項編譯的應用程式都會使用「例外狀況」來處理程式執行期間發生的非預期錯誤。 下列主題將討論 C++/CX 或 C++/CLI 應用程式中的例外狀況處理。

## <a name="in-this-section"></a>本節內容

[使用 Managed 例外狀況的基本概念](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
描述如何擲回例外狀況和使用 **try**/**catch** 區塊。

[在 /clr 之下例外狀況處理行為的差異](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
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
描述標準 C++ 中的例外狀況處理。

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
