---
title: "使用合併模組來轉散發元件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "合併模組, 使用"
  - "可轉散發應用程式, 使用合併模組"
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用合併模組來轉散發元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 包含授權用於與應用程式轉散發的各個 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 元件之 [合併模組](http://msdn.microsoft.com/library/aa367434)。  在 Windows Installer 安裝程式檔案中編譯合併模組時，會將特定 DLL 部署至具有特定平台的電腦。  在您的安裝程式檔中，指定應用程式必要條件的合併模組。  安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 後，合併模組會安裝於 \\Program Files\\Common Files\\Merge Modules\\ \(只可轉散發非偵錯版本的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLL\)。如需關於授權用於轉散發的合併模組清單的連結和詳細資訊，請參閱[轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
 您可以使用合併模組將可轉散發 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLL 安裝至 %SYSTEMROOT%\\system32\\ 資料夾 \([!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 本身即使用這項技術\)。不過，除非安裝的使用者具有系統管理員權限，否則安裝至此資料夾會失敗。  
  
 除非您不需要維護您的應用程式，而且未對於多個 DLL 版本具有相依性，否則建議您不要使用合併模組。  一個安裝程式中不可含有相同 DLL 的不同版本合併模組，而且合併模組會使得在應用程式之外獨立維護 DLL 變得困難。  相反地，我們建議您安裝 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 可轉散發套件。  
  
## 請參閱  
 [轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)