---
title: "Windows 市集應用程式、Windows 執行階段和 C 執行階段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Windows 市集應用程式、Windows 執行階段和 C 執行階段
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式為在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 中執行的程式 \(該程式在 [!INCLUDE[win8](../build/includes/win8_md.md)] 上執行\)。  [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 是可信賴的環境，控制可供 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式使用的函式、變數和資源。  不過，根據設計，[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 的限制不允許大部分 C 執行階段程式庫 \(CRT\) 的功能在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式中使用。  
  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 不支援下列 CRT 功能：  
  
-   與不支援的功能相關之大部分 CRT 函式。  
  
     例如，[!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式無法使用 `exec` 和 `spawn` 系列的常式建立處理序。  
  
     當 CRT 函式在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式中不受支援時，會記載該事實於其參考文件中。  
  
-   大部分的多位元組字元和字串的函式。  
  
     不過，Unicode 和 ANSI 文字皆受到支援。  
  
-   主控台應用程式和命令列引數。  
  
     不過，傳統桌面應用程式仍然支援主控台和命令列引數。  
  
-   環境變數。  
  
-   目前工作目錄的概念。  
  
-   使用 [\/MT](../build/reference/md-mt-ld-use-run-time-library.md) 或 `/MTd` 編譯器選項，與 CRT 靜態連結和建置的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式和 DLL。  
  
     也就是使用 CRT 的多執行緒、靜態版本的應用程式。  
  
-   使用 [\/MDd](../build/reference/md-mt-ld-use-run-time-library.md) 編譯器選項建置的應用程式。  
  
     也就是說，CRT 的偵錯、多執行緒和特定 DLL 的版本。  這類應用程式在 [!INCLUDE[win8_appstore_long](../build/reference/includes/win8_appstore_long_md.md)] 中不受支援。  
  
 如需在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式無法提供使用的 CRT 函式完整清單及替代函式的建議，請參閱 [\/ZW 不支援的 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 請參閱  
 [相容性](../c-runtime-library/compatibility.md)   
 [Windows 執行階段不支援的 CRT 函式](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)