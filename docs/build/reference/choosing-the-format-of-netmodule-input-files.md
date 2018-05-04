---
title: 選擇.netmodule 的格式輸入檔 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62575d3e816bdc10587e7a4c9cebcea735329ec1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>選擇 .netmodule 輸入檔的格式
為 MSIL 的.obj 檔案 (以編譯[/clr](../../build/reference/clr-common-language-runtime-compilation.md)) 也可用來當作.netmodule 檔。  .obj 檔案包含中繼資料和原生符號。  .netmodule 僅包含中繼資料。  
  
 您可以將的 MSIL 的.obj 檔案傳遞給其他 Visual Studio 編譯器中，透過 /addmodule 編譯器選項 （但請留意.obj 檔案會成為產生的組件的一部分，以及必須隨附於組件）。  例如，Visual C# 和 Visual Basic 有 /addmodule 編譯器選項。  
  
> [!NOTE]
>  在大部分情況下，您需要從建立 .net 模組的編譯中傳遞 .obj 檔給連結器。  傳遞 .dll 或 .netmodule MSIL 模組檔案給連結器可能會產生 LNK1107。  
  
 .obj 檔案加上其相關聯的 .h 檔案 (經由原始程式碼中的 #include 加以參考)，可以讓 C++ 應用程式使用模組中的原生類型，而在 .netmodule 檔中，只有 Managed 類型才能由 C++ 應用程式加以使用。  如果您嘗試傳遞.obj 檔案，以 #using，原生類型的資訊將無法使用。# 請改為 include.obj 檔案的.h 檔案。  
  
 其他 Visual Studio 編譯器只可以取用從模組的 managed 型別。  
  
 使用下列來決定您是否需要使用 .netmodule 或 .obj 檔做為 Visual C++ 連結器的模組輸入：  
  
-   如果您是使用 Visual C++ 以外的 Visual Studio 編譯器進行建置，請產生 .netmodule 並且使用 .netmodule 做為連結器的輸入。  
  
-   如果是使用 Visual C++ 編譯器產生模組，而且如果模組會用來建置程式庫以外的其他項目，請使用由編譯器產生的 .obj 檔案做為連結器的模組輸入，切勿使用 .netmodule 檔做為輸入。  
  
-   如果您的模組會用來建置 （未受管理） 的原生程式庫，.obj 檔做為模組輸入至連結器和產生的.lib 程式庫檔案。  
  
-   如果您的模組會用來建置 Managed 程式庫，而且如果連結器的所有模組輸入都能夠進行驗證 (以 /clr:safe 產生)，請使用 .obj 檔案做為連結器的模組輸入，然後產生 .dll (組件) 或 .netmodule (模組) 程式庫檔。  
  
-   如果您的模組會用來建置 managed 程式庫，而且會以 /clr 產生連結器的一或多個模組輸入，.obj 檔做為模組輸入至連結器，並產生.dll （組件）。  如果您想要公開 （expose） 從程式庫的 managed 型別，而且如果也想使用的原生型別程式庫中的 c + + 應用程式，您的程式庫所組成 （您也要出貨每個模組的.h 檔案的元件程式庫模組的.obj 檔案以便它們可以參考以 #include 從來源程式碼)。  
  
## <a name="see-also"></a>另請參閱  
 [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)