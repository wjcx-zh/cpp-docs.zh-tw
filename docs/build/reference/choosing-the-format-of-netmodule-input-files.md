---
title: 選擇 .netmodule 輸入檔的格式
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: b4d4b80e4b9195d184b9d97cea67bbaaa3d7d843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320567"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>選擇 .netmodule 輸入檔的格式

MSIL .obj 檔(使用[/clr](clr-common-language-runtime-compilation.md)編譯)也可以用作 .netmodule 檔。  .obj 檔包含中繼資料和本機符號。  .netmodule 僅包含中繼資料。

您可以通過 /addmodule 編譯器選項將 MSIL .obj 檔傳遞給任何其他 Visual Studio 編譯器(但請注意,.obj 檔將成為生成的程式集的一部分,並且必須隨程式集一起提供)。  例如,Visual C++ 和可視化基本具有 /addmodule 編譯器選項。

> [!NOTE]
> 在大部分情況下，您需要從建立 .net 模組的編譯中傳遞 .obj 檔給連結器。  傳遞 .dll 或 .netmodule MSIL 模組檔案給連結器可能會產生 LNK1107。

.obj 檔案加上其相關聯的 .h 檔案 (經由原始程式碼中的 #include 加以參考)，可以讓 C++ 應用程式使用模組中的原生類型，而在 .netmodule 檔中，只有 Managed 類型才能由 C++ 應用程式加以使用。  如果嘗試將 .obj 檔傳遞給#using,則有關本機類型的資訊將不可用;因此,將不可用。#include .obj 檔的 .h 檔。

其他 Visual Studio 編譯器只能使用模組中的託管類型。

使用以下內容確定是否需要使用 .netmodule 還是 .obj 檔案作為 MSVC 連結器的模組輸入:

- 如果您是使用 Visual C++ 以外的 Visual Studio 編譯器進行建置，請產生 .netmodule 並且使用 .netmodule 做為連結器的輸入。

- 如果使用 MSVC 編譯器生成模組,並且模組將用於建譯庫以外的內容,請使用編譯器生成的 .obj 檔案作為模組輸入連結器;不要使用 .netmodule 檔案作為輸入。

- 如果模組將用於建構本機(非託管)庫,請使用 .obj 檔案作為連結器的模組輸入並生成 .lib 庫檔案。

- 如果您的模組會用來建置 Managed 程式庫，而且如果連結器的所有模組輸入都能夠進行驗證 (以 /clr:safe 產生)，請使用 .obj 檔案做為連結器的模組輸入，然後產生 .dll (組件) 或 .netmodule (模組) 程式庫檔。

- 如果您的模組將用於建構託管庫,並且如果只需 /clr 即可生成一個或多個輸入連結器的模組,請使用 .obj 檔案作為連結器的模組輸入並生成 .dll(程式集)。  如果要從庫中公開託管類型,並且還希望C++應用程式在庫中使用本機類型,則庫將由庫元件模組的 .obj 檔組成(您還需要為每個模組提供 .h 檔,以便可以使用原始程式碼中#include引用這些檔)。

## <a name="see-also"></a>另請參閱

[.netmodule 檔作為連結器輸入](netmodule-files-as-linker-input.md)
