---
title: Visual Studio 舊版的 c + + 專案升級
description: 如何從舊版的 Visual Studio 升級 Microsoft C++ 專案。
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: 7a4ab98c196d601bc458fe33bb1e2cb45ac30088
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505891"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Visual Studio 舊版的 c + + 專案升級

若要升級在舊版 Visual Studio 中建立的專案，請在最新版本的 Visual Studio 中開啟專案。 Visual Studio 將專案升級為目前架構的優惠。

如果您選擇 [ **否**]，專案就不會升級。 針對 Visual Studio 2010 和更新版本中建立的專案，您仍然可以在較新版本的 Visual Studio 中使用專案。 您只需設定專案屬性，就能繼續以較舊的工具組為目標。 如果您在電腦上保留舊版 Visual Studio，其工具組會在較新的版本中提供。 例如，如果您的專案必須繼續在 Windows XP 上執行，您可以升級為 Visual Studio 2019。 然後，您可以在專案屬性中將工具組指定為 v141_xp 或更早版本。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](use-native-multi-targeting.md)。

如果您選擇 [ **是]**，則會就地升級專案。 它無法轉換回較早的版本。 在升級案例中，這就是建立現有專案和方案檔的備份複本的原因。

## <a name="upgrade-reports"></a>升級報表

升級專案時，您會取得升級報表。 報表也會儲存在您的專案資料夾中，作為 UpgradeLog.htm。 升級報表會顯示轉換期間發現問題的摘要。 它會列出所做變更的一些資訊，包括：

- 專案屬性。

- Include 檔案。

- 因為編譯器一致性改善或標準中的變更，所以不再完全編譯的程式碼。

- 依賴不再提供之 Visual Studio 或 Windows 功能的程式碼。 或者，不包含在 Visual Studio 預設安裝中的標頭檔，或已從產品中移除的標頭檔。

- 因為 Api 中的變更（例如重新命名的 Api、變更的函式簽章或已淘汰的函式）而不再編譯的程式碼。

- 因為診斷中的變更而不再編譯的程式碼，例如警告變成錯誤

- 連結器錯誤是因為程式庫已變更，尤其是在使用/NODEFAULTLIB 時。

- 執行時間錯誤或非預期的結果，因為行為變更。

- 工具中引進的錯誤。 如果您發現問題，請透過一般支援管道或使用 [Visual Studio c + + 開發人員社群](https://developercommunity.visualstudio.com/spaces/62/index.html) 頁面，將它報告給 Visual C++ 團隊。

某些升級的專案和解決方案可順利建立，而不需要修改。 不過，大部分的專案可能需要變更專案設定和您的原始程式碼。 沒有辦法解決這些問題，但我們建議使用階段式方法。 開始之前，請參閱 [潛在升級問題的總覽](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) ，以取得許多常見錯誤種類的詳細資訊。

1. 如果) 適用于慣用的版本，請將平臺工具組、c + + 語言標準和 Windows SDK 版本 (。  (**專案**  >  **屬性**設定  >  **屬性**  >  **一般**) 

1. 如果您有許多錯誤，可以在修正時暫時關閉一些選項。 若要關閉[/permissive-](../build/reference/permissive-standards-conformance.md)選項，請使用 [**專案**  >  **屬性**] 設定  >  **屬性**  >  **C/c + +**  >  **語言**。 若要關閉程式[代碼分析](../code-quality/code-analysis-for-c-cpp-overview.md)選項，請使用 [**專案**屬性] 設定屬性 [程式  >  **Properties**  >  **Configuration Properties**  >  **代碼分析**]。

1. 請確定所有相依性都存在，而且包含路徑或程式庫位置是正確的。  (**專案**  >  **屬性**設定  >  **屬性**的  >  **VC + + 目錄**) 

1. 找出並修正已不再存在的 Api 參考所造成的錯誤。

1. 修正任何其他阻礙編譯的錯誤。 請參閱常見錯誤修正 [的潛在升級問題總覽](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) 。

1. 重新開啟 **/permissive-** ，並修正先前在 MSVC 中編譯之不符合標準的程式碼所造成的任何新錯誤。

1. 開啟程式碼分析，以找出可能的問題或過時的程式碼模式，不再被視為可接受。 如果程式碼分析旗標許多錯誤，您可以關閉部分警告，先將焦點放在最重要的部分。 IDE 可協助您快速修正某些類型的問題。

1. 請考慮其他現代化程式碼的機會。 例如，將自訂資料結構和演算法取代為來自 c + + 標準程式庫的自訂資料結構和演算法，或提升開放原始碼程式庫。 使用標準功能，可讓其他人更輕鬆地維護程式碼。 您可以確信這段程式碼已經過完善的測試，並由許多專家對標準委員會和更廣泛的 c + + 社區進行審核。

若要修正錯誤，請嘗試在 Stack Overflow 或 [c + + 開發人員社群](https://developercommunity.visualstudio.com/spaces/62/index.html)上搜尋或張貼問題。

## <a name="in-this-section"></a>本節內容

[可能的升級問題總覽](overview-of-potential-upgrade-issues-visual-cpp.md)\
[將您的程式碼升級至通用 CRT](upgrade-your-code-to-the-universal-crt.md)\
[更新 WINVER 和 _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[修正程式庫內部的相依性](fix-your-dependencies-on-library-internals.md)\
[浮點遷移問題](floating-point-migration-issues.md)\
[Visual Studio 2019 中已淘汰的 c + + 功能](features-deprecated-in-visual-studio.md)\
[VCBuild 與 MSBuild 的比較](build-system-changes.md)\
[移植協力廠商程式庫](porting-third-party-libraries.md)

## <a name="see-also"></a>另請參閱

[Visual Studio 中 Visual C++ 的新功能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visual C++ 變更歷程記錄 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[非標準行為](../cpp/nonstandard-behavior.md)\
[移植資料應用程式](../data/data-access-programming-mfc-atl.md)
