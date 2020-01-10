---
title: 支援的平台 (Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
ms.openlocfilehash: 049b28d23c7f5f5f023f3b2964577b75992c2998
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75793826"
---
# <a name="supported-platforms-visual-c"></a>支援的平台 (Visual C++)

使用 Visual Studio 所建置的應用程式，可用於各種平台上，如下所示。

|作業系統|x86|x64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
|Windows Vista|{2&gt;X&lt;2}|{2&gt;X&lt;2}|||
|Windows Server 2008|{2&gt;X&lt;2}|{2&gt;X&lt;2}|||
|Windows 7|{2&gt;X&lt;2}|{2&gt;X&lt;2}|||
|Windows Server 2012 R2|{2&gt;X&lt;2}|{2&gt;X&lt;2}|||
|Windows 8|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}||
|Windows 8.1|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}||
|Windows 10|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}|
|Android \*\*|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}|
|iOS \*\*|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}|
|Linux \*\*\*|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}|{2&gt;X&lt;2}|

\* 您可以使用 Visual Studio 2017、Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 Update 1 中所包含的 Windows XP 平臺工具組，來建立 Windows XP 和 Windows Server 2003 專案。 如需如何使用這個平台工具組的相關資訊，請參閱[為 Windows XP 設定程式](../build/configuring-programs-for-windows-xp.md)。 如需變更平台工具組的其他資訊，請參閱[如何：修改目標 Framework 和平台工具組](../build/how-to-modify-the-target-framework-and-platform-toolset.md)。

\*\* 您可以安裝 Visual Studio 2017 及更新版本安裝程式中的**使用 C++ 進行行動開發**工作負載。 在 Visual Studio 2015 安裝程式中，選擇 [Visual C++ for Cross Platform Mobile Development] 元件，將 iOS 或 Android 平台設為目標。 如需指示，請參閱[安裝適用於跨平台行動裝置開發的 Visual C++](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)。 若要建置 iOS 程式碼，您必須具有 Mac 電腦，並且符合其他需求。 如需必要條件清單和安裝指示，請參閱[安裝和設定工具以使用 iOS 建置](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios)。 您可以配合目標硬體來建置 x86 或 ARM 程式碼。 使用 x86 組態為 iOS 模擬器、Microsoft Visual Studio Emulator for Android 和一些 Android 裝置進行建置。 使用 ARM 組態為 iOS 裝置和大部分 Android 裝置進行建置。

\*\*\* 您可在 Visual Studio 2017 及更新版本安裝程式中，安裝**使用 C++ 進行 Linux 開發**工作負載，將 Linux 平台設為目標。 如需指示，請參閱[下載、安裝及設定 Linux 工作負載](../linux/download-install-and-setup-the-linux-development-workload.md)。 因為此工具組會編譯您在目標電腦上的可執行檔，所以可針對任何支援的架構進行建置。

\*\*\*\* Visual Studio 2017 及更新版本有提供 ARM64 支援。

如需如何設定目標平台組態的資訊，請參閱[如何：將 Visual C++ 專案設定為以 64 位元 (x64) 平台為目標](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。

## <a name="see-also"></a>請參閱

- [Visual Studio 版本中的 Visual C++ 工具和功能](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [使用者入門](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
