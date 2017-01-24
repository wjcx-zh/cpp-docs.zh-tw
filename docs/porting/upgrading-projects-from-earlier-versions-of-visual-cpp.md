---
title: "從舊版的 Visual C++ 升級專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "32-bit code porting"
  - "upgrading Visual C++ applications, 32-bit code"
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
caps.latest.revision: 36
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從舊版的 Visual C++ 升級專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在大部分情況下，您都可以開啟在舊版 Visual Studio 中建立的專案。 不過，開啟時 Visual Studio 會將專案升級。 如果您儲存此升級的專案，在舊版本中便無法開啟。  
  
> [!IMPORTANT]
>  如果您嘗試轉換已轉換的專案，Visual Studio 會要求確認，因為重新轉換會刪除現有的檔案。  
  
 許多升級的專案與方案都可以不經過修改成功建置。 不過，有些專案可能需要變更設定或原始程式碼，或者兩者都變更。 建議您使用下列方針先解決設定問題，如果專案仍然無法建置，您就可以解決程式碼問題。  
  
1.  製作現有專案和方案檔案的複本。 如果您要比較檔案的版本，您可以並行安裝目前版本和舊版的 Visual Studio。  
  
2.  在目前版本的 Visual Studio 中開啟並且升級專案或方案複本，然後予以儲存。  
  
3.  針對每個轉換的專案，開啟捷徑功能表，然後選擇 \[屬性\]。 在 \[組態屬性\] 下，選取 \[一般\]，然後選取目前版本的 \[平台工具組\]。 \(例如，針對 Visual Studio 2013，選取 v120\)。  
  
4.  建置方案。 如果建置失敗，請修改設定並且重建。  
  
 資料來源是包含在不同的資料庫專案中，如此您就可以更輕鬆地修改和偵錯這些來源的預存程序。 如果您升級含有資料來源的 C\+\+ 專案，則會自動建立個別的資料庫專案。  
  
 如需如何更新目標 Windows 版本的相關資訊，請參閱 [修改 WINVER 和 \_WIN32\_WINNT](../porting/modifying-winver-and-win32-winnt.md)。  
  
## 請參閱  
 [建置系統變更](../build/build-system-changes.md)   
 [Visual C\+\+ 2015 的重大變更](../porting/visual-cpp-change-history-2003-20151.md)   
 [非標準行為](../cpp/nonstandard-behavior.md)