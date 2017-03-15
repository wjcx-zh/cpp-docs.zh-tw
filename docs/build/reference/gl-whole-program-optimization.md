---
title: "/GL (整個程式最佳化) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gl"
  - "VC.Project.VCCLWCECompilerTool.WholeProgramOptimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GL 編譯器選項 [C++]"
  - "GL 編譯器選項 [C++]"
  - "-GL 編譯器選項 [C++]"
  - "整個程式最佳化和 C++ 編譯器"
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /GL (整個程式最佳化)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟用整個程式最佳化。  
  
## 語法  
  
```  
/GL[-]  
```  
  
## 備註  
 整個程式最佳化可以讓編譯器以程式中所有模組的資訊執行最佳化。  如果不使用整個程式最佳化，最佳化將是以每一模組 \(編譯\) 的方式進行。  
  
 整個程式最佳化預設為關閉，且必須是明確啟用；  儘管如此，仍然可以用 **\/GL\-** 來明確地加以停用。  
  
 使用所有模組的資訊，編譯器可以：  
  
-   使暫存器的使用跨函式界限最佳化。  
  
-   對全域資料執行更好的追蹤修改，使得載入和存放區的數目能夠縮減。  
  
-   對以指標取值修改的可能項目集合進行更好的追蹤，以縮減載入和存放區的數目。  
  
-   將函式內嵌於模組，即使該函式是定義於另一個模組中。  
  
 利用 **\/GL** 產生的 .obj 檔案不能供 [EDITBIN](../../build/reference/editbin-reference.md) 和 [DUMPBIN](../../build/reference/dumpbin-reference.md) 這類連結器公用程式使用。  
  
 如果利用 **\/GL** 和 [\/c](../../build/reference/c-compile-without-linking.md) 編譯程式，應該要使用 \/LTCG 連結器選項建立輸出檔。  
  
 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 無法與 **\/GL** 一起使用  
  
 以目前版本的 **\/GL** 產生的檔案格式不一定能由後續版本的 Visual C\+\+ 讀取。  除非您願意針對使用者可能會使用的所有 Visual C\+\+ 版本 \(不論現在或將來\) 交運 .lib 檔案複本，否則不應該交運以 **\/GL** 所產生之 .obj 檔案構成的 .lib 檔案。  
  
 以 **\/GL** 和先行編譯標頭檔產生的 .obj 檔案不應用來建置 .lib 檔案，除非這個 .lib 檔案將在產生 **\/GL** 檔案的同一部電腦上進行連結。  在連結時將會需要來自 .obj 檔案的先行編譯標頭檔資訊。  
  
 如需可用的最佳化與整個程式最佳化之限制的詳細資訊，請參閱 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。 **\/GL** 也可以進行特性指引最佳化可用；請參閱 \/LTCG。為特性指引最佳化進行編譯時，如果要函式從特性指引最佳化排列順序，必須以 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 或隱含 \/Gy 的編譯器選項進行編譯。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  請參閱 [\/LTCG \(連結時間產生程式碼\)](../../build/reference/ltcg-link-time-code-generation.md)，取得如何在開發環境中指定 **\/GL** 的詳細資訊。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)