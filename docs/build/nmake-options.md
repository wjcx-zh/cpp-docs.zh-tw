---
title: "NMAKE 選項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE 程式, 選項"
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# NMAKE 選項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表說明各種 NMAKE 選項，  每個選項前面會有斜線 \(\/\) 或破折號 \(–\)，而且選項不會區分大小寫。  使用 [\!CMDSWITCHES](../build/makefile-preprocessing-directives.md) 變更在 Makefile 或 Tools.ini 中的選項設定。  
  
|選項|用途|  
|--------|--------|  
|\/A|強制建置所有評估的目標，即使相對於相依性尚未過期。  不強制建置不相關的目標。|  
|\/B|即使時間戳記相等，仍會強制建置。  只建議極快速的系統使用 \(解析為兩秒或更短時間\)。|  
|\/C|隱藏預設輸出，包含 NMAKE 非嚴重錯誤或警告、時間戳記，和 NMAKE 著作權訊息。  隱藏由 \/K 所發出的警告。|  
|\/D|當目標不存在時，顯示每個評估的目標、相依性，和訊息的時間戳記。  進行 Makefile 偵錯時與 \/P 搭配使用，將會相當有用  使用 **\!CMDSWITCHES** 設定或清除部分 Makefile 的 \/D。|  
|\/E|導致環境變數覆寫 Makefile 巨集定義。|  
|\/ERRORREPORT\[NONE &#124; PROMPT &#124; QUEUE &#124; SEND \]|如果 nmake.exe 在執行階段失敗，您可以使用 \/ERRORREPORT 將這些內部錯誤的資訊傳送到 Microsoft。<br /><br /> 如需 \/ERRORREPORT 的詳細資訊，請參閱 [\/errorReport \(回報編譯器內部錯誤\)](../build/reference/errorreport-report-internal-compiler-errors.md)。|  
|\/F `filename`|將 `filename` 指定為 Makefile。  `filename` 之前可以有空格或定位字元。  為每一個 Makefile 指定一次 \/F。  若要從標準輸入提供 Makefile，請為 `filename` 指定破折號 \(–\)，並使用 F6 或 CTRL\+Z 結束鍵盤輸入。|  
|\/G|顯示包含 \!INCLUDE 指示詞的 Makefile。如需詳細資訊，請參閱 [Makefile 前置處理指示詞](../build/makefile-preprocessing-directives.md)。|  
|\/HELP、\/?|顯示 NMAKE 命令列語法的簡短摘要。|  
|\/I|忽略所有命令的結束代碼。  若要設定或清除部分 Makefile 的 \/I，請使用 **\!CMDSWITCHES**。  若要忽略部分 Makefile 的結束代碼，請使用破折號 \(–\) 命令修飾詞或 [.IGNORE](../build/dot-directives.md)。  若同時指定 \/K，則會覆寫 \/K。|  
|\/K|如果命令傳回錯誤，會繼續建置不相關的相依性。  同時會發出警告，並傳回結束代碼 1。  根據預設，如果任何命令傳回非零的結束代碼，NMAKE 將會暫止。  \/C 會隱藏 \/K 的警告；若同時指定 \/I，則 \/I 就會覆寫 \/K。|  
|\/N|顯示但不執行命令；執行前置處理命令。  不執行在 NMAKE 遞迴呼叫中的命令。  用在偵錯 Makefile 和檢查時間戳記是有用的。  若要設定或清除部分 Makefile 的 \/N，請使用 **\!CMDSWITCHES**。|  
|\/NOLOGO|隱藏 NMAKE 的著作權訊息。|  
|\/P|將資訊 \(巨集定義、推斷規則、目標、[.SUFFIXES](../build/dot-directives.md) 清單\) 顯示為標準輸出，然後執行建置。  如果 Makefile 或命令列目標都不存在，就會只顯示資訊。  與 \/D 搭配使用，以偵錯 Makefile。|  
|\/Q|檢查目標的時間戳記；不要執行建置。  如果所有目標都已更新，就會傳回零的結束代碼；如果有任何的目標未更新，便會傳回非零的結束代碼。  執行前置處理命令。  從批次檔中執行 NMAKE 時會很有用。|  
|\/R|清除 **.SUFFIXES** 清單，忽略在 Tools.ini 檔中定義或預先定義的推斷規則和巨集。|  
|\/S|隱藏顯示執行的命令。  若要隱藏顯示部分的 Makefile，請使用 **@** 命令修飾詞或 [.SILENT](../build/dot-directives.md)。  若要設定或清除部分 Makefile 的 \/S，請使用 **\!CMDSWITCHES**。|  
|\/T|更新命令列目標 \(或第一個 Makefile 目標\) 的時間戳記，並執行前置處理命令，但不執行建置。|  
|\/U|必須與 \/N 搭配使用。  傾印 NMAKE 內嵌檔，\/N 輸出才能用來當做批次檔。|  
|\/X `filename`|將 NMAKE 錯誤輸出傳送至 `filename`，而不是標準錯誤。  `filename` 之前可以有空格或定位字元。  若要將錯誤輸出傳送至標準輸出，請為 `filename` 指定破折號 \(–\)。  不會影響命令到標準錯誤的輸出。|  
|\/Y|停用批次模式推斷規則。  當選取這個選項以後，所有的批次模式推斷規則都會被視為標準推斷規則。|  
  
## 請參閱  
 [執行 NMAKE](../build/running-nmake.md)