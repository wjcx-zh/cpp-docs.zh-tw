---
title: 應用程式定義域和 Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
ms.openlocfilehash: 16c02bb58681ecb241d3552f57e0b05f2d6711b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208794"
---
# <a name="application-domains-and-visual-c"></a>應用程式定義域和 Visual C++

如果您有 `__clrcall` 虛擬函式，則 vtable 將會是每個應用程式域（appdomain）。 如果您在一個 appdomain 中建立物件，您只能從該 appdomain 內呼叫虛擬函式。 在混合模式（ **/clr**）中，如果您的類型沒有 `__clrcall` 的虛擬函式，您就會有每個進程的 vtable。 **/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

如需詳細資訊，請參閱

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>另請參閱

- [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
