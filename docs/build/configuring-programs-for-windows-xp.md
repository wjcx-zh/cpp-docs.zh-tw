---
title: 為 Windows XP 設定程式 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c2b1dc80cec8ba18522d8238752857105993074
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720723"
---
# <a name="configuring-programs-for-windows-xp"></a>為 Windows XP 設定程式

由於 Visual Studio 支援多個平台工具組，您可以針對作業系統和預設工具組不支援的執行階段程式庫。 例如，藉由切換平台工具組，您可以使用 C + + 11、 C + + 14 和在 Visual Studio 中 Visual c + + 編譯器支援的 C + + 17 語言增強功能來建立以 Windows XP 和 Windows Server 2003 為目標的應用程式。 您可以也會使用舊版平台工具組來維護的二進位檔相容的舊版程式碼，同時仍然利用 Visual Studio IDE 的最新的功能。

## <a name="install-the-windows-xp-platform-toolset"></a>安裝 Windows XP 平台工具組

若要在 Visual Studio 2017 中取得的平台工具組和目標 Windows XP 和 Windows Server 2003 的元件，請執行 Visual Studio 安裝程式。 當您初次安裝 Visual Studio 或您選擇**修改**若要修改現有的安裝，請確定**使用 c + + 的桌面開發**選取工作負載。 在此工作負載的選用元件的清單中，選擇**c + + 的 Windows XP 支援**，然後選擇**安裝**或**修改**。

## <a name="windows-xp-targeting-experience"></a>以 Windows XP 為目標的體驗

Windows XP 平台工具組隨附於 Visual Studio 中的 Windows 7 SDK 版本，但它會使用目前的 c + + 編譯器。 它也會設定專案屬性，以適當的預設值，例如，針對舊版的相容連結器規格。 只有 Windows 桌面應用程式，使用 Windows XP 和 Windows Server 2003 上執行 Windows XP 平台工具組所建立的但這些應用程式也可以在較新的 Windows 作業系統上執行。

#### <a name="to-target-windows-xp"></a>以 Windows XP 為目標

1. 在方案總管中，開啟專案的捷徑功能表，然後選擇 [屬性]。

1. 在 **屬性頁**對話方塊中的專案，在**組態屬性** > **一般**，將**平台工具組**所需的 Windows XP 工具組的屬性。 例如，選擇**Visual Studio 2017-Windows XP (v141_xp)** 建立適用於 Windows XP 和 Windows Server 2003 的程式碼，使用 Microsoft Visual c + + 2017年編譯器。

### <a name="c-runtime-support"></a>C++ 執行階段支援

Windows XP 平台工具組，C 執行階段程式庫 (CRT)、 c + + 標準程式庫、 Active Template Library (ATL)、 Concurrency Runtime Library (ConCRT)、 平行模式程式庫 (PPL)、 Microsoft Foundation Class 程式庫 (MFC)，及 c + + AMP （c + +加速大規模程式設計） 程式庫包含適用於 Windows XP 和 Windows Server 2003 的執行階段支援。 針對這些作業系統，支援的最低版本是 Windows XP Service Pack 3 (SP3) 適用於 x86 Windows XP Service Pack 2 (SP2) x64 和 Windows Server 2003 Service Pack 2 (SP2) 適用於 x86 和 x64。

安裝 Visual Studio 中，根據目標平台工具組支援這些程式庫：

|程式庫|以 Windows 桌面應用程式為目標的預設平台工具組|預設的平台工具組目標存放區應用程式|以 Windows XP、 Windows Server 2003 為目標的 Windows XP 平台工具組|
|---|---|---|---|
|CRT|X|X|X|
|C++ 標準程式庫|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> 應用程式所撰寫的 C + + /cli Windows XP 和 Windows Server 2003 上執行的 CLI 和.NET Framework 4 為目標。

### <a name="differences-between-the-toolsets"></a>這些工具組的差異

由於平台和程式庫支援差異，所以使用 Windows XP 平台工具組的應用程式的開發體驗不會使用預設 Visual Studio 平台工具組的應用程式與為完成。

- **C + + 語言功能**

   只有 c + + 語言功能在 Visual Studio 2012 中實作支援應用程式中，使用 v110\_xp 平台工具組。 只有 c + + 語言功能實作 Visual Studio 2013 中支援應用程式中，使用 v120\_xp 平台工具組。 只有 c + + 語言功能在 Visual Studio 2015 中實作支援應用程式中，使用 v140\_xp 平台工具組。 建置使用舊版的平台工具組時，visual Studio 會使用對應的編譯器。 使用最新的 Windows XP 平台工具組，才能利用其他的 c + + 語言功能，在該版本的編譯器中實作。

- **遠端偵錯**

   Visual Studio 遠端工具不支援在 Windows XP 或 Windows Server 2003 上的遠端偵錯。 若要在 Windows XP 或 Windows Server 2003 上執行時，偵錯應用程式，您可以使用從較舊版本的 Visual Studio 偵錯工具在本機或遠端偵錯。 這類似於在 Windows Vista 上偵錯應用程式的體驗，會是平台工具組的執行階段目標，而不是遠端偵錯目標。

- **靜態分析**

   Windows XP 平台工具組不支援靜態分析，因為 Windows 7 SDK 和執行階段程式庫的 SAL 註釋不相容。 當您想要的應用程式支援 Windows XP 或 Windows Server 2003 上執行靜態分析時，您可以為目標的預設平台工具組，以執行分析，將解決方案暫時切換，並再切換回 Windows XP 平台工具組，建置應用程式。

- **偵錯 DirectX 圖形**

   圖形偵錯工具不支援 Direct3D 9 API，因為它無法用於偵錯在 Windows XP 或 Windows Server 2003 使用 Direct3D 的應用程式。 不過，如果應用程式實作使用 Direct3D 10 或 Direct3D 11 API 的替代轉譯器，則會使用圖形偵錯工具來診斷這些 API 的使用問題。

- **建置 HLSL**

   根據預設，Windows XP 工具組不會編譯 HLSL 原始程式碼檔。 若要編譯 HLSL 檔，請下載及安裝 2010 年 6 月的 DirectX SDK，然後再設定專案的 VC 目錄以包含這個檔案。 如需詳細資訊，請參閱 「 DirectX SDK 不會註冊 Visual Studio 2010 的 Include/程式庫路徑 」 一節[2010 年 6 月 DirectX SDK 下載頁面](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)。
