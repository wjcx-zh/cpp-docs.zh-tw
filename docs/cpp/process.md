---
title: 處理序
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: f684c9c2ddfcb0aa166e1240c5f928ee52218f45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227201"
---
# `process`

指定您的 Managed 應用程式處理序應該使用特定全域變數的單一複本、靜態成員變數，或在處理序中的所有應用程式定義域中共用的靜態區域變數。 這主要是在使用進行編譯時使用 **`/clr:pure`** ，它在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。 使用進行編譯時 **`/clr`** ，全域和靜態變數預設為每個進程，且不需要使用 **`__declspec(process)`** 。

只有全域變數、靜態成員變數或原生類型的靜態區域變數可以用標記 **`__declspec(process)`** 。

**`process`** 只有在使用進行編譯時才有效 [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) 。

如果您想要讓每個應用程式域都有自己的全域變數複本，請使用[appdomain](../cpp/appdomain.md)。

如需詳細資訊，請參閱[應用程式域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md) 。

## <a name="see-also"></a>另請參閱

[`__declspec`](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
