---
title: 連結器工具錯誤 LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: ea675ca835dfc3fe4881e5fabbea746a4442b10a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498993"
---
# <a name="linker-tools-error-lnk1309"></a>連結器工具錯誤 LNK1309

> *type1*模組偵測到; 具有無效參數 /CLRIMAGETYPE:*type2*

## <a name="remarks"></a>備註

CLR 映像類型以要求 **/CLRIMAGETYPE**但連結器無法產生該類型的映像，因為一個或多個模組是與該類型不相容。

例如，您會看到 LNK1309 如果您指定**十分**，並傳遞模組，以建置 **/clr: pure**。

**/Clr: pure**並 **/clr: safe**編譯器選項以及支援程式庫在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

如果您嘗試建置部分信任的 CLR 純應用程式，並使用 ptrustu [d].lib，也會看到 LNK1309。 如需如何建立部分信任的應用程式的資訊，請參閱[如何： 建立在 CRT 程式庫 DLL 的部分信任的應用程式移除相依性所](../../dotnet/create-a-partially-trusted-application.md)。

如需詳細資訊，請參閱 < [/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)並[/CLRIMAGETYPE （指定 CLR 映像類型）](../../build/reference/clrimagetype-specify-type-of-clr-image.md)。