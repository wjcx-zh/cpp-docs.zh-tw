---
title: 混合 (原生和 Managed) 組件
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: 11bdfc98c64b2612129e10c002c68ee243bec7da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311884"
---
# <a name="mixed-native-and-managed-assemblies"></a>混合 (原生和受控) 組件

混合元件能夠同時包含未受管理的機器指令和 MSIL 指令。 這可讓它們呼叫並由 .NET 元件呼叫，同時保留與原生C++程式庫的相容性。 開發人員可以使用混合的元件，使用 .NET 和C++機器碼的混合來撰寫應用程式。

例如，透過使用 **/clr**編譯器參數只重新編譯C++一個模組，可將完全由機器碼組成的現有程式庫帶入 .net 平臺。 此模組接著可以使用 .NET 功能，但仍可與應用程式的其餘部分相容。 您甚至可以在同一個檔案內逐函式來決定 managed 和原生編譯之間的功能（請參閱[managed、非](../preprocessor/managed-unmanaged.md)受控）。

Visual C++僅支援使用 **/clr**編譯器選項產生混合的 managed 元件。 **/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。 如果您需要純粹或可驗證的 managed 元件，建議您使用C#來建立它們。

舊版的 Microsoft C++編譯器工具組支援三種不同類型的 managed 元件產生：混合、單純和可驗證。 後面兩個程式碼會在[純粹和可驗證C++的程式碼（/cli）](../dotnet/pure-and-verifiable-code-cpp-cli.md)中討論。

## <a name="in-this-section"></a>本節內容

[如何：遷移至/clr](../dotnet/how-to-migrate-to-clr.md)<br/>
說明在應用程式中引進或升級 .NET 功能的建議步驟。

[如何：使用/clr 編譯 MFC 和 ATL 程式碼](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
討論如何編譯現有的 MFC 和 ATL 程式，以將目標設為通用語言執行時間。

[混合組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
說明「載入器鎖定」的問題和解決方案。

[混合組件的程式庫支援](../dotnet/library-support-for-mixed-assemblies.md)<br/>
討論如何在 **/clr**編譯中使用原生程式庫。

[效能考量](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
說明混合元件和資料封送處理的效能影響。

[應用程式定義域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
討論應用C++程式域的視覺支援。

[雙重 Thunking](../dotnet/double-thunking-cpp.md)<br/>
討論 managed 函式的原生進入點的效能影響。

[避免在使用以/clr 建立的 COM 物件時，CLR 關閉的例外狀況](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
討論如何確保使用以 **/clr**編譯之 COM 物件的 managed 應用程式正常關機。

[如何：移除對 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式](../dotnet/create-a-partially-trusted-application.md)<br/>
討論如何藉由移除 msvcm90 的相依性，以使用視覺C++效果建立部分信任的 Common Language Runtime 應用程式。

如需混合元件之程式碼撰寫方針的詳細資訊，請參閱 MSDN 文章： [Managed/非受控碼互通性總覽](/previous-versions/dotnet/articles/ms973872(v=msdn.10))。

## <a name="see-also"></a>另請參閱

- [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)
