---
title: 如何：將原生 DLL 加入至全域組件快取
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: 1b11ebfae704ca1529113a00b463df728c85fe60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641359"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>如何：將原生 DLL 加入至全域組件快取

您可以將原生 DLL (而非 COM) 放入全域組件快取。

## <a name="example"></a>範例

**/ASSEMBLYLINKRESOURCE**可讓您的組件中嵌入原生 DLL。

如需詳細資訊，請參閱 [/ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)。

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>另請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)