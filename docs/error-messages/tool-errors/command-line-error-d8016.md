---
title: "命令列錯誤 D8016 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D8016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8016"
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令列錯誤 D8016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'option1' 和 'option2' 的命令列選項不相容  
  
 不能同時指定這些命令列選項。  
  
 請檢查環境變數，如 CL，取得選項規格。  
  
 **\/clr** 表示 **\/EHa**，而且您不能指定其他任何 **\/EH** 編譯器選項搭配 **\/clr**。  如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 更新 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 6.0 專案以後，您可能會接到 D8016：專案更新精靈處理可能會為專案中的每一套原始程式碼啟用 **\/RTC**，因而覆寫了該專案的 **\/RTC** 設定。若要解決這個問題，請將專案中每一套原始程式碼的 **\/RTC** 設定變更為預設設定，也就是說，**\/RTC**  的專案設定在每個檔案中都能生效。  
  
 如需變更 **\/RTC** 屬性設定的詳細資訊，請參閱 [\/RTC \(執行階段錯誤檢查\)](../../build/reference/rtc-run-time-error-checks.md)。