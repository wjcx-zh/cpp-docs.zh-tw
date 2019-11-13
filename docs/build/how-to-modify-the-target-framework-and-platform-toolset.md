---
title: 如何：修改目標 Framework 和平台工具組
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: c5e7172fea06f6b455422fb023a0b6462b5c4103
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964896"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>如何：修改目標 Framework 和平台工具組

您可以編輯 Visual Studio C++專案檔案，以不同版本的C++平臺工具組、Windows SDK 和 .NET Framework （C++僅限/cli 專案）為目標。 根據預設，專案系統會使用對應於建立專案所用 Visual Studio 版本的 .NET Framework 版本及工具組版本。 您可以修改 .vcxproj 檔案中的所有這些值，讓您可以針對每個編譯目標使用相同的程式碼基底。

## <a name="platform-toolset"></a>平臺工具組

平臺工具組是由C++編譯器（cl）和連結器（link .exe）所組成，以及 C/C++ standard 程式庫。 由於 Visual Studio 2015，工具組的主要版本已維持為14，這表示以 Visual Studio 2019 或 Visual Studio 2017 編譯的專案會與以 Visual Studio 2015 編譯的專案回溯相容。 從 Visual Studio 2015 開始，次要版本已針對每個版本更新1：

- Visual Studio 2015： v140
- Visual Studio 2017： v141
- Visual Studio 2019：適用于 v142

這些工具組支援 .NET Framework 4.5 和更新版本。

Visual Studio 也支援專案的C++多目標。 您可以使用 Visual Studio IDE 來編輯和建立使用舊版 Visual Studio 所建立的專案，而不需將其升級為使用新版的工具組。 您需要在電腦上安裝較舊的工具組。 如需詳細資訊，請參閱[如何在 Visual Studio 中使用原生多目標](../porting/use-native-multi-targeting.md)。 例如，在 Visual Studio 2015 中，您可以將*目標*設為 .NET Framework 2.0，但您必須使用舊版工具組來支援它。

## <a name="target-framework-ccli-project-only"></a>目標 framework （C++僅限/cli 專案）

當您變更目標 Framework 時，也會將平台工具組變更為支援該 Framework 的版本。 例如，若要使用 .NET Framework 4.5，必須使用 Visual Studio 2015 (v140)、Visual Studio 2013 (v120) 或 Visual Studio 2012 (v110) 這些相容的平台工具組。 您可以使用[Windows 7.1 SDK](https://www.microsoft.com/download/details.aspx?id=8279)平臺工具組，將目標設為 .NET Framework 2.0、3.0、3.5 和4，以及 x86/x64 平臺。

您可以建立自訂平台工具組進一步擴充目標平台。 如需詳細資訊，請參閱 Visual C++ 部落格中的 [C++ 原生多目標](https://devblogs.microsoft.com/cppblog/c-native-multi-targeting/) 。

### <a name="to-change-the-target-framework"></a>若要變更目標 Framework

1. 在 Visual Studio 的 **方案總管**中選取您的專案。 在功能表列上開啟 [專案] 功能表，然後選擇 [卸載專案]。 這會卸載專案的專案 (.vcxproj) 檔案。

   > [!NOTE]
   >  在 Visual Studio 中修改專案檔時，無法載入 C ++ 專案。 不過，當專案在 Visual Studio 中載入時，您可以使用其他編輯器 (例如記事本) 修改專案檔。 Visual Studio 會偵測到專案檔已變更，並提示您重新載入專案。

1. 在功能表列上，選取 [ **檔案**]、[ **開啟**]、[ **檔案**]。 在 [ **開啟檔案** ] 對話方塊中，巡覽至專案資料夾，然後開啟專案 (.vcxproj) 檔案。

1. 在專案檔中，尋找目標 Framework 版本的項目。 例如，如果您的專案設計為使用 .NET Framework 4.5，請在 `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` 項目的 `<PropertyGroup Label="Globals">` 項目中找出 `<Project>` 。 如果 `<TargetFrameworkVersion>` 項目不存在，您的專案不會使用 .NET Framework，也就不需要變更。

1. 將值變更為所需的 Framwork 版本，例如 v3.5 或 v4.6。

1. 儲存變更並關閉編輯器。

1. 在 [ **方案總管**]中，開啟專案的捷徑功能表，然後選擇 [ **重新載入專案**]。

1. 若要驗證此變更，請在 [方案總管]上按一下滑鼠右鍵，以開啟專案 (而非解決方案) 的捷徑功能表，然後選擇 [屬性] ，以開啟專案的 [屬性頁] 對話方塊。 在對話方塊的左窗格中，展開 [ **組態屬性** ]，然後選取 [ **一般**]。 確認 **目標 .NET Framework 版本** 顯示的是新的  Framework 版本。

### <a name="to-change-the-platform-toolset"></a>變更平臺工具組

1. 在 Visual Studio 的 [方案總管]中，開啟專案 (而非解決方案) 的捷徑功能表，然後選擇 [屬性] 以開啟專案 [屬性頁] 對話方塊。

1. 在 [ **屬性頁** ] 對話方塊中，開啟 [ **組態** ] 下拉式清單，然後選取 [ **所有組態**]。

1. 在對話方塊的左窗格中，展開 [ **組態屬性** ]，然後選取 [ **一般**]。

1. 在右窗格中，選取 [ **平台工具組** ]，然後從下拉式清單中選取您想要的工具組。 例如，如果您已安裝 Visual Studio 2010 工具組，請選取 [ **Visual Studio 2010 （v100）** ] 以用於您的專案。

1. 選擇 [ **確定** ] 按鈕。

## <a name="see-also"></a>請參閱

[命令列上的 MSBuild - C++](msbuild-visual-cpp.md)
