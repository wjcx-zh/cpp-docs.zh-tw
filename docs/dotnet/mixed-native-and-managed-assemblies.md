---
title: 混合 （原生和 Managed） 組件 |Microsoft 文件
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
ms.openlocfilehash: 0ac18841d5050bc8fb849ac542dc298ce89c964f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mixed-native-and-managed-assemblies"></a>混合 (原生和 Managed) 組件
混合的組件也能包含未受管理的機器指示和 MSIL 指令。 這可讓他們可以呼叫和被呼叫.NET 元件，同時保留未完全受管理的元件的相容性。 使用混合的組件，開發人員可以撰寫使用混合的 managed 和 unmanaged 功能的應用程式。 這可讓混合的組件適用於現有 Visual c + + 應用程式移轉至.NET 平台。  
  
 例如，現有的應用程式完全組成 unmanaged 函式可以帶至.NET 平台編譯一個模組 **/clr**編譯器參數。 此模組就能夠使用.NET 功能，但仍相容的應用程式的其餘部分。 如此一來，應用程式可以轉換成.NET 平台，以漸進式片段的片段的方式。 甚至可以決定要在相同的檔案以函式的函式為基礎的 managed 和 unmanaged 編譯 (請參閱[managed、 unmanaged](../preprocessor/managed-unmanaged.md))。  
  
 Visual c + + 支援三種不同類型的 managed 組件產生： 混合的、 純粹的和可驗證。 後面兩個中會討論[純粹的和可驗證程式碼 (C + + /CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [如何： 移轉至 /clr](../dotnet/how-to-migrate-to-clr.md)  
 描述引入或升級您的應用程式中的.NET 功能的建議的步驟。  
  
 [如何： /clr 編譯 MFC 和 ATL 程式碼使用](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)  
 討論如何編譯 MFC 和 ATL 程式現有 Common Language Runtime 為目標。  
  
 [混合組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)  
 描述 「 載入器鎖定 」 問題和解決方案。  
  
 [混合組件的程式庫支援](../dotnet/library-support-for-mixed-assemblies.md)  
 討論如何使用原生程式庫中的 **/clr**編譯。  
  
 [效能考量](../dotnet/performance-considerations-for-interop-cpp.md)  
 描述混合的組件和資料封送處理的效能含意。  
  
 [應用程式定義域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)  
 討論 Visual c + + 支援的應用程式定義域。  
  
 [Double Thunking](../dotnet/double-thunking-cpp.md)  
 討論 managed 函式的原生進入點的效能含意。  
  
 [以 /clr 避免 CLR 關機時耗用建置的 COM 物件上的例外狀況](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)  
 討論如何確保適當關機之下，使用 COM 物件，以編譯的受管理應用程式的 **/clr**。  
  
 [如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式](../dotnet/create-a-partially-trusted-application.md)  
 討論如何建立使用 Visual c + + 所移除的相依性 msvcm90.dll 部分信任的 Common Language Runtime 應用程式。  
  
 若是混合組件程式碼撰寫方針的詳細資訊，請參閱 MSDN 文件 」 概觀的未受管理/受管理程式碼交互操作性 」，在[ http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp ](http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp)。  
  
## <a name="see-also"></a>另請參閱  
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)