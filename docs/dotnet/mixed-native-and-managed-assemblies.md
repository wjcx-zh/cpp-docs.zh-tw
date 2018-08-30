---
title: 混合 （原生和 Managed） 組件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2a48f34edec8a9f24f22d35be482d3b297215dbe
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210621"
---
# <a name="mixed-native-and-managed-assemblies"></a>混合 （原生和 managed） 組件

混合的組件會包含未受管理的機器指令和 MSIL 指令。 這可讓他們能夠呼叫，並呼叫.NET 元件，同時保留未完全受管理的元件與相容性。 使用混合的組件，開發人員可以撰寫使用混合的 managed 和 unmanaged 功能的應用程式。 這可讓混合的組件適用於移轉現有的 Visual c + + 應用程式，以.NET 平台。

例如，現有的應用程式，其中包含完全 unmanaged 函式可以帶至.NET 平台編譯一個模組 **/clr**編譯器參數。 此模組就能夠使用.NET 功能，但保持相容應用程式的其餘步驟。 如此一來，應用程式被可轉換成漸進式、-循序漸進的方式在.NET 平台。 甚至可以在相同的檔案以函式的函式為基礎的 managed 和 unmanaged 編譯之間做決定 (請參閱[managed、 unmanaged](../preprocessor/managed-unmanaged.md))。

Visual c + + 只支援使用混合的 managed 組件產生 **/clr**編譯器選項。 **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。 如果您需要純或可驗證的 managed 組件時，我們建議使用 C# 建立它們。

舊版的 Visual c + + 編譯器工具組支援的 managed 組件的三種不同類型的產生： 混合的、 純粹的和可驗證。 後面兩個會討論[純粹的和可驗證程式碼 (C + + /cli CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)。

## <a name="in-this-section"></a>本節內容

[如何： 移轉至 /clr](../dotnet/how-to-migrate-to-clr.md)<br/>
描述引入或升級應用程式中的.NET 功能的建議的步驟。

[如何： 編譯 MFC 和 ATL 程式碼使用 /clr](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
討論如何編譯現有的 MFC 和 ATL 程式為目標的通用語言執行平台。

[混合組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
描述 「 載入器鎖定 」 問題和解決方案。

[混合組件的程式庫支援](../dotnet/library-support-for-mixed-assemblies.md)<br/>
討論如何使用中的原生程式庫 **/clr**編譯。

[效能考量](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
說明在混合的組件和資料封送處理效能的含意。

[應用程式定義域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
討論對應用程式定義域的 Visual c + + 支援。

[Double Thunking](../dotnet/double-thunking-cpp.md)<br/>
討論 managed 函式的原生進入點的效能含意。

[以 /clr 防止 CLR 關閉時取用 COM 物件建立的例外狀況](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
討論如何確保取用 COM 物件，使用編譯在受控應用程式的正常關機 **/clr**。

[如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式](../dotnet/create-a-partially-trusted-application.md)<br/>
討論如何建立使用 Visual c + + 移除相依性 msvcm90.dll 部分信任的通用語言執行平台應用程式。

如需有關混合組件的程式碼撰寫方針的詳細資訊，請參閱 MSDN 文章[概觀的 Managed 與 Unmanaged 程式碼互通性](https://msdn.microsoft.com/library/ms973872.aspx)。

## <a name="see-also"></a>另請參閱

- [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)
