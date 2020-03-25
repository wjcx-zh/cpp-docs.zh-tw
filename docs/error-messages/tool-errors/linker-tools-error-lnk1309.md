---
title: 連結器工具錯誤 LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: 88b05512fd45adb6dc96a6c130ceccb74f3ab14e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194898"
---
# <a name="linker-tools-error-lnk1309"></a>連結器工具錯誤 LNK1309

> 偵測到*type1*模組;with switch/CLRIMAGETYPE 無效：*type2*

## <a name="remarks"></a>備註

已使用 **/CLRIMAGETYPE**要求 CLR 映射類型，但連結器無法產生該類型的影像，因為一或多個模組與該類型不相容。

例如，如果您指定 **/CLRIMAGETYPE： safe** ，而且您傳遞以 **/clr： pure**建立的模組，您將會看到 LNK1309。

**/Clr： pure**和 **/clr： safe**編譯器選項和支援程式庫在 Visual Studio 2015 中已被取代，Visual Studio 2017 中不支援。

如果您嘗試使用 ptrustu [d] .lib 建立部分信任的 CLR 純應用程式，您也會看到 LNK1309。 如需如何建立部分信任的應用程式的相關資訊，請參閱[如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式](../../dotnet/create-a-partially-trusted-application.md)。

如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)和[/CLRIMAGETYPE （指定 Clr 映射的類型）](../../build/reference/clrimagetype-specify-type-of-clr-image.md)。
