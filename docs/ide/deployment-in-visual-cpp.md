---
title: "Visual C++ 中的部署 | Microsoft Docs"
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
  - "應用程式部署 [C++]"
  - "部署應用程式 [C++]"
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 中的部署
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在另一台電腦上部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 應用程式時，您必須安裝該應用程式及該應用程式相依的所有程式庫檔案。  如果更新程式庫 \(例如更正安全性弱點後\)，您可以在部署該應用程式的位置套用更新。  
  
 Visual Studio 可透過三種方法在您部署應用程式時一併部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫：集中部署、本機部署或靜態連結。  Microsoft 會自動更新集中部署的程式庫。  若是屬於本機部署或靜態連結的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫，應用程式撰寫者必須提供更新。  
  
## 集中部署  
 集中部署會將 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫檔案安裝在 %windir% \\system32\\ 目錄中。  若要集中部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫，您可以使用下列其中一項：  
  
-   「*可轉散發套件檔*」\(Redistributable package files\)，這些是獨立的命令列可執行檔，您可用於安裝 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 可轉散發程式庫。  
  
-   「*可轉散發合併模組 \(.msm 檔案\)*」\(Redistributable merge modules\)，您可以用於部署特定程式庫及包含在應用程式 Windows Installer \(.msi\) 檔案中的程式庫。  
  
 可轉散發套件檔會安裝特定系統架構的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫。  在安裝應用程式之前，您可以設定應用程式，將其設定為執行的必要條件。  合併模組可以包含 Windows Installer 應用程式安裝檔中特定 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫的安裝邏輯。  您可以包含應用程式所需數量的合併模組。  
  
 若使用可轉散發套件集中部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫，Microsoft 會自動更新，因此建議您的應用程式使用動態連結和可轉散發套件。  
  
## 本機部署  
 本機部署會將程式庫檔案和可執行檔一同安裝在應用程式資料夾中。  因為每個版本的檔案名稱會加上其版本號碼以避免重複，因此可以將不同版本的程式庫安裝在相同資料夾中。  例如，第 12 版的 C 執行階段是 msvcr120.dll。  
  
 由於 Microsoft 無法自動更新本機部署的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫，本機部署這些程式庫時請特別注意。  如果您決定使用可轉散發程式庫的本機部署，建議您自行實作能夠自動更新本機部署程式庫的方法。  
  
## 靜態連結  
 您可以靜態連結 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫與應用程式，也就是說，您可以將程式庫編譯至應用程式，如此就不需要再個別部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫檔案。  不過，由於無法就地更新靜態連結的程式庫，因此採用這種方法時請特別小心。  如果您使用靜態連結而想要更新連結的程式庫，您必須重新編譯並重新部署應用程式。  
  
## 疑難排解  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫的載入順序與系統相關。  若要診斷載入器問題，請使用 depends.exe 或 where.exe。  如需詳細資訊，請參閱[動態連結程式庫搜尋順序 \(Windows\)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)。  
  
## 請參閱  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)