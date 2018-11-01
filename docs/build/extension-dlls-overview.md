---
title: 擴充 DLL：概觀
ms.date: 11/04/2016
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: 1967370f587b0b78c4e68ebff14804b20f158bd0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498198"
---
# <a name="mfc-extension-dlls-overview"></a>MFC 擴充 Dll： 概觀

MFC 擴充 DLL 是 DLL，通常會實作衍生自現有 Mfc 程式庫類別的可重複使用類別。 MFC 擴充 Dll 是建置使用 MFC （也稱為 MFC 的共用版本） 的動態連結程式庫版本。 只有 MFC 可執行檔 （應用程式或 MFC 的標準 Dll） 建立的 MFC 的共用版本可以使用 MFC 擴充 DLL。 使用 MFC 擴充 DLL，您可以從 MFC 衍生新的自訂類別，並接著提供這個擴充的版本的 MFC 呼叫 DLL 的應用程式。

擴充 Dll 也可用來傳遞應用程式和 DLL 之間的 MFC 衍生的物件。 傳遞的物件相關聯的成員函式會存在於物件建立所在的模組。 因為使用共用的 MFC 的 DLL 版本時，這些函式會正確匯出，您可以自由地傳遞 MFC 或 MFC 延伸模組載入的 Dll 和應用程式之間的 MFC 衍生的物件指標。

如需範例 MFC 擴充 DLL 的基本需求，可滿足的 dll，請參閱 MFC 範例[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。 特別是，看看 Testdll1.cpp 和 Testdll2.cpp 檔案。

請注意，詞彙 AFXDLL 不再使用 Visual c + + 文件中。 MFC 擴充 DLL 有之前的 AFXDLL 相同的特性。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [初始化 MFC 擴充 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [MFC 延伸模組 DLL](../build/extension-dlls.md)

- [在 MFC DLL 中使用資料庫、OLE 和通訊端 MFC 延伸模組 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [非 MFC DLL：概觀](../build/non-mfc-dlls-overview.md)

- [靜態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [建立 MFC DLL](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>另請參閱

[DLL 的種類](../build/kinds-of-dlls.md)