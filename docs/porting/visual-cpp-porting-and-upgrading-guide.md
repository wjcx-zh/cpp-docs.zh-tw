---
title: Visual C++ 移植和升級指南 | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed94830a2a048f6706371ed7a88a706d7df04ab7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079840"
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Visual C++ 移植和升級指南

本主題提供升級 Visual C++ 程式碼的指南。 其中包括如何讓程式碼能夠在新版工具上正確編譯和執行，以及利用新語言和 Visual Studio 功能。 本主題也包含將舊版應用程式移轉至更新式平台的相關資訊。

## <a name="reasons-to-upgrade-visual-c-code"></a>升級 Visual C++ 程式碼的原因

基於下列原因，您應該考慮升級程式碼：

- 由於編譯器最佳化功能的增強，程式碼撰寫速度更快。

- 由於編譯器本身效能的提升，建置速度更快。

- 改善標準一致性。 Visual C++ 現在實作的許多功能都是來自最新的 C++ 標準。

- 安全性更高。 提供防護檢查等安全性功能。

### <a name="porting-your-code"></a>移植您的程式碼

升級時，請先考慮您的應用程式程式碼和專案。 是否使用 Visual Studio 建置應用程式？ 如果是，請識別涉及的專案。  是否有自訂建置指令碼？ 如果您有自訂建置指令碼，而不是使用 Visual Studio 的建置系統，則需要在升級時執行更多工作，因為您無法透過 Visual Studio 更新專案檔和組建設定來節省時間。

Visual Studio 中的建置系統和專案檔格式，已從 Visual Studio 2008 以前版本中的 vcbuild，變更為 Visual Studio 2010 以後版本中的 MSBuild。 如果您從 2010 以前版本進行升級，並具有高度自訂的建置系統，您可能必須執行更多工作才能升級。 如果您從 Visual Studio 2010 (含) 以後版本進行升級，您的專案已使用 MSBuild，因此升級專案並針對應用程式建置應該比較容易。

如果您未使用 Visual Studio 的建置系統，則應該考慮升級為使用 MSBuild。 如果升級為使用 MSBuild，未來升級可能比較輕鬆，而且也比較容易使用 Visual Studio Online 等服務。 MSBuild 支援 Visual Studio 支援的所有目標平台。

### <a name="porting-visual-studio-projects"></a>移植 Visual Studio 專案

若要開始升級專案或方案，請直接在新版 Visual Studio 中開啟方案，然後遵循提示開始進行升級。  當您升級專案時，您會取得升級報告，該報告會與 UpgradeLog.htm 一起儲存在專案資料夾中。 升級報告顯示升級程序期間所遇到的問題摘要，以及所做之變更的一些相關資訊，或者顯示可能無法自動解決的問題。

1. 專案屬性

2. Include 檔案

3. 因標準中的編譯器一致性改善或變更而不再正常編譯的程式碼

4. 依賴不再可用之 Visual Studio 或 Windows 功能的程式碼，或者不包含在 Visual Studio 的預設安裝或已從產品移除的標頭檔

5. 由於 API 中的變更 (例如 API 已重新命名、函式簽章已變更或函式已被取代)，而不再進行編譯的程式碼

6. 由於診斷中的變更 (例如警告變成錯誤)，而不再進行編譯的程式碼

7. 由於已變更程式庫所造成的連結器錯誤 (特別是使用 /NODEFAULTLIB 時)

8. 由於行為變更所造成的執行階段錯誤或未預期的結果

9. 由於工具所引進的錯誤所造成的錯誤。 如果發生錯誤，請透過一般支援管道或使用 [Visual Studio 意見反應中心](http://connect.microsoft.com/VisualStudio/Feedback)，向 Visual C++ 小組回報。

除了由於編譯器錯誤而無法避免的變更之外，升級程序中還有一些選擇性變更，例如：

1. 新警告可能表示您想要清除程式碼。 根據特定診斷，這樣做可以改善程式碼的可攜性、標準一致性和安全性。

2. 您可能想要利用較新的編譯器功能，例如 [/guard:cf (啟用流程控制防護)](../build/reference/guard-enable-control-flow-guard.md) 編譯器選項可新增未經授權程式碼執行的檢查。

3. 您可能想要更新一些程式碼以使用簡化程式碼的新語言功能、提升程式的效能，或更新程式碼以使用最新程式庫及符合最新標準和最佳做法。

在您升級並測試專案之後，您還可能想要考慮進一步改善程式碼、規劃程式碼的未來方向，甚至重新考慮專案的架構。 會收到持續進行的開發工作嗎？ 讓您的程式碼在其他平台上執行很重要嗎？  如果是，要在哪些平台上執行？  雖然 C++ 是為了可攜性和跨平台開發所設計的標準語言，但許多 Windows 應用程式的程式碼還是會與 Windows 平台緊密相連。 您想要重構程式碼，來區隔這些高度繫結至 Windows 平台的組件嗎？

您的使用者介面呢？ 如果您使用 MFC，可能會想要更新 UI。 您正在使用 2008 中以功能套件形式引進的任何新版 MFC 功能嗎？ 如果您只想讓應用程式有較新的外觀與風格，則不需要重寫整個應用程式；您可以考慮在 MFC 中使用功能區 API，或使用 MFC 的一些新功能。

如果您要提供程式的 XAML 使用者介面，但不想要建立 UWP 應用程式，則可以搭配使用 C# 與 WPF 來建立 UI 層，以及將標準 C++ 邏輯重構為 DLL。 在 C++/CLI 中建立交互操作層，以連線 C# 與您的原生程式碼。 另一個選項是使用 [C++/CX](https://msdn.microsoft.com/library/windows/apps/xaml/hh699871.aspx) 或 [C++/WinRT](https://github.com/microsoft/cppwinrt) 建立 UWP 應用程式。 在 Windows 10 中，您可以使用 [Desktop App Converter](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) 將現有傳統型應用程式封裝為 UWP 應用程式，而不需要修改任何程式碼。

或者，您可能現在有新的需求，或可以預見會有以非 Windows 桌面的平台 (例如 Windows Phone 或 Android 裝置) 為目標的需求。 您可以將使用者介面程式碼移植到跨平台 UI 程式庫。 有了這些 UI 架構，您就能夠以多個裝置為目標，但仍然使用 Visual Studio 和 Visual Studio 偵錯工具作為開發環境。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[從舊版的 Visual C++ 升級專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|討論如何使用在舊版 Visual C++ 中建立的專案。|
|[Visual Studio 2017 RC 中 C++ 編譯器的新功能](../what-s-new-for-visual-cpp-in-visual-studio.md)|從 Visual Studio 2015 到 Visual Studio 2017 的 IDE 和工具變更|
|[Visual Studio 2017 中的 C++ 一致性改善](../cpp-conformance-improvements-2017.md)|從 Visual Studio 2015 到 Visual Studio 2017 的標準一致性改善|
|[Visual C++ 變更歷程記錄 2003 - 2015](visual-cpp-change-history-2003-2015.md)|從 Visual Studio 2003 到 2015 之 Visual C++ 程式庫和建置工具的所有變更清單，可能需要在程式碼中進行變更。|
|[從 2003 到 2015 的 Visual C++ 新功能](visual-cpp-what-s-new-2003-through-2015.md)|從 Visual Studio 2003 到 Visual Studio 2015 之 Visual C++ 的所有「新功能」資訊。|
|[移植協力廠商程式庫](porting-third-party-libraries.md)|如何使用 **vcpkg** 命令列工具，將舊版開放原始碼程式庫移植至使用較新 Visual C++ 工具組所編譯的版本。|
|[移植和升級：範例和案例研究](porting-and-upgrading-examples-and-case-studies.md)|在本節中，我們將移植和升級幾個範例和應用程式，並討論這些經驗和結果。 您可能發現閱讀這些內容有助於了解移植和升級程序的相關作業。 我們將在整個過程中討論升級的秘訣和訣竅，並示範如何修正特定錯誤。|
|[移植到通用 Windows 平台](porting-to-the-universal-windows-platform-cpp.md)|包含將程式碼移植到 Windows 10 的相關資訊。|
|[針對 UNIX 使用者的 Visual C++ 簡介](introduction-to-visual-cpp-for-unix-users.md)|提供資訊給剛開始使用 Visual C++，並想更有效率使用它的 UNIX 使用者。|
|[從 UNIX 移植到 Win32](porting-from-unix-to-win32.md)|討論將 UNIX 應用程式移轉至 Windows 的選擇。|

## <a name="see-also"></a>請參閱

[Visual C++](../visual-cpp-in-visual-studio.md)