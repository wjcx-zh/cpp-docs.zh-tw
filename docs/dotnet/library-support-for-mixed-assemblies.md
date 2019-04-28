---
title: 混合組件的程式庫支援
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: 42116c09d5b31cf669eb6d5d1e75eae60b2610a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312004"
---
# <a name="library-support-for-mixed-assemblies"></a>混合組件的程式庫支援

視覺化C++支援使用C++標準程式庫、 C 執行階段程式庫 (CRT)、 ATL 和 MFC 編譯的應用程式[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。 這可讓使用.NET Framework 功能，以及使用這些程式庫的現有應用程式。

> [!IMPORTANT]
> **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

這項支援包括下列 DLL 和匯入程式庫：

- 如果您使用編譯的 Msvcmrt [d].lib **/clr**。 此匯入程式庫混合組件連結。

這項支援可提供數個相關的優點：

- CRT 與C++標準程式庫可供混合程式碼。 CRT 與C++標準程式庫會提供不是可驗證;最後，您呼叫仍會路由至相同的 CRT 與C++為您的標準程式庫從原生程式碼中使用。

- 修正在混合的映像中的統一的例外狀況處理。

- 靜態初始設定的C++在混合的映像中的變數。

- Managed 程式碼中的每個 AppDomain 和處理序專屬變數的支援。

- 解析用於編譯 Visual Studio 2003 及更早版本的混合 Dll 載入器鎖定問題。

此外，這項支援存在下列限制：

- 只將 CRT DLL 的模型才支援以編譯程式碼 **/clr**。 有不支援的靜態 CRT 程式庫 **/clr**組建。

## <a name="see-also"></a>另請參閱

- [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
