---
title: 若是混合組件的程式庫支援 |Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
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
ms.openlocfilehash: 8c3fec26f3e41c3edd2346ac2e1b9b1f6b98ba33
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069616"
---
# <a name="library-support-for-mixed-assemblies"></a>混合組件的程式庫支援

Visual c + + 支援 c + + 標準程式庫、 C 執行階段程式庫 (CRT)，使用 ATL 和 MFC 編譯的應用程式[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。 這可讓使用.NET Framework 功能，以及使用這些程式庫的現有應用程式。

> [!IMPORTANT]
> **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

這項支援包括下列 DLL 和匯入程式庫：

- 如果您使用編譯的 Msvcmrt [d].lib **/clr**。 此匯入程式庫混合組件連結。

這項支援可提供數個相關的優點：

- CRT 與 c + + 標準程式庫有混合的程式碼。 提供 c + + 標準程式庫與 CRT 是無法驗證;最後，您呼叫仍然會路由傳送到相同的 CRT 與 c + + 標準程式庫，您會使用原生程式碼。

- 修正在混合的映像中的統一的例外狀況處理。

- 混合的映像中的 c + + 變數的靜態初始設定。

- Managed 程式碼中的每個 AppDomain 和處理序專屬變數的支援。

- 解析用於編譯 Visual Studio 2003 及更早版本的混合 Dll 載入器鎖定問題。

此外，這項支援存在下列限制：

- 只將 CRT DLL 的模型才支援以編譯程式碼 **/clr**。 有不支援的靜態 CRT 程式庫 **/clr**組建。

## <a name="see-also"></a>另請參閱

- [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
