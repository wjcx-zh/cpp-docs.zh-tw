---
title: "EDITBIN 選項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "editbin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EDITBIN 程式,  選項"
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# EDITBIN 選項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用 EDITBIN 來修改目的檔 \(Object File\)、可執行檔和動態連結程式庫 \(DLLs\)。  選項會指定 EDITBIN 所做的變更。  
  
 選項是由虛線 \( – \) 或斜線 \(\/\) 選項規範，後接選項名稱所組成。  選項名稱不可縮寫。  某些選項可接受於冒號 \( : \)之後指定的引數。  在選項規格內不可有空格或 Tab 字元。  請使用一個或多個空格或 Tab 字元來分隔命令列上的選項規格。  選項名稱及其關鍵字引數或檔名引數並沒有大小寫之分別。  例如， \-繫結和 \/BIND 表示同一件事。  
  
 EDITBIN 具有下列選項：  
  
|選項|用途|  
|--------|--------|  
|[\/ALLOWBIND](../../build/reference/allowbind.md)|指定 DLL 是否可以重新繫結 。|  
|[\/ALLOWISOLATION](../../build/reference/allowisolation.md)|指定 DLL 或可執行檔資訊清單查閱行為。|  
|[\/APPCONTAINER](../../build/reference/appcontainer.md)|指定應用程式是否必須在 AppContainer ——例如[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式——處理序環境中執行。|  
|[\/BIND](../../build/reference/bind.md)|設定進入點的位址在對速度載入時間之指定的物件。|  
|[\/DYNAMICBASE](../../build/reference/dynamicbase.md)|指定 DLL 或可執行檔映像是否可以使用位址空間配置隨機載入 \(ASLR\) 功能，於載入時隨機重定基底 \(Rebase\)。|  
|[\/ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|向 Microsoft 報告內部錯誤。|  
|[\/HEAP](../../build/reference/heap.md)|以位元組設定可執行檔映像的堆積的大小。|  
|[\/HIGHENTROPYVA](../../build/reference/highentropyva.md)|指定 DLL 或可執行檔映像是否支援高熵 64 位元位址空間配置隨機載入 \(ASLR\)。|  
|[\/INTEGRITYCHECK](../../build/reference/integritycheck.md)|指定是否在載入時間檢查數位簽章。|  
|[\/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|指定物件是否支援大於 2GB 的位址。|  
|[\/NOLOGO](../../build/reference/nologo-editbin.md)|隱藏程式 EDITBIN 啟始資訊。|  
|[\/NXCOMPAT](../../build/reference/nxcompat.md)|指定可執行檔映像是否與 Windows 資料執行防止功能相容。|  
|[\/REBASE](../../build/reference/rebase.md)|設定指定之物件的基底位址。|  
|[\/RELEASE](../../build/reference/release.md)|設定標頭中的總和檢查碼。|  
|[\/SECTION](../../build/reference/section-editbin.md)|覆寫某一區段的屬性。|  
|[\/STACK](../../build/reference/stack.md)|以位元組設定可執行檔映像的堆疊的大小。|  
|[\/SUBSYSTEM](../../build/reference/subsystem.md)|指定執行環境。|  
|[\/SWAPRUN](../../build/reference/swaprun.md)|指定必須將可執行檔映像複製到分頁檔，再從分頁檔執行。|  
|[\/TSAWARE](../../build/reference/tsaware.md)|指定應用程式在多使用者環境中執行。|  
|[\/VERSION](../../build/reference/version.md)|設定標題的版本號碼。|  
  
## 請參閱  
 [C\/C\+\+ 建置工具](../../build/reference/c-cpp-build-tools.md)   
 [EDITBIN 參考](../../build/reference/editbin-reference.md)