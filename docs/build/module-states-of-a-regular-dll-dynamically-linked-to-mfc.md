---
title: 動態連結至 MFC 之 MFC DLL 的模組狀態
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: cedce676f5586369446c9856fd33e4d16c237b27
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220589"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>動態連結至 MFC 之 MFC DLL 的模組狀態

將一般 MFC DLL 動態連結至 MFC DLL 的功能，可讓某些設定變得非常複雜。 例如，一般 MFC DLL 和使用它的可執行檔可以動態連結至 MFC DLL 和任何 MFC 擴充 Dll。

此設定會對 MFC 全域資料造成問題，例如目前`CWinApp`物件的指標，以及處理對應。

在 MFC 版本4.0 之前，此全域資料會放在 MFC DLL 本身，並由進程中的所有模組共用。 由於每個使用 Win32 DLL 的進程都會取得自己的 DLL 資料複本，因此這個配置提供了一種簡單的方式來追蹤每個處理常式的資料。 此外，由於 AFXDLL 模型假設在進程中只會有一個`CWinApp`物件和一組控制碼對應，因此可以在 MFC DLL 本身追蹤這些專案。

但是能夠以動態方式將一般 MFC DLL 連結至 MFC DLL，現在可以在進程中有兩個或多`CWinApp`個物件，以及兩個或更多的控制碼對應集。 MFC 如何追蹤應該使用的專案？

解決方案是提供每個模組（應用程式或一般 MFC DLL）自己的全域狀態資訊複本。 因此，在一般 MFC DLL 中呼叫**AfxGetApp** ，會傳回 DLL 中`CWinApp`物件的指標，而不是可執行檔中的。 每個模組的 MFC 全域資料複本稱為模組狀態，並在[MFC 技術提示 58](../mfc/tn058-mfc-module-state-implementation.md)中加以說明。

MFC 通用視窗程式會自動切換到正確的模組狀態，因此您不需要在一般 MFC DLL 中執行的任何訊息處理常式中擔心它。 但是當可執行檔呼叫一般 MFC DLL 時，您需要明確地將目前的模組狀態設定為 DLL 的狀態。 若要這麼做，請在從 DLL 匯出的每個函式中使用**AFX_MANAGE_STATE**宏。 將下列程式程式碼新增至從 DLL 匯出的函式開頭，即可完成這項作業：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

- [動態連結至 MFC 的標準 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 擴充 Dll](extension-dlls-overview.md)

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
