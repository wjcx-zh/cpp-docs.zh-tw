---
title: 選擇 .netmodule 輸入檔的格式
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: d48bfe84210143db333d1e6b081acf1aa66980cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294573"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>選擇 .netmodule 輸入檔的格式

MSIL.obj 檔案 (以編譯[/clr](clr-common-language-runtime-compilation.md)) 也可用來當做.netmodule 檔。  .obj 檔案包含中繼資料和原生的符號。  .netmodule 僅包含中繼資料。

您可以將任何其他 Visual Studio 編譯器中的 MSIL.obj 檔案，透過 /addmodule 編譯器選項 （但請注意.obj 檔案會成為產生的組件的一部分，且必須隨附於組件）。  例如，Visual C# 和 Visual Basic 有 /addmodule 編譯器選項。

> [!NOTE]
>  在大部分情況下，您需要從建立 .net 模組的編譯中傳遞 .obj 檔給連結器。  傳遞 .dll 或 .netmodule MSIL 模組檔案給連結器可能會產生 LNK1107。

.obj 檔案加上其相關聯的 .h 檔案 (經由原始程式碼中的 #include 加以參考)，可以讓 C++ 應用程式使用模組中的原生類型，而在 .netmodule 檔中，只有 Managed 類型才能由 C++ 應用程式加以使用。  如果您嘗試傳遞.obj 檔案，以 #using，原生類型的相關資訊將無法使用;#include.obj 檔案的.h 檔案改為。

其他 Visual Studio 編譯器只能取用 managed 的類型，從模組。

若要判斷是否需要使用.netmodule 或.obj 檔做為模組輸入 MSVC 連結器使用下列：

- 如果您是使用 Visual C++ 以外的 Visual Studio 編譯器進行建置，請產生 .netmodule 並且使用 .netmodule 做為連結器的輸入。

- 如果您使用 MSVC 編譯器來產生模組，而且如果模組會用來建置以外的程式庫中，使用由編譯器產生做為連結器的模組輸入的.obj 檔案請勿使用.netmodule 檔做為輸入。

- 如果您的模組會用來建置 （未受管理） 的原生程式庫中，使用做為連結器的模組輸入的.obj 檔案，並產生.lib 程式庫檔案。

- 如果您的模組會用來建置 Managed 程式庫，而且如果連結器的所有模組輸入都能夠進行驗證 (以 /clr:safe 產生)，請使用 .obj 檔案做為連結器的模組輸入，然後產生 .dll (組件) 或 .netmodule (模組) 程式庫檔。

- 如果您的模組會用來建置 managed 程式庫，且會以 /clr 產生連結器的一或多個模組輸入，.obj 檔作為連結器的模組輸入，然後產生.dll （組件）。  如果您想要公開 managed 的類型，從程式庫，而您也想C++（您也要提供每個外掛模組的.h 檔案的程式庫元件模組的.obj 檔案將會包含應用程式使用的文件庫中，而您的程式庫中的原生類型ule，以便它們可以參考使用 #include： 從原始碼)。

## <a name="see-also"></a>另請參閱

[.netmodule 檔作為連結器輸入](netmodule-files-as-linker-input.md)
