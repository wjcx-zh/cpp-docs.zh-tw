---
title: "為 Windows XP 設定 C++ 11 程式 | Microsoft Docs"
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
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
caps.latest.revision: 14
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 為 Windows XP 設定 C++ 11 程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由於 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 支援多個平台工具組，因此您可以將預設工具組不支援的作業系統和執行階段程式庫設為目標。  例如，您可以使用 C\+\+11 語言增強功能、編譯器、程式庫和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中實作的其他功能，來建立以 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 為目標的應用程式。  您可以使用舊版平台工具組來保留與二進位檔相容的舊版程式碼，同時仍然利用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 的最新功能。  
  
> [!NOTE]
>  您必須安裝 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] Update 4，才能將 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的平台工具組支援加入 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)]。  若要下載及安裝 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] Update 4 複本，請參閱 Microsoft 下載中心的 [Microsoft Visual Studio Express 2012 for Windows Desktop](http://go.microsoft.com/fwlink/?LinkID=265464)。  然後安裝 [Visual Studio 2012 Update 4](http://go.microsoft.com/fwlink/?LinkID=335900) 以取得 v110\_xp 平台工具組。  安裝後，即可使用 Windows Update 來接收最新的軟體更新。  
  
## 以 Windows XP 為目標的體驗  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 隨附的 Windows XP 平台工具組是 [!INCLUDE[win7](../build/includes/win7_md.md)] 隨附的 [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)] SDK 版本，但使用目前的 C\+\+ 編譯器。  它也會將專案屬性設定為適當的預設值，例如設定下層目標的相容連結器規格。  只有使用 Windows XP 平台工具組建立的 Windows 桌面應用程式可在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上執行，但這些應用程式也可在較新的作業系統上執行，例如 Windows Vista、[!INCLUDE[win7](../build/includes/win7_md.md)]、[!INCLUDE[winsvr08](../build/includes/winsvr08_md.md)]、[!INCLUDE[win8](../build/includes/win8_md.md)] 或 [!INCLUDE[winserver8](../build/includes/winserver8_md.md)]。  
  
#### 以 Windows XP 為目標  
  
1.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在專案 \[屬性頁\] 對話方塊之 \[組態屬性\] 下的 \[一般\] 中，將 \[平台工具組\] 屬性設為所需的 Windows XP 工具組。  例如，選擇 \[Visual Studio 2012 \- Windows XP \(v110\_xp\)\] 建立程式碼，該程式碼是與 Microsoft Visual C\+\+ 2012 可轉散發程式庫相容的二進位檔。  
  
### C\+\+ 執行階段支援  
 除了 Windows XP 平台工具組之外，C Runtime Library \(CRT\)、Standard Template Library \(STL\)、Active Template Library \(ATL\)、Concurrency Runtime Library \(ConCRT\)、Parallel Patterns Library \(PPL\)、Microsoft Foundation Class \(MFC\) 程式庫和 C\+\+ AMP \(C\+\+ Accelerated Massive Programming\) 程式庫還包含對 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的執行階段支援。  這些作業系統的支援版本包括適用於 x86 的 [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 \(SP3\)、適用於 x64 的 [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 \(SP2\)，以及適用於 x86 和 x64 的 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 \(SP2\)。  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 所安裝的平台工具組支援下列程式庫 \(視目標而定\)：  
  
|程式庫|以 Windows 桌面應用程式為目標的預設平台工具組|以 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式為目標的預設目標平台工具組|以 [!INCLUDE[winxp](../build/includes/winxp_md.md)]、[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 為目標的 Windows XP 平台工具組|  
|---------|---------------------------------|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|  
|CRT|X|X|X|  
|STL|X|X|X|  
|ATL|X|X|X|  
|ConCRT\/PPL|X|X|X|  
|MFC|X||X|  
|C\+\+ AMP|X|X||  
  
> [!NOTE]
>  以 C\+\+\/CLI 撰寫並以 .NET Framework 4 為目標的應用程式可在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上執行。  
  
### 這些工具組的差異  
 由於平台和程式庫支援的差異，使用 Windows XP 平台工具組的應用程式開發體驗並不如使用預設 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 平台工具組的應用程式開發體驗完整。  
  
-   **C\+\+ 語言功能**  
  
     使用 v110\_xp 平台工具組的應用程式只支援在 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 中實作的 C\+\+11 語言功能。  使用 v120\_xp 平台工具組的應用程式只支援在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 中實作的 C\+\+ 11 語言功能。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 使用舊版平台工具組建置時，會使用對應的編譯器。  請使用較新版的 Windows XP 平台工具組，以利用該版本中所實作的其他 C\+\+11 功能。  
  
-   **遠端偵錯**  
  
     Remote Tools for [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 不支援在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上進行遠端偵錯。  若要偵錯在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上執行的應用程式，您可以使用舊版 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的偵錯工具在本機或從遠端進行偵錯。  這類似於在 Windows Vista 上偵錯應用程式的體驗，會是平台工具組的執行階段目標，而不是遠端偵錯目標。  
  
-   **靜態分析**  
  
     Windows XP 平台工具組不支援靜態分析，因為 [!INCLUDE[win7](../build/includes/win7_md.md)] SDK 和執行階段程式庫的 SAL 註釋不相容。  當您想要在支援 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的應用程式上執行靜態分析時，您可以將解決方案暫時切換為以預設平台工具組為目標，以執行分析，然後再切換回 Windows XP 平台工具組，以建置應用程式。  
  
-   **偵錯 DirectX 圖形**  
  
     由於圖形偵錯工具不支援 Direct3D 9 API，因此無法使用這項工具對在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上使用 Direct3D 的應用程式進行偵錯。  不過，如果應用程式實作使用 Direct3D 10 或 Direct3D 11 API 的替代轉譯器，則會使用圖形偵錯工具來診斷這些 API 的使用問題。  
  
-   **建置 HLSL**  
  
     根據預設，Windows XP 工具組不會編譯 HLSL 原始程式碼檔。  若要編譯 HLSL 檔，請下載及安裝 2010 年 6 月的 DirectX SDK，然後再設定專案的 VC 目錄以包含這個檔案。  如需詳細資訊，請參閱 [2010 年 6 月的 DirectX SDK 下載頁面](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)中的＜DirectX SDK 不會註冊 Visual Studio 2010 的 Include\/程式庫路徑＞一節。