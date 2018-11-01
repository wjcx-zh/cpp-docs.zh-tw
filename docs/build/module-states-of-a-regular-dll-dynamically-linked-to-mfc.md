---
title: 動態連結至 MFC 的標準 MFC DLL 的模組狀態
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: bd485e484287a17b1f016acc7012178a2c74343d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462877"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>動態連結至 MFC 的標準 MFC DLL 的模組狀態

動態連結至 MFC DLL 的 一般 MFC DLL 的能力可讓一些非常複雜的組態。 比方說，MFC DLL，並使用它的可執行檔可以同時以動態方式連結到 MFC DLL 以及任何 MFC 擴充 Dll。

這個組態會與 MFC 全域資料，例如目前的指標有關的問題`CWinApp`物件和控制代碼的對應。

MFC 4.0 版，此全域資料常駐於 MFC DLL 本身前後程序中所有模組所共用。 因為每個使用 Win32 DLL 的處理序都有它自己的 DLL 的資料複本，此配置會提供簡單的方法，來追蹤每個處理序的資料。 此外，因為 AFXDLL 模型假設，會有只有一個`CWinApp`物件和一組處理程序中的對應，MFC DLL 本身中可追蹤這些項目。

但若要動態連結至 MFC DLL 的 MFC DLL 的能力，現在可以有兩個或多個`CWinApp`處理序中的物件，和也兩個或多個集合的控制代碼對應。 如何沒有 MFC 追蹤的應該使用何者？

解決方法是為每個模組 （應用程式或 MFC DLL） 提供它自己的全域狀態資訊的複本。 因此，呼叫**AfxGetApp**在一般 MFC DLL 將指標傳回至`CWinApp`DLL，而不是可執行檔中的物件。 這個每個模組 MFC 通用資料複本就所謂的模組狀態及所述[MFC 技術提示 58](../mfc/tn058-mfc-module-state-implementation.md)。

MFC 通用的視窗程序會自動切換到正確的模組狀態，因此您不需要擔心它在您的標準 MFC DLL 中實作的任何訊息處理常式。 但當可執行檔呼叫 MFC 的標準 DLL 時，您需要明確地將目前的模組狀態設定為 dll。 若要這樣做，請使用**AFX_MANAGE_STATE**從 DLL 匯出的每個函式中的巨集。 這是藉由從 DLL 匯出的函式的開頭加入下列程式碼行：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

- [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL](../build/extension-dlls-overview.md)

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)