---
title: "轉散發控制項 | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 轉散發"
  - "可轉散發控制項"
ms.assetid: 32d03b95-d328-4f10-ad9b-f3ebbe03339d
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 轉散發控制項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ .NET 提供您可以在應用程式中使用的 ActiveX 控制項。 然後您可以連同應用程式一起轉散發控制項。 在 \[插入 ActiveX 控制項\] 對話方塊中，反白顯示一個控制項將會顯示其 .ocx 或 .dll 檔案。  
  
 如需可轉散發 Visual C\+\+ 所提供之 ActiveX 控制項的清單，請參閱 Visual C\+\+ .NET 產品光碟第二片光碟上的 Program Files\\Microsoft Visual Studio .NET 2003\\redist.txt；Win\\System 資料夾中的任何 .ocx 檔案都是可轉散發檔案。  
  
 [MFC ActiveX 控制項：散發 ActiveX 控制項](../../mfc/mfc-activex-controls-distributing-activex-controls.md)說明如何安裝及登錄可轉散發 ActiveX 控制項。  
  
 [合併模組專案](http://msdn.microsoft.com/zh-tw/e92e4f85-fba5-45ee-a432-892a956daeb9)說明 Visual Studio .NET 部署如何透過合併模組來處理檔案的轉散發。  
  
 [轉散發資料庫支援檔案](../../ide/redistributing-database-support-files.md)討論如何轉散發 Microsoft Data Access SDK 中的資料庫技術支援檔案。  
  
 如果您的應用程式使用連接到資料庫的 ActiveX 控制項，則需要安裝或執行下列作業：  
  
-   **適用於 Windows 的 DCOM。**您需要在執行 Windows 2000 之前的 Windows 版本的任何電腦上，執行 Dcom98.exe 或 Dcom95.exe \(Dcom98.exe 適用於 Windows 98；Dcom95.exe 適用於 Windows 95\)。  
  
-   **MDAC 2.8 SDK。**您應該在目標電腦上安裝 Microsoft Data Access 2.8 SDK。 您可以從 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=205525](http://go.microsoft.com/fwlink/?LinkId=205525) 下載這個 SDK。  
  
-   **MDAC 2.8 轉散發程式。**MDAC 2.8 SDK 設計為搭配 MDAC 2.8 轉散發程式 \(MDAC\_TYP.EXE\) 使用。 您可以從 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164412](http://go.microsoft.com/fwlink/?LinkId=164412) 下載 MDAC\_TYP.EXE。  
  
-   **複寫 DSN。**您也需要複寫目標電腦上的資料來源名稱。 您可以透過 [ConfigDSN](https://msdn.microsoft.com/en-us/library/ms709275.aspx) 等函式，利用程式設計方式來執行這項作業。  
  
## 元件轉散發的重要注意事項  
  
-   **轉散發 DAO 元件。** Microsoft 建議您使用 Jet 4.0 SP3 \(2927.04 版\) 或更新版本。 Jet 4.0 SP3 隨附於 Windows 2000 和 Windows Me。 使用這個版本的 Jet 可減少您的應用程式必須測試的 Jet 版本數目。  
  
     Windows XP 隨附舊版 Windows 中未包含的已升級 Service Pack 版 Jet。 在 Windows XP 上測試您的應用程式時，會自動測試 Windows XP 隨附的 Jet 版本。 您必須先在 Jet 4.0 的兩種版本上測試 DAO 應用程式，再加以發行。  
  
     Windows XP 版本的唯一不同之處，在於已修正自 Windows 2000 發行以來所發現的問題。 如果您應用程式的使用者未遇到問題，則不需要升級為 Jet 4.0 SP3 以後的版本。  
  
-   **已知的 ActiveX 控制項問題。** 在尚未安裝 Visual C\+\+ 的電腦上動態建立可轉散發 ActiveX 控制項執行個體時，已知會發生一個問題，如知識庫文章＜PRB：可轉散發控制項的動態建立失敗＞\(Q151804\) 中所述。 您可以在 MSDN Library 光碟或是在 [http:\/\/support.microsoft.com](http://support.microsoft.com) 找到知識庫文章。 此外，將某些 ActiveX 控制項放在對話方塊時，已知也會發生一個問題，那就是出現訊息方塊，指出控制項需要設計階段授權，如知識庫文章＜PRB：Microsoft ActiveX 控制項需要設計階段授權＞\(Q155059\) 中所述。 您可以在 MSDN Library 光碟或是在 [http:\/\/support.microsoft.com](http://support.microsoft.com) 找到知識庫文章。  
  
-   **Visual Studio 授權控制項。** Visual Studio 授權可以轉散發給其他 Visual Studio 開發工具特有的其他 ActiveX 控制項。 例如，圖表控制項可以與同時隨附於 Visual Studio 的 Visual Basic 一起散發。 因此，如果您使用 Visual C\+\+ 做為 Visual Studio 授權的一部分，您可以轉散發圖表控制項。 不過，如果您只購買 Visual C\+\+，則沒有可轉散發的授權。  
  
## 請參閱  
 [使用 ActiveX 控制項](../../data/ado-rdo/using-activex-controls.md)   
 [MFC ActiveX 控制項：散發 ActiveX 控制項](../../mfc/mfc-activex-controls-distributing-activex-controls.md)