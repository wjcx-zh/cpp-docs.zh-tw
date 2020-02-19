---
title: 升級C++舊版 Visual Studio 的專案
description: 如何從舊版的 Visual Studio 升級 Microsoft C++ 專案。
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: bc9fb5628c1a628b91f306c346f2bbb1dea13de8
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416115"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>升級C++舊版 Visual Studio 的專案

若要升級在舊版 Visual Studio 中建立的專案，請直接在最新版本的 Visual Studio 中開啟專案。 Visual Studio 將專案升級為目前架構的優惠。

如果您選擇 [**否**]，專案就不會升級。 針對在 Visual Studio 2010 和更新版本中建立的專案，您仍然可以在較新版本的 Visual Studio 中使用專案。 只要設定您的專案屬性，即可繼續以較舊的工具組為目標。 如果您將舊版的 Visual Studio 保留在電腦上，則會在較新版本中提供其工具組。 例如，如果您的專案必須繼續在 Windows XP 上執行，您可以升級至 Visual Studio 2019。 然後，您可以在專案屬性中將工具組指定為 v141_xp 或更早的版本。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](use-native-multi-targeting.md)。

如果您選擇 [**是]** ，則會就地升級專案。 它無法轉換回先前的版本。 在升級案例中，這就是建立現有專案和方案檔備份複本的最佳做法。

## <a name="upgrade-reports"></a>升級報表

當您升級專案時，您會取得升級報表。 報表也會以 UpgradeLog 的形式儲存在您的專案資料夾中。 [升級] 報表會顯示轉換期間發現的問題摘要。 它會列出一些已進行變更的相關資訊，包括：

- 專案屬性。

- Include 檔案。

- 因為編譯器的一致性改進或標準中的變更，而不再編譯的程式碼。

- 依賴已無法再使用之 Visual Studio 或 Windows 功能的程式碼。 或者，不包含在 Visual Studio 預設安裝中的標頭檔，或已從產品移除。

- 因為 Api 的變更（例如重新命名的 Api、已變更的函式簽章，或已被取代的函式）而不再編譯的程式碼

- 因為診斷中的變更而不再編譯的程式碼，例如警告變成錯誤

- 連結器錯誤，因為已變更程式庫，特別是在使用/NODEFAULTLIB 時。

- 執行時間錯誤或非預期的結果，因為行為變更。

- 工具中引進的錯誤。 如果您發現問題，請透過一般支援管道或C++使用[Visual Studio C++開發人員社區](https://developercommunity.visualstudio.com/spaces/62/index.html)頁面，向視覺效果小組報告。

有些已升級的專案和解決方案可以成功建立而不需要修改。 不過，大部分專案都可能需要變更專案設定和您的原始程式碼。 修正這些問題沒有一種正確的方法，但我們建議使用階段式方法。 開始之前，請參閱[潛在升級問題的總覽](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)，以取得許多常見錯誤種類的詳細資訊。

1. 將 [平臺工具組C++ ]、[語言標準] 和 [Windows SDK 版本（如果適用的話）] 設定為慣用的版本。 （**專案** > **屬性** > 設定**屬性** > **一般**）

1. 如果您有許多錯誤，可以在修正時暫時關閉一些選項。 若要關閉 [ [/permissive-](../build/reference/permissive-standards-conformance.md) ] 選項，請使用 [**專案** > **屬性**] > [設定**屬性**] > [ **C/C++**  > **語言**]。 若要關閉 [程式[代碼分析](/cpp/code-quality/code-analysis-for-c-cpp-overview)] 選項，請使用 [**專案** > **屬性**] > 設定**屬性** > [程式**代碼分析**]。

1. 請確定所有相依性都存在，而且包含路徑或程式庫位置是正確的。 （**專案** > **屬性** > 設定**屬性** > **VC + + 目錄**）

1. 識別並修正因參考不再存在的 Api 而造成的錯誤。

1. 修正任何阻礙編譯的剩餘錯誤。 如需常見錯誤的修正，請參閱[潛在升級問題的總覽](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)。

1. 重新開啟 **/permissive-** ，並修正先前在 MSVC 中編譯之不一致程式碼所造成的任何新錯誤。

1. 開啟程式碼分析，以找出可能的問題或已過時的編碼模式，而不再被視為可接受。 如果程式碼分析旗標許多錯誤，您可以關閉一些警告，先將重點放在最重要的部分。 IDE 可協助您快速修正某些類型的問題。

1. 請考慮其他現代化程式碼的機會。 例如，以C++標準程式庫中的自訂資料結構和演算法，或提升開放原始碼程式庫來取代。 藉由使用標準功能，您可以更輕鬆地讓其他人維護程式碼。 您可以確信這段程式碼已經過完善的測試，並由許多專家對標準委員會和更廣泛C++的社區進行審核。

對於難以修正的錯誤，請嘗試在 Stack Overflow 或[ C++開發人員的團體](https://developercommunity.visualstudio.com/spaces/62/index.html)上搜尋或張貼問題。

## <a name="in-this-section"></a>本節內容

[可能的升級問題總覽](overview-of-potential-upgrade-issues-visual-cpp.md)\
將[您的程式碼升級至通用 CRT](upgrade-your-code-to-the-universal-crt.md)\
[更新 WINVER 和 _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[修正程式庫內部\ 的](fix-your-dependencies-on-library-internals.md)相依性
[浮點遷移問題](floating-point-migration-issues.md)\
[Visual Studio 2019 中已淘汰的功能\ C++ ](features-deprecated-in-visual-studio.md)
[VCBuild 與 MSBuild](build-system-changes.md)\
[埠協力廠商程式庫](porting-third-party-libraries.md)

## <a name="see-also"></a>另請參閱

[Visual Studio 中的視覺效果C++新功能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[視覺C++效果變更歷程記錄 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[非標準行為](../cpp/nonstandard-behavior.md)\
[埠資料應用程式](../data/data-access-programming-mfc-atl.md)
