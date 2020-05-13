---
title: 如何：偵錯發行的組建
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 6d93fac4e980085c322acb55e6f8758e6cea0a00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188960"
---
# <a name="how-to-debug-a-release-build"></a>如何：偵錯發行的組建

您可以 debug 應用程式的發行組建。

### <a name="to-debug-a-release-build"></a>若要 debug 發行組建

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](working-with-project-properties.md)。

1. 按一下 [ **C/c + +** ] 節點。 將 [**偵錯工具資訊格式**] 設定為[[C7 相容（/Z7）](reference/z7-zi-zi-debug-information-format.md) ] 或 [**程式資料庫（/zi）**]。

1. 展開 [**連結器**]，然後按一下 [**一般**] 節點。 將 [**啟用增量連結**] 設定為[[否] （/INCREMENTAL： No）](reference/incremental-link-incrementally.md)。

1. 選取 [**調試**] 節點。 將 [**產生調試資訊**] 設定為[[是（/debug）]](reference/debug-generate-debug-info.md)。

1. 選取 [**優化**] 節點。 將**參考**設定為[/opt： REF](reference/opt-optimizations.md) ，並**啟用 COMDAT 折**迭至[/opt： ICF](reference/opt-optimizations.md)。

1. 您現在可以在 [發行] 組建應用程式中進行 debug。 若要找出問題，請逐步執行程式碼（或使用即時的偵錯工具），直到您找出發生失敗的位置，然後再判斷不正確的參數或程式碼。

   如果應用程式在 debug 組建中運作，但在發行組建中失敗，則其中一個編譯器優化可能會在原始程式碼中公開缺失。 若要找出問題，請停用每個原始程式碼檔的選取優化，直到找出造成問題的檔案和優化為止。 （若要加速此程式，您可以將檔案分成兩個群組、停用一個群組的優化，以及當您在群組中發現問題時，請繼續進行分割，直到找出問題檔案為止）。

   您可以使用[/rtc](reference/rtc-run-time-error-checks.md)嘗試在您的偵錯工具組建中公開這類 bug。

   如需詳細資訊，請參閱[優化您的程式碼](optimizing-your-code.md)。

## <a name="see-also"></a>請參閱

[解決發行組建的問題](fixing-release-build-problems.md)
