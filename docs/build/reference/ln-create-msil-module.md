---
title: "/LN (建立 MSIL 模組) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/LN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LN 編譯器選項 [C++]"
  - "-LN 編譯器選項 [C++]"
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /LN (建立 MSIL 模組)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定組件資訊清單不應插入輸出檔中。  
  
## 語法  
  
```  
/LN  
```  
  
## 備註  
 **\/LN** 預設為不生效 \(組件資訊清單已插入輸出檔中\)。  
  
 使用 **\/LN** 時，也必須使用其中一個 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 選項。  
  
 資訊清單中沒有組件中繼資料的 Managed 程式稱為模組。  如果使用 [\/c \(編譯而不連結\)](../../build/reference/c-compile-without-linking.md) 和 **\/LN** 進行編譯，請在連結階段中指定 [\/NOASSEMBLY \(建立 MSIL 模組\)](../../build/reference/noassembly-create-a-msil-module.md)，以建立輸出檔。  
  
 如果您要採取以元件為基礎的作法建置組件，可能就要建立模組。也就是說，您可以撰寫型別，並將它們編譯入模組中。然後，您可以從一個或多個模組產生組件。如需從模組建立組件的詳細資訊，請參閱 [.netmodule 檔做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md) 或 [Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)。  
  
 模組的預設副檔名為 .netmodule。  
  
 在 Visual C\+\+ 2005 之前的 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 版本中，模組是以 **\/clr:noAssembly**建立的。  
  
 Visual C\+\+ 連結器接受 .netmodule 檔案做為輸入，而和連結器產生的輸出檔將是組件或 .netmodule 沒有輸入至連結器的執行階段依賴任何 .netmodules。如需詳細資訊，請參閱[.netmodule 檔做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
-   在連結器階段中指定 [\/NOASSEMBLY \(建立 MSIL 模組\)](../../build/reference/noassembly-create-a-msil-module.md)，以建立輸出檔。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   這個編譯器選項無法以程式設計方式進行變更。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)