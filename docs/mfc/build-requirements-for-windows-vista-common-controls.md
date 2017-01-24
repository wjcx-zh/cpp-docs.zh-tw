---
title: "Windows Vista 通用控制項的組建需求 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通用控制項 (MFC)"
  - "通用控制項 (MFC), 組建需求"
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Vista 通用控制項的組建需求
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Foundation Class \(MFC\) 程式庫支援 Windows 通用控制項 6.1 版。  通用控制項在 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 中，而且程式庫在 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]中。  程式庫提供增強現有類別的新的方法和支援 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 通用控制項的新類別和方法。  當您建置應用程式時，您應該遵循下列章節中描述的編輯和移轉要求。  
  
## 編譯需求  
  
### 支援版本  
 雖然其他方法支援舊版的作業系統，一些新的類別和方法只支援 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] \(含\) 以後版本。  在每個方法主題的 `Requirements` 區段的附註指定最小作業系統何時是 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]。  
  
 即使您的電腦上執行 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]，您可以在 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 上執行的 MFC 應用程式，如果您的電腦上的 6.1 版 MFC 標頭檔。  不過，對於  [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]特別設計的通用控制項在該系統只能使用和在舊版作業系統之前忽略。  
  
### 支援的字元集。  
 新的 Windows 通用控制項僅支援 Unicode 字元集而非 ANSI 字元集。  如果您已在命令列應用程式，請使用下列兩個定義 \(\/D\) 編譯器選項指定 Unicode 做為基底字元集:  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 如果您在 Visual Studio 整合式開發環境 \(IDE\) \(IDE\) 建置應用程式，請指定 \[**字元集**\] 屬性的 \[**Unicode 字元集**\] 索引標籤在專案屬性的 \[**概觀**\] 節點。  
  
 數個 MFC 方法 ANSI 版本是已被取代的開始 Windows 通用控制項 6.1 版。  如需詳細資訊，請參閱[已被取代的 ANSI 應用程式開發介面](../mfc/deprecated-ansi-apis.md)。  
  
## 遷移需求  
 如果您使用 Visual Studio IDE 建立使用 Windows 通用控制項 6.1 版的新 MFC 應用程式， IDE 會自動宣告適當的資訊清單。  不過，因此，如果您將舊版 Visual Studio 的現有的 MFC 應用程式，而且想要使用新的通用控制項， IDE 不會自動提供資訊清單資訊升級您的應用程式。  相反地，您在 stdafx.h 檔案必須手動插入下列程式碼:  
  
```  
#ifdef UNICODE  
#if defined _M_IX86  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_IA64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_X64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#else  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#endif  
#endif  
```  
  
## 請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [階層架構圖表](../mfc/hierarchy-chart.md)   
 [已被取代的 ANSI 應用程式開發介面](../mfc/deprecated-ansi-apis.md)