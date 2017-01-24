---
title: "LIB 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIB [C++], 模式"
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LIB 概觀
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LIB 會建立在建置 \(Build\) 程式時，可與 [LINK](../../build/reference/linker-options.md) 一起使用的標準程式庫、匯入程式庫和匯出檔案。  LIB 從命令提示字元執行。  
  
 您可以在下列模式中使用 LIB：  
  
-   [建置或修改 COFF 程式庫](../../build/reference/managing-a-library.md)  
  
-   [將成員物件抽取至檔案中](../../build/reference/extracting-a-library-member.md)  
  
-   [建立匯出檔案和匯入程式庫](../../build/reference/working-with-import-libraries-and-export-files.md)  
  
 這些模式是相互排斥的；您一次只能在一種模式中使用 LIB。  
  
## Lib 選項  
 下表列出 lib.exe 的選項和詳細資訊的連結。  
  
 **\/DEF**  
 建立匯入程式庫和匯出檔案。  
  
 如需詳細資訊，請參閱[建置匯入程式庫和匯出檔案](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **\/ERRORREPORT**  
 將有關使用 lib.exe 的內部錯誤資訊傳送給 Microsoft。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **\/EXPORT**  
 從程式匯出函式。  
  
 如需詳細資訊，請參閱[建置匯入程式庫和匯出檔案](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **\/EXTRACT**  
 建立包含現有程式庫成員複本的目的檔 \(.obj\)。  
  
 如需詳細資訊，請參閱[引出程式庫成員](../../build/reference/extracting-a-library-member.md)。  
  
 **\/INCLUDE**  
 將符號加入至符號表。  
  
 如需詳細資訊，請參閱[建置匯入程式庫和匯出檔案](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **\/LIBPATH**  
 覆寫環境程式庫路徑。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **\/LIST**  
 將有關輸出程式庫的資訊顯示於標準輸出。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **\/LTCG**  
 會使得程式庫在使用連結時產生程式碼下建置。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **\/MACHINE**  
 指定程式的目標平台。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **\/NAME**  
 當建置匯入程式庫時，指定正在建置之匯入程式庫的 DLL 名稱。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **\/NODEFAULTLIB**  
 從解析外部參考時所搜尋的程式庫清單，移除一個或多個預設程式庫。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **\/NOLOGO**  
 隱藏 LIB 著作權訊息和版本號碼的顯示，並防止命令檔的回應。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **\/OUT**  
 覆寫預設輸出檔案名稱。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **\/REMOVE**  
 省略輸出程式庫中的某個物件。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **\/SUBSYSTEM**  
 告訴作業系統如何執行藉由連結到輸出程式庫而建立的程式。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **\/VERBOSE**  
 顯示有關工作階段進度的詳細資訊，其中包括正在加入的 .obj 檔名稱。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **\/WX**  
 將警告視為錯誤。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
## 請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)   
 [LIB 輸入檔](../../build/reference/lib-input-files.md)   
 [LIB 輸出檔案](../../build/reference/lib-output-files.md)   
 [其他 LIB 輸出](../../build/reference/other-lib-output.md)   
 [程式庫結構](../../build/reference/structure-of-a-library.md)