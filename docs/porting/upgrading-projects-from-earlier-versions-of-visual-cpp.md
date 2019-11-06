---
title: 升級C++舊版 Visual Studio 的專案
description: 如何從舊版的 Visual Studio 升級 Microsoft C++ 專案。
ms.date: 10/29/2019
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: b317271a9cd0873e60a6dd9acd1b73a766aaea19
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627158"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>升級C++舊版 Visual Studio 的專案

若要升級在 Visual Studio 2008 或更早版本中建立的專案，您必須先使用 Visual Studio 2010，將專案從 VCBuild 格式（. vcproj）轉換為 MSBuild 格式（. .vcxproj）。 如需詳細資訊，請參閱[Visual Studio 2008 的指示](use-native-multi-targeting.md#instructions-for-visual-studio-2008)。

若要升級在 Visual Studio 2010 或更新版本中建立的專案，請直接在最新版本的 Visual Studio 中開啟專案。 Visual Studio 將專案升級為目前架構的優惠。 如果您選擇 [**否**]，而且電腦上有舊版的 Visual Studio，您可以在較新版本的 Visual Studio 中工作，並繼續以較舊的工具組為目標。 例如，如果您的專案必須繼續在 Windows XP 上執行，您可以將它升級為 Visual Studio 2019，但您必須將工具組指定為 v141 或更早的版本。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](use-native-multi-targeting.md)。 如果您選擇 [**是]** ，則專案將會轉換，而且無法轉換回舊版。 因此，在升級案例中，建立現有專案和方案檔的複本是不錯的作法。

## <a name="upgrade-reports"></a>升級報表

當您升級專案時，您會取得升級報告，該報告會與 UpgradeLog.htm 一起儲存在專案資料夾中。 升級報表會顯示發生的問題的摘要，以及一些已進行變更的相關資訊，包括：

1. 專案屬性

2. Include 檔案

3. 由於編譯器一致性改進或標準中的變更，而不再編譯的程式碼

4. 依賴不再可用之 Visual Studio 或 Windows 功能的程式碼，或者不包含在 Visual Studio 的預設安裝或已從產品移除的標頭檔

5. 由於 API 中的變更 (例如 API 已重新命名、函式簽章已變更或函式已被取代)，而不再進行編譯的程式碼

6. 因為診斷變更而不再編譯的程式碼，例如警告變成錯誤

7. 由於已變更程式庫所造成的連結器錯誤 (特別是使用 /NODEFAULTLIB 時)

8. 由於行為變更所造成的執行階段錯誤或未預期的結果

9. 工具中引進的錯誤。 如果發生錯誤，請透過一般支援管道或使用 [Visual Studio C++ Developer Community](https://developercommunity.visualstudio.com/spaces/62/index.html) (Visual Studio C++ 開發人員社群) 頁面，向 Visual C++ 小組回報。

有些已升級的專案和解決方案可以成功建立而不需要修改。 不過，大部分的專案可能需要變更專案設定和原始程式碼。 有一種正確的方法可以解決這些情況，但是建議使用某種階段式方法。 開始之前，請參閱[潛在升級問題的總覽](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)，以取得許多常見錯誤種類的詳細資訊。

 1. 將平臺工具組、 C++語言標準和 Windows SDK 版本（如果適用）設定為所需的版本。 （**專案** > **屬性** > 設定**屬性** > **一般**）
 1. 如果您有許多錯誤，請關閉 [[寬鬆](../build/reference/permissive-standards-conformance.md)] 選項（[**專案** > **屬性**] > 設定**屬性** > [ **CC++ /**  > **語言**]）和 [程式[代碼分析]](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)（**專案** > **屬性** > 設定**屬性** > 程式**代碼分析**）] 選項會暫時減少錯誤計數。
 1. 請確定所有相依性都存在，而且包含路徑或程式庫位置是正確的。 （**專案** > **屬性** > 設定**屬性** > **VC + + 目錄**）
 1. 識別並修正因參考不再存在的 Api 而造成的錯誤。
 1. 修正任何阻礙編譯的剩餘錯誤。 如需常見錯誤的修正，請參閱[潛在升級問題的總覽](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)。
 1. 開啟 [**寬鬆**]，並修正因先前在 MSVC 中編譯的不一致程式碼而出現的任何新錯誤。
 1. 開啟程式碼分析，以找出可能的問題或已過時的編碼模式，而不再被視為可接受。 如果程式碼分析旗標許多錯誤，您可以關閉一些警告，先將重點放在最重要的部分。 IDE 可協助您快速修正某些類型的問題。
 1. 請考慮其他現代化程式碼的機會，例如，以C++標準程式庫中的自訂資料結構和演算法，或提升開放原始碼程式庫來取代。 藉由使用標準功能，您可以更輕鬆地讓其他人維護程式碼，同時也能安心相信，許多專家對於標準委員會和更廣泛C++的社區而言，程式碼已經過妥善測試與審核。

對於難以修正的錯誤，請嘗試在 Stack Overflow 或[ C++開發人員的團體](https://developercommunity.visualstudio.com/spaces/62/index.html)上搜尋或張貼問題。

## <a name="in-this-section"></a>本節內容

[潛在升級問題概觀](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[將程式碼升級至通用 CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[更新 WINVER 和 _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[修正程式庫內部項目上的相依性](fix-your-dependencies-on-library-internals.md)<br/>
[浮點數的移轉問題](floating-point-migration-issues.md)<br/>
[C++Visual Studio 2019 中已淘汰的功能](features-deprecated-in-visual-studio.md)<br/>
[VCBuild 與 MSBuild 的比較](build-system-changes.md)<br/>
[埠協力廠商程式庫](porting-third-party-libraries.md)<br/>

## <a name="see-also"></a>請參閱

[Visual Studio 之 Visual C++ 的新功能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual C++ 變更歷程記錄 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[非標準行為](../cpp/nonstandard-behavior.md)<br/>
[埠資料應用程式](../data/data-access-programming-mfc-atl.md)<br/>
