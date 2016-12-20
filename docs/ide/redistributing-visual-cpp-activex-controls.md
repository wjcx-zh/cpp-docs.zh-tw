---
title: "轉散發 Visual C++ ActiveX 控制項 | Microsoft Docs"
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
  - "控制項 [C++], 散發"
  - "控制項 [C++], 轉散發"
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 轉散發 Visual C++ ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 6.0 提供了可用於應用程式的 ActiveX 控制項，您可將這些應用程式再轉散發。  Visual C\+\+ 不再包含這些控制項。  根據 Visual C\+\+ 6.0 的授權合約，您可以將這些控制項與使用 Visual C\+\+ 開發的應用程式一起轉散發。  
  
> [!NOTE]
>  Microsoft 不再支援 Visual C\+\+ 6.0。  
  
 如需可轉散發的 Visual C\+\+ 6.0 ActiveX 控制項的清單，請參閱 Visual C\+\+ 6.0 產品光碟片的光碟片 1 上的 Common\\Redist\\Redist.txt。  
  
 在散發應用程式時，您必須為 ActiveX 控制項安裝及登錄 .ocx \(使用 Regsvr32.exe\)。  此外，您應確定目標電腦具有下列系統檔案的現行版本 \(星號表示該檔案必須註冊\)：  
  
-   Asycfilt.dll  
  
-   Comcat.dll \*  
  
-   Oleaut32.dll \*  
  
-   Olepro32.dll \*  
  
-   Stdole2.tlb  
  
 如果目標系統上未提供這些 DLL，您需要使用規定的機制來讓它們更新，才能更新對應的作業系統。  您可以從 [http:\/\/windowsupdate.microsoft.com](http://windowsupdate.microsoft.com) 下載 Windows 作業系統最新的 Service Pack。  
  
 如果應用程式使用連接到資料庫的其中一個 ActiveX 控制項，您必須將 Microsoft Data Access Components \(MDAC\) 安裝到目標系統上。  如需詳細資訊，請參閱[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)。  
  
 使用連接到資料庫的 ActiveX 控制項時，您還必須在目標電腦上複製資料來源。  您可以程式化地使用如 `ConfigDSN` 函式來執行這項動作。  
  
 某些可轉散發的 ActiveX 控制項具有其他的相依性。  Visual C\+\+ 6.0 產品光碟片上的 Os\\System 資料夾內的每一個 .ocx 檔，都有一個並存的 .dep 檔。  針對您想轉散發的每一個 .ocx 檔，查閱對應的 .dep 檔中的是否有一個或多個 USES 項目。  如果有列出檔案，您必須確定該檔案是在目標電腦上。  任何 DLL 都直接支援需要註冊的 .ocx 檔   \(若要讓 Regsvr32.exe 成功，目標電腦必須先包含控制項靜態載入的所有 DLL\)。此外，如果列為相依性的 DLL 在 Os\\System 資料夾和 Visual C\+\+ 6.0 CD 上也有 .dep 檔，您也必須為 USES 項目調查該 .dep 檔。  
  
## 請參閱  
 [轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)