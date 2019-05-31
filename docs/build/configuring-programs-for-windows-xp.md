---
title: 為 Windows XP 設定程式
ms.date: 05/16/2019
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 55753737b4868f33487ed980eaf37a8801f59638
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450697"
---
# <a name="configuring-programs-for-windows-xp"></a>為 Windows XP 設定程式

由於 Visual Studio 支援多個平台工具組，因此您可以將預設工具組不支援的作業系統和執行階段程式庫設為目標。 例如，藉由切換平台工具組，您可以使用 Visual Studio 中的 MSVC 編譯器所支援的 C++11、C++14 和 C++17 語言增強功能，建立以 Windows XP 和 Windows Server 2003 為目標的應用程式。 您也可以使用舊版平台工具組來保留與二進位檔相容的舊版程式碼，同時仍可使用 Visual Studio IDE 的最新功能。

Visual Studio 2019 和更新版本不包含使用 v142 工具組建立 Windows XP 程式碼的支援。 使用隨附於 Visual Studio 2017 的 v141 工具組進行 Windows XP 開發的支援可作為 Visual Studio 安裝程式中的選擇性元件使用。

## <a name="install-the-windows-xp-platform-toolset"></a>安裝 Windows XP 平台工具組

若要在 Visual Studio 2017 中取得以 Windows XP 和 Windows Server 2003 為目標的平台工具組和元件，請執行 Visual Studio 安裝程式。 當您初次安裝 Visual Studio 或選擇 [修改]  以修改現有的安裝時，請確實選取 [使用 C++ 的桌面開發]  工作負載。 在此工作負載的選擇性元件清單中，選擇 [C++ 的 Windows XP 支援]  ，然後選擇 [安裝]  或 [修改]  。

## <a name="windows-xp-targeting-experience"></a>以 Windows XP 為目標的體驗

隨附於 Visual Studio 的 Windows XP 平台工具組是 Windows 7 SDK 的版本，但使用目前的 C++ 編譯器。 它也會將專案屬性設定為適當的預設值，例如設定下層目標的相容連結器規格。 只有使用 Windows XP 平台工具組建立的 Windows 桌面應用程式可在 Windows XP 和 Windows Server 2003 上執行，但這些應用程式也可在較新的 Windows 作業系統上執行。

#### <a name="to-target-windows-xp"></a>以 Windows XP 為目標

1. 在方案總管  中，開啟專案的捷徑功能表，然後選擇 [屬性]  。

1. 在專案的 [屬性頁]  對話方塊中，於 [組態屬性]   > [一般]  下方將 [平台工具組]  屬性設為所需的 Windows XP 工具組。 例如，選擇 **Visual Studio 2017 - Windows XP (v141_xp)** ，以使用 Visual Studio 2017 中的 Microsoft C++ 編譯器建立適用於 Windows XP 和 Windows Server 2003 的程式碼。

### <a name="c-runtime-support"></a>C++ 執行階段支援

除了 Windows XP 平台工具組之外，C Runtime Library (CRT)、C++ 標準範本程式庫、Active Template Library (ATL)、Concurrency Runtime Library (ConCRT)、Parallel Patterns Library (PPL)、Microsoft Foundation Class (MFC) 程式庫和 C++ AMP (C++ Accelerated Massive Programming) 程式庫還包含對 Windows XP 和 Windows Server 2003 的執行階段支援。 這些作業系統的最低支援版本包括適用於 x86 的 Windows XP Service Pack 3 (SP3)、適用於 x64 的 Windows XP Service Pack 2 (SP2)，以及適用於 x86 和 x64 的 Windows Server 2003 Service Pack 2 (SP2)。

Visual Studio 所安裝的平台工具組支援下列程式庫 (視目標而定)：

|程式庫|以 Windows 桌面應用程式為目標的預設平台工具組|以市集應用程式為目標的預設平台工具組|以 Windows XP、Windows Server 2003 為目標的 Windows XP 平台工具組|
|---|---|---|---|
|CRT|X|X|X|
|C++ 標準程式庫|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> 以 C++/CLI 撰寫、並以 .NET Framework 4 為目標的應用程式可在 Windows XP 和 Windows Server 2003 上執行。

### <a name="differences-between-the-toolsets"></a>這些工具組的差異

由於平台和程式庫支援的差異，使用 Windows XP 平台工具組的應用程式在開發體驗方面並不像使用預設 Visual Studio 平台工具組的應用程式那麼完整。

- **C++ 語言功能**

   使用 v110\_xp 平台工具組的應用程式僅支援在 Visual Studio 2012 中實作的 C++ 語言功能。 使用 v120\_xp 平台工具組的應用程式僅支援在 Visual Studio 2013 中實作的 C++ 語言功能。 使用 v140\_xp 平台工具組的應用程式僅支援在 Visual Studio 2015 中實作的 C++ 語言功能。 Visual Studio 在使用舊版平台工具組建置時，會使用對應的編譯器。 請使用最新版的 Windows XP 平台工具組，以利用該編譯器版本中實作的其他 C++ 語言功能。

- **遠端偵錯**

   Visual Studio 遠端工具不支援 Windows XP 或 Windows Server 2003 上的遠端偵錯。 若要偵錯在 Windows XP 或 Windows Server 2003 上執行的應用程式，您可以使用舊版 Visual Studio 的偵錯工具在本機或從遠端進行偵錯。 這類似於在 Windows Vista 上偵錯應用程式的體驗，會是平台工具組的執行階段目標，而不是遠端偵錯目標。

- **靜態分析**

   Windows XP 平台工具組不支援靜態分析，因為 Windows 7 SDK 和執行階段程式庫的 SAL 註釋不相容。 當您想要在支援 Windows XP 或 Windows Server 2003 的應用程式上執行靜態分析時，您可以將解決方案暫時切換為以預設平台工具組為目標，以執行分析，然後再切換回 Windows XP 平台工具組，以建置應用程式。

- **偵錯 DirectX 圖形**

   由於圖形偵錯工具不支援 Direct3D 9 API，因此無法使用這項工具偵錯在 Windows XP 或 Windows Server 2003 上使用 Direct3D 的應用程式。 不過，如果應用程式實作使用 Direct3D 10 或 Direct3D 11 API 的替代轉譯器，則會使用圖形偵錯工具來診斷這些 API 的使用問題。

- **建置 HLSL**

   根據預設，Windows XP 工具組不會編譯 HLSL 原始程式碼檔。 若要編譯 HLSL 檔，請下載及安裝 2010 年 6 月的 DirectX SDK，然後再設定專案的 VC 目錄以包含這個檔案。 如需詳細資訊，請參閱 [2010 年 6 月的 DirectX SDK 下載頁面](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)中的「DirectX SDK 不會註冊 Visual Studio 2010 的 Include/程式庫路徑」一節。
