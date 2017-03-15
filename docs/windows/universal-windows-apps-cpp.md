---
title: "通用 Windows 應用程式 (C++) | Microsoft Docs"
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
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 通用 Windows 應用程式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通用 Windows 平台 \(UWP\) 應用程式具體表現一組強調以內容為主之簡單使用者介面的設計原則，該內容可針對不同裝置的不同螢幕大小自動調整。 您會在 XAML 標記中建立 UI，並在原生 C\+\+ 中建立程式碼後置。 您也可以建立元件 \(DLL\)，供其他語言所撰寫的 UWP 應用程式使用。 UWP 應用程式的應用程式開發介面是 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，這是構造良好的程式庫，可提供各種不同的作業系統服務。  
  
> [!NOTE]
>  許多有關使用 C\+\+ 開發 UWP 應用程式的文件都在 [Windows 開發人員中心](http://go.microsoft.com/fwlink/p/?LinkId=255563)網站上。 本文中的部分連結會前往該網站。  
  
## 使用 C\+\+\/CX 的 UWP 應用程式  
  
|||  
|-|-|  
|[Visual C\+\+ 語言參考 \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=255561)|描述一組擴充功能，其可簡化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 應用程式開發介面的 C\+\+ 使用，並可啟用根據例外狀況的錯誤處理。|  
|[建置應用程式和程式庫 \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=264858)|說明如何建立可以從 C\+\+\/CX 應用程式或元件存取的 DLL 和靜態程式庫。|  
|[教學課程：使用 C\+\+ 建立您的第一個 Windows 市集應用程式](http://go.microsoft.com/fwlink/p/?LinkId=255556)|介紹以 C\+\+ 開發 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式之基本概念的逐步解說 \(尚未更新有關在 Windows 10 上開發 UWP 的資訊\)。|  
|[使用 C\+\+ 建立 Windows 市集應用程式的藍圖](http://go.microsoft.com/fwlink/p/?LinkId=255553)|提供有關使用 C\+\+ 開發 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式和遊戲之文章的連結。|  
|[在 C\+\+ 中建立 Windows 執行階段元件](http://go.microsoft.com/fwlink/p/?LinkId=255559)|說明如何建立其他 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式和元件可以使用的 DLL。|  
|[開發遊戲](http://go.microsoft.com/fwlink/p/?LinkId=255554)|說明如何使用 DirectX 和 C\+\+ 來建立遊戲。|  
  
## 使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) 的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 提供低階 COM 介面，ISO C\+\+ 程式碼可藉以在沒有例外狀況的環境中存取 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。 在大多數情況下，建議您使用 C\+\+\/CX 而不是 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 來進行 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]應用程式開發。 如需 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 的詳細資訊，請參閱 [Windows Runtime C\+\+ Template Library \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
## 請參閱  
 [Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)