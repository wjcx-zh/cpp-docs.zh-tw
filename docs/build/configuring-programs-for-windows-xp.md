---
title: 為 Windows XP 設定程式
description: 如何在 Visual Studio 中安裝和使用 c + + Windows XP 工具組。
ms.date: 03/16/2020
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 92364d7fd25ac617baacc125b279fb0ee9c92f62
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440474"
---
# <a name="configuring-programs-for-windows-xp"></a>為 Windows XP 設定程式

Visual Studio 支援多個平臺工具組。 這表示您可以將預設工具組不支援的作業系統和執行時間程式庫設為目標。 例如，藉由切換平臺工具組，您可以使用 Visual Studio 2017 c + + 編譯器來建立以 Windows XP 和 Windows Server 2003 為目標的應用程式。 您也可以使用舊版平台工具組來保留與二進位檔相容的舊版程式碼，同時仍可使用 Visual Studio IDE 的最新功能。

::: moniker range="vs-2019"

Visual Studio 2019 中提供的適用于 v142 工具組不包含建立 Windows XP 程式碼的支援。 使用 Visual Studio 2017 v141_xp 工具組支援 Windows XP 開發，在 Visual Studio 安裝程式中是以個別元件選項的形式提供。

::: moniker-end

## <a name="install-the-windows-xp-platform-toolset"></a>安裝 Windows XP 平台工具組

::: moniker range="<=vs-2017"

若要取得以 Windows XP 和 Windows Server 2003 為目標的 Visual Studio 2017 平臺工具組和元件，請執行 Visual Studio 安裝程式。 當您一開始安裝 Visual Studio 或修改現有的安裝時，請確定已選取 [**使用 c + + 進行桌面開發**] 工作負載。 在此工作負載的選擇性元件清單中，選擇 [C++ 的 Windows XP 支援]****，然後選擇 [安裝]**** 或 [修改]****。

::: moniker-end

::: moniker range="vs-2019"

若要取得以 Windows XP 和 Windows Server 2003 為目標的 v141_xp 平臺工具組和元件，請執行 Visual Studio 安裝程式。 當您一開始安裝 Visual Studio，或修改現有的安裝時，請確定已選取 [**使用 c + + 進行桌面開發**] 工作負載。 在 [**個別元件**] 索引標籤的 [**編譯器]、[組建工具] 和 [運行**時間] 底下，選擇 [ **c \[+ + Windows XP Support for VS 2017 （v141） tools 已淘汰]]**，然後選擇 [**安裝**或**修改**

::: moniker-end

## <a name="windows-xp-targeting-experience"></a>以 Windows XP 為目標的體驗

Visual Studio 隨附的 Windows XP 平臺工具組是 Windows 7 SDK 的版本，但它會使用 Visual Studio 2017 c + + 編譯器。 它也會將專案屬性設定為適當的預設值，例如設定下層目標的相容連結器規格。 只有使用 Windows XP 平臺工具組建立的 Windows 桌面應用程式可以在 Windows XP 和 Windows Server 2003 上執行。 這些應用程式也可以在較新的 Windows 作業系統上執行。

### <a name="to-target-windows-xp"></a>以 Windows XP 為目標

1. 在方案總管**** 中，開啟專案的捷徑功能表，然後選擇 [屬性]****。

1. 在專案的 [**屬性頁**] 對話方塊中，選取 [設定**屬性** > ]**[一般**]。 將 [**平臺工具**組] 屬性設定為您慣用的 Windows XP 工具組。 例如，選擇 **Visual Studio 2017 - Windows XP (v141_xp)**，以使用 Visual Studio 2017 中的 Microsoft C++ 編譯器建立適用於 Windows XP 和 Windows Server 2003 的程式碼。

### <a name="c-runtime-support"></a>C++ 執行階段支援

除了 Windows XP 平臺工具組，有數個程式庫也包含 Windows XP 和 Windows Server 2003 的執行時間支援。 這些程式庫包括： C 執行時間程式庫（CRT）、c + + 標準程式庫、Active Template Library （ATL）、並行執行階段程式庫（ConCRT）、平行模式程式庫（PPL）、MFC 程式庫（MFC）和 C++ AMP （c + + 加速大型程式設計）程式庫。 針對這些作業系統，支援的最低版本包括：適用于 x86 的 Windows XP Service Pack 3 （SP3）、適用于 x64 的 Windows XP service Pack 2 （SP2），以及適用于 x86 和 x64 的 windows Server 2003 Service Pack 2 （SP2）。

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

由於平臺和程式庫支援的差異，使用 Windows XP 平臺工具組之應用程式的開發體驗，與使用預設 Visual Studio 平臺工具組的應用程式並不完整。

- **C++ 語言功能**

   使用 v110\_xp 平台工具組的應用程式僅支援在 Visual Studio 2012 中實作的 C++ 語言功能。 使用 v120\_xp 平台工具組的應用程式僅支援在 Visual Studio 2013 中實作的 C++ 語言功能。 使用 v140\_xp 平台工具組的應用程式僅支援在 Visual Studio 2015 中實作的 C++ 語言功能。 使用 v141\_xp 平臺工具組的應用程式只支援在 Visual Studio 2017 中實作為 c + + 語言功能。 Visual Studio 在使用舊版平台工具組建置時，會使用對應的編譯器。 請使用最新版的 Windows XP 平台工具組，以利用該編譯器版本中實作的其他 C++ 語言功能。

- **遠端偵錯**

   Visual Studio 遠端工具不支援 Windows XP 或 Windows Server 2003 上的遠端偵錯。 若要在 Windows XP 或 Windows Server 2003 上本機或遠端偵錯程式，請使用舊版 Visual Studio 的偵錯工具。 這類似于在 Windows Vista 上進行應用程式的偵錯工具，這是平臺工具組的執行時間目標，而不是遠端偵錯程式目標。

- **靜態分析**

   Windows XP 平台工具組不支援靜態分析，因為 Windows 7 SDK 和執行階段程式庫的 SAL 註釋不相容。 您仍然可以在支援 Windows XP 或 Windows Server 2003 的應用程式上執行靜態分析。 暫時將解決方案切換為以預設平臺工具組為目標，以進行分析，然後切換回 Windows XP 平臺工具組來建立應用程式。

- **偵錯 DirectX 圖形**

   因為圖形偵錯工具不支援 Direct3D 9 API，所以不能用來對在 Windows XP 或 Windows Server 2003 上使用 Direct3D 的應用程式進行 debug 錯。 不過，如果應用程式根據 Direct3D 10 或 Direct3D 11 Api 來執行替代轉譯器，您可以使用圖形偵錯工具來診斷問題。

- **建置 HLSL**

   Windows XP 工具組預設不會編譯 HLSL 原始程式碼檔。 若要編譯 HLSL 檔，請下載及安裝 2010 年 6 月的 DirectX SDK，然後再設定專案的 VC 目錄以包含這個檔案。 如需詳細資訊，請參閱 [2010 年 6 月的 DirectX SDK 下載頁面](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)中的「DirectX SDK 不會註冊 Visual Studio 2010 的 Include/程式庫路徑」一節。
