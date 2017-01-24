---
title: "LINK 輸出 | Microsoft Docs"
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
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ilk 檔案"
  - "DLL [C++], 做為連結器輸出"
  - "可執行檔 [C++], 做為連結器輸出"
  - "檔案 [C++], LINK"
  - "ILK 檔案"
  - "匯入程式庫 [C++], 建立"
  - "LINK 工具 [C++], 對應檔"
  - "LINK 工具 [C++], 輸出"
  - "連結器 [C++], 輸出檔"
  - "對應檔 [C++]"
  - "對應檔 [C++], LINK 輸出"
  - "輸出檔 [C++], 連結器"
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LINK 輸出
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LINK 輸出包括 .exe 檔、DLL、對應檔和訊息。  
  
##  <a name="_core_output_files"></a> 輸出檔  
 LINK 的預設輸出檔為 .exe 檔。  如果指定了 [\/DLL](../../build/reference/dll-build-a-dll.md) 選項，LINK 將會建置 .dll 檔。  您可以使用[輸出檔名稱 \(\/OUT\)](../../build/reference/out-output-file-name.md) 選項以控制輸出檔的名稱。  
  
 在累加模式中，LINK 會建立一個 .ilk 檔以保存狀態資訊，供程式的後續累加組建使用。  如需有關 .ilk 檔的詳細資訊，請參閱 [.ilk 檔](../../build/reference/dot-ilk-files-as-linker-input.md)。  如需有關累加連結的詳細資訊，請參閱[以累加方式連結 \(\/INCREMENTAL\)](../../build/reference/incremental-link-incrementally.md) 選項。  
  
 當 LINK 在建立含有匯出 \(通常為 DLL\) 的程式時，除非組建中已經使用了一個 .exp 檔，否則它也會建置一個 .lib 檔。  您可以用 [\/IMPLIB](../../build/reference/implib-name-import-library.md) 選項以控制匯入程式庫檔名。  
  
 如果指定了[產生對應檔 \(\/MAP\)](../../build/reference/map-generate-mapfile.md) 選項，LINK 將會建立一個對應檔。  
  
 如果指定了[產生偵錯資訊 \(\/DEBUG\)](../../build/reference/debug-generate-debug-info.md) 選項，LINK 便會建立一個 PDB 以包含程式的偵錯資訊。  
  
##  <a name="_core_other_output"></a> 其他輸出  
 當您輸入 `link` 且不附帶任何其他命令列輸入時，LINK 會顯示一個摘要其選項的用法敘述。  
  
 而且除非使用了[隱藏程式啟始資訊 \(\/NOLOGO\)](../../build/reference/nologo-suppress-startup-banner-linker.md) 選項，否則 LINK 將會顯示著作權和版本訊息並且回應命令檔輸入。  
  
 您可以使用[列印進度訊息 \(\/VERBOSE\)](../../build/reference/verbose-print-progress-messages.md) 選項，顯示有關組建的其他詳細資料。  
  
 LINK 會以 LNK*nnnn* 的形式發出錯誤和警告訊息。  這種錯誤前置詞和數字範圍也使用於 LIB、DUMPBIN 和 EDITBIN 中。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)