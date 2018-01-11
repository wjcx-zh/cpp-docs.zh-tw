---
title: "混合的、 純粹的和可驗證的功能比較 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- safe assemblies [C++], vs. pure
- mixed assemblies [C++], vs. pure
- safe assemblies [C++], vs. mixed
- pure MSIL [C++]
- verifiable assemblies [C++]
- pure MSIL [C++], vs. safe
- pure MSIL [C++], vs. mixed
- pure MSIL [C++], compared to mixed and safe
- verifiable assemblies [C++], vs. mixed
- mixed assemblies [C++], vs. safe
- verifiable assemblies [C++], vs. pure
- pure assemblies [C++]
- safe assemblies [C++]
- mixed assemblies [C++]
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3ee9fbed3fd82fd450fd179683fd119cb1630034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>混合的、純粹的和可驗證的功能比較 (C++/CLI)
本主題會比較不同的功能**/clr**編譯模式。 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
## <a name="feature-comparison"></a>功能比較  
  
|功能|混合 (/ clr)|純 (/ /clr: pure)|安全 (/: safe)|相關的資訊|  
|-------------|---------------------|-------------------------|-------------------------|-------------------------|  
|CRT 程式庫|支援|支援||[依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC/ATL|支援|||[MFC 桌面應用程式](../mfc/mfc-desktop-applications.md)&#124;[類別概觀](../atl/atl-class-overview.md)|  
|Unmanaged 函式|支援|||[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)|  
|未受管理的資料|支援|支援||[純粹的和可驗證的程式碼 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|可從 Unmanaged 函式呼叫|支援|||[如何： 移轉至 /clr: pure (C + + /CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)|  
|呼叫 unmanaged 函式的支援|支援|只有 C 樣式函式|P/Invoke 只能|[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|支援的反映|只有 Dll|支援|支援|[反映 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|  
  
## <a name="see-also"></a>請參閱  
 [純粹的和可驗證的程式碼 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)