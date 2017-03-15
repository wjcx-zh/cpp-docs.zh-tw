---
title: "選擇 .netmodule 輸入檔的格式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 選擇 .netmodule 輸入檔的格式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MSIL .obj 檔 \(使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 進行編譯\) 也可以.netmodule當成 .netmodule 使用。.obj 檔包含中繼資料和原生符號。.netmodule 僅包含中繼資料。  
  
 您可以經由 \/addmodule 編譯器選項，傳遞 MSIL .obj 檔給其他任何 Visual Studio 編譯器 \(但是請注意，.obj 檔會變成所產生組件的一部分，而且必須隨附於組件中\)。例如，Visual C\# 和 Visual Basic 都有 \/addmodule 編譯器選項。  
  
> [!NOTE]
>  在大部分情況下，您會需要從建立 .net 模組的編譯，傳遞 .obj 檔給連結器。其中一種情況例外是，如果 .netmodule 以[\/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)建立。傳遞 .dll 或 .netmodule MSIL 模組檔案給連結器可能會產生 LNK1107。  
  
 您可以在原始程式碼中透過 \#include 加以參考的 .obj 檔案，以及其相關聯的 .h 檔案，可以讓 C\+\+ 應用程式使用模組中的原生型別，而在 .netmodule 檔中，只有 Managed 型別才能由 C\+\+. C\+\+ 應用程式使用。如果您嘗試傳遞 .obj 檔給 \#using，就無法使用關於原生型別的資訊；請改用 \#include .obj 檔案的 .h 檔案。  
  
 其他 Visual Studio 編譯器僅能使用模組的 Managed 型別。  
  
 使用下列來決定您是否需要使用 .netmodule 或做為模組的 .obj 檔做為 Visual C\+\+ 連結器的模組輸入：  
  
-   如果您使用 Visual Studio 編譯器而不是Visual C\+\+ 來進行建置，請產生 .netmodule 並且使用 .netmodule 做為連結器的輸入。  
  
-   如果是使用 Visual C\+\+ 編譯器產生模組，而且如果模組會用來建置程式庫以外的其他項目，請使用由編譯器產生的 .obj 檔案做為連結器的模組輸入，切勿使用 .netmodule 檔作為輸入。  
  
-   如果您的模組將用來建置原生 \(非 Managed\) 程式庫，請使用 .obj 檔做為連結器的模組輸入，然後產生.lib 程式庫檔案。  
  
-   如果您的模組會用來建置 Managed 程式庫，而且如果連結器的所有模組輸入都能夠進行驗證 \(以 \/clr:safe 產生\)，請使用 .obj 檔案做為連結器的模組輸入，然後產生 .dll \(組件\) 或 .netmodule \(模組\)程式庫檔。  
  
-   如果您的模組將用來建置 Managed 程式庫，而且如果連結器的所有模組輸入都將會以 \/clr:pure 或 \/clr:safe 產生，如果您只想從程式庫公開 Managed 型別，請使用 .obj 檔做為連結器的模組輸入至連結器並產生 .dll \(組件\) 或 .netmodule \(模組\)。如果您要從程式庫公開 Managed 型別，而且如果您也要 C\+\+ 應用程式使用程式庫中的原生型別，您的程式庫將會由程式庫元件模組的 .obj 檔案組成 \(您也需要在每個模組中隨附 .h 檔案，讓它們可由原始程式碼利用 \#include 加以參考\)。  
  
-   如果您的模組將用來建置 Managed 程式庫，而且如果連結器的一個或多個模組輸入都將以 \/clr 產生，請使用 .obj 檔案做為連結器的模組輸入，然後產生 .dll \(組件\)。如果您要從程式庫公開 Managed 型別，而且如果您也要 C\+\+ 應用程式使用程式庫中的原生型別，您的程式庫將會由程式庫元件模組的 .obj 檔案組成 \(您也需要在每個模組中隨附 .h 檔案，讓它們可由原始程式碼利用 \#include 加以參考\)。  
  
## 請參閱  
 [.netmodule 檔做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)