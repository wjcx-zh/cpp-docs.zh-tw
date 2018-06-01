---
title: 應用程式定義域和 Visual c + + |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b935b9a5d1561fa1c8b961ee48b92f59b98e2bd2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704330"
---
# <a name="application-domains-and-visual-c"></a>應用程式定義域和 Visual c + +

如果您有`__clrcall`虛擬函式，每個應用程式定義域 (appdomain)，將會在 vtable。 如果您在一個 appdomain 中建立物件，您只可以呼叫該 appdomain 內的虛擬函式。 在混合模式 (**/clr**) 如果您的型別沒有，您會有同處理序 vtable`__clrcall`虛擬函式。 **/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

如需詳細資訊，請參閱:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>另請參閱

- [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)