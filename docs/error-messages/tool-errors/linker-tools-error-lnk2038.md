---
title: "連結器工具錯誤 LNK2038 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2038"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2038"
ms.assetid: b8d0fb35-eee6-4f52-b3c4-239cb4f65656
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2038
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\<filename.obj\> 的相符偵測中 '\<name\>': value '\<value 1\>' 與 value '\<value 2\>' 不符  
  
 連結器偵測到符號不相符。  這個錯誤表示不同部分的應用程式包括程式庫或其他物件程式碼應用程式連結符號的用來衝突的定義。  [偵測到不相符](../../preprocessor/detect-mismatch.md) pragma 是用來定義此符號和偵測衝突的值。  
  
### 更正這個錯誤  
  
-   在專案的目的檔過期時，會發生這個錯誤。  在您嘗試其他解決這個錯誤之前，執行一個乾淨的組建以確保這是目前的物件檔案。  
  
-   Visual Studio 會定義下列符號以防止連接不相容的程式碼，可能會造成執行階段錯誤或其他未預期的行為。  
  
     `_MSC_VER`  
     表示用來建構應用程式或程式庫 Visual C\+\+ 編譯器的主要和次要版本號碼。  使用其中一個版本的Visual C\+\+編譯器去編譯的程式碼與具有不同版本編號的編譯器編譯出來的程式碼不相容。  如需詳細資訊，請參閱 [預先定義的巨集](../../preprocessor/predefined-macros.md)中的 `_MSC_VER`。  
  
     如果您連結到與所使用的Visual C\+\+編譯器版本不相容的文件庫，而且無法取得或建立相容的文件庫版本，您可以使用更簡單的編譯器版本去建立專案──只要變更專案的 \[**平台工具組**\] 屬性。  如需詳細資訊，請參閱[如何：修改目標 Framework 和平台工具組](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)。  
  
     `_ITERATOR_DEBUG_LEVEL`  
     表示在 C\+\+ 標準程式庫啟用的安全性層級和偵錯功能。  這些功能可以變更某些 C\+\+ 標準程式庫物件的表示並讓它們與使用其他安全性和偵錯功能的項目。  如需詳細資訊，請參閱[\_ITERATOR\_DEBUG\_LEVEL](../../standard-library/iterator-debug-level.md)。  
  
     `RuntimeLibrary`  
     表示應用程式或文件庫所使用的 C\+\+標準文件庫和 C 執行階段版本。  程式碼會使用 C\+\+ 標準程式庫或 C 執行階段版本與使用不同版本的程式碼不相容。  如需詳細資訊，請參閱[\/MD、\/MT、\/LD \(使用執行階段程式庫\)](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
     `_PPLTASKS_WITH_WINRT`  
     撰寫用來表示 [平行模式程式庫\(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 與物件連接編譯使用 [\/ZW](../../build/reference/zw-windows-runtime-compilation.md) 編譯器選項的其他設定。\(**\/ZW** 支援 C\+\+\/CX。\)使用或依賴 PPL的程式碼必須編譯使用應用程式的其他部分相同的 **\/ZW** 設定。  
  
     請確認這些符號的值在您的Visual Studio 方案的專案中一致，而且他們也與應用程式所連結的程式碼和文件庫一致。  
  
## 請參閱  
 [連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)