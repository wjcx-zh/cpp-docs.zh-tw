---
title: 混合的組件的程式庫支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9fbb660d3f62c255ab81c7e77fef6c5d042efb12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="library-support-for-mixed-assemblies"></a>混合組件的程式庫支援
Visual c + + 支援 c + + 標準程式庫，一般的執行階段程式庫 (CRT)，使用 ATL 和 MFC 應用程式，以編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。 這可讓使用.NET Framework 功能，以及使用這些程式庫的現有應用程式。  
  
 這項支援導入了下列新 DLL 和匯入程式庫：  
  
-   如果您以 /clr 編譯的 Msvcmrt [d].lib。 混合的組件連結至這個匯入程式庫。  
  
 這項支援會提供數個相關的優點：  
  
-   CRT 和 c + + 標準程式庫會提供給混合或純程式碼。 提供 c + + 標準程式庫與 CRT 是無法驗證;最後，您呼叫仍然會路由傳送至相同的 CRT 和 c + + 標準程式庫為您從原生程式碼使用。  
  
-   更正純粹的和混合影像中的統一的例外狀況處理。  
  
-   純粹的和混合影像中的 c + + 變數的靜態初始設定。  
  
-   支援在 managed 程式碼的 Per-appdomain 和處理序專屬變數。  
  
-   解析套用至編譯的 Visual Studio 2003 及更早版本的混合 Dll 載入器鎖定問題。  
  
 此外，這項支援會提供下列限制：  
  
-   CRT DLL 模型支援以 /clr 編譯的程式碼。  
  
 因為它不會保證使用較早版本，您應該更新 commn language runtime (CLR) 至目前版本。 這些變更內建的程式碼將不會執行 CLR 版本 1.x。  
  
## <a name="see-also"></a>另請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)