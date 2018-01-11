---
title: "混合的組件的程式庫支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b3bc50416eceac64c134a31a4d7384e33db69b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="library-support-for-mixed-assemblies"></a>混合組件的程式庫支援
Visual c + + 支援 c + + 標準程式庫，一般的執行階段程式庫 (CRT)，使用 ATL 和 MFC 應用程式，以編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。 這可讓使用.NET Framework 功能，以及使用這些程式庫的現有應用程式。  
  
 這項支援導入了下列新 DLL 和匯入程式庫：  
  
-   如果您以 /clr 編譯的 Msvcmrt [d].lib。 混合的組件連結至這個匯入程式庫。  
  
-   Msvcm90 [d].dll 和 Msvcurt [d].lib 如果編譯以 /clr: pure。 DLL 是混合的組件，提供受管理的 C 執行階段 (CRT) 支援，而且是 managed 組件安裝在全域組件快取 (GAC) 的一部分。 此匯入程式庫和最後會繫結至 Msvcm90.dll 純粹組件連結。  
  
 這項支援會提供數個相關的優點：  
  
-   CRT 和 c + + 標準程式庫會提供給混合或純程式碼。 提供 c + + 標準程式庫與 CRT 是無法驗證;最後，您呼叫仍然會路由傳送至相同的 CRT 和 c + + 標準程式庫為您從原生程式碼使用。  
  
-   更正純粹的和混合影像中的統一的例外狀況處理。  
  
-   純粹的和混合影像中的 c + + 變數的靜態初始設定。  
  
-   支援在 managed 程式碼的 Per-appdomain 和處理序專屬變數。  
  
-   解析套用至編譯的 Visual Studio 2003 及更早版本的混合 Dll 載入器鎖定問題。  
  
 此外，這項支援會提供下列限制：  
  
-   支援只 CRT DLL 模型 (同時以 /clr 或 /clr 編譯的程式碼： pure)。  
  
-   如果這些物件會使用 Visual c + + 程式庫 （因為所有的物件必須是純在純映像），您不能混用純粹的和混合的單一映像中的物件。 如果您這樣做，您會收到連結時間錯誤。  
  
 因為它不會保證使用較早版本，您應該更新 commn language runtime (CLR) 至目前版本。 這些變更內建的程式碼將不會執行 CLR 版本 1.x。  
  
## <a name="see-also"></a>請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)