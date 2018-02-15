---
title: "為 Windows XP 設定程式 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02ddf1d602fa88caa3ab069e6f2304ccb066621a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="configuring-programs-for-windows-xp"></a>為 Windows XP 設定程式

由於 Visual Studio 支援多個平台工具組，您可以為目標的作業系統和執行階段程式庫不支援的預設工具組。 例如，藉由切換平台工具組，您可以使用 C + + 11、 C + + 14 中和支援的 Visual c + + 編譯器，Visual Studio 中的 C + + 17 語言增強功能來建立應用程式目標[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]。 您可以也使用舊版平台工具組來保留二進位相容的舊版程式碼，同時仍然利用 Visual Studio IDE 的最新功能。

## <a name="install-the-windows-xp-platform-toolset"></a>安裝 Windows XP 平台工具組

若要取得的平台工具組和以目標元件[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]在 Visual Studio 2017，執行 Visual Studio 安裝程式。 當您初次安裝 Visual Studio 或您選擇**修改**若要修改現有的安裝，請確定**的 c + + 桌面應用程式開發**選取工作負載。 在此工作負載的選用元件的清單中選擇**c + + 的 Windows XP 支援**，然後選擇 **安裝**或**修改**。

## <a name="windows-xp-targeting-experience"></a>以 Windows XP 為目標的體驗

隨附於 Visual Studio 中的 Windows XP 平台工具組是版本的[!INCLUDE[win7](../build/includes/win7_md.md)]SDK，但它會使用目前的 c + + 編譯器。 它也會設定專案屬性，以適當的預設值，例如，下層目標的相容連結器的規格。 使用 Windows XP 平台工具組所建立的桌面應用程式執行的 Windows[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]，但這些應用程式也可在較新的 Windows 作業系統上執行。

#### <a name="to-target-windows-xp"></a>以 Windows XP 為目標

1. 在方案總管中，開啟專案的捷徑功能表，然後選擇 [屬性]。

1. 在**屬性頁**對話方塊中的專案，在**組態屬性** > **一般**，將**平台工具組**所需的 Windows XP 工具組的屬性。 例如，選擇**Visual Studio 2017-Windows XP (v141_xp)**建立程式碼[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]所使用的 Microsoft Visual c + + 2017年編譯器。

### <a name="c-runtime-support"></a>C++ 執行階段支援

以及 Windows XP 平台工具組、 C 執行階段程式庫 (CRT)、 c + + 標準程式庫、 Active Template Library (ATL)、 Concurrency Runtime Library (ConCRT)、 Parallel Patterns Library (PPL)、 Microsoft Foundation 類別庫 (MFC)，而 c + + AMP （c + +Accelerated Massive 程式設計) 程式庫包括執行階段支援[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]。 針對這些作業系統中，最小支援的版本為[!INCLUDE[winxp](../build/includes/winxp_md.md)]x86、 Service Pack 3 (SP3) [!INCLUDE[winxp](../build/includes/winxp_md.md)] x64 的 Service Pack 2 (SP2) 和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]適用於 x86 和 x64 的 Service Pack 2 (SP2)。

安裝 Visual Studio 中，所根據的目標平台工具組支援這些程式庫：

|程式庫|以 Windows 桌面應用程式為目標的預設平台工具組|預設平台工具組目標市集應用程式|Windows XP 平台工具組目標[!INCLUDE[winxp](../build/includes/winxp_md.md)]， [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|
|---|---|---|---|
|CRT|X|X|X|
|C++ 標準程式庫|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> 以 C++/CLI 撰寫並以 .NET Framework 4 為目標的應用程式可在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上執行。

### <a name="differences-between-the-toolsets"></a>這些工具組的差異

由於平台和程式庫支援的差異，所以使用 Windows XP 平台工具組的應用程式的開發經驗不使用預設 Visual Studio 平台工具組的應用程式與為完成。

- **C + + 語言功能**

   只有 c + + 語言功能在 Visual Studio 2012 中實作支援應用程式中的 v110\_xp 平台工具組。 只有 c + + 語言功能在 Visual Studio 2013 中實作支援應用程式中的 v120\_xp 平台工具組。 只有 c + + 語言功能在 Visual Studio 2012 中實作支援應用程式中的 v140\_xp 平台工具組。 建置使用舊版平台工具組時，visual Studio 會使用對應的編譯器。 若要充分利用該版本的編譯器中實作的其他 c + + 語言功能使用最新的 Windows XP 平台工具組。

- **遠端偵錯**

   Visual Studio 遠端工具不支援在遠端偵錯[!INCLUDE[winxp](../build/includes/winxp_md.md)]或[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]。 若要偵錯應用程式上執行時[!INCLUDE[winxp](../build/includes/winxp_md.md)]或[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]，您可以使用從較舊版本的 Visual Studio 偵錯工具在本機或遠端偵錯。 這類似於在 Windows Vista 上偵錯應用程式的體驗，會是平台工具組的執行階段目標，而不是遠端偵錯目標。

- **靜態分析**

   Windows XP 平台工具組不支援靜態分析，因為 [!INCLUDE[win7](../build/includes/win7_md.md)] SDK 和執行階段程式庫的 SAL 註釋不相容。 當您想要在支援 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的應用程式上執行靜態分析時，您可以將解決方案暫時切換為以預設平台工具組為目標，以執行分析，然後再切換回 Windows XP 平台工具組，以建置應用程式。

- **偵錯 DirectX 圖形**

     由於圖形偵錯工具不支援 Direct3D 9 API，因此無法使用這項工具對在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上使用 Direct3D 的應用程式進行偵錯。 不過，如果應用程式實作使用 Direct3D 10 或 Direct3D 11 API 的替代轉譯器，則會使用圖形偵錯工具來診斷這些 API 的使用問題。

- **建置 HLSL**

   根據預設，Windows XP 工具組不會編譯 HLSL 原始程式碼檔。 若要編譯 HLSL 檔，請下載及安裝 2010 年 6 月的 DirectX SDK，然後再設定專案的 VC 目錄以包含這個檔案。 如需詳細資訊，請參閱 「 DirectX SDK 不會註冊 Visual Studio 2010 的 Include/程式庫路徑 」 一節[2010 年 6 月 DirectX SDK 下載頁面](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)。
