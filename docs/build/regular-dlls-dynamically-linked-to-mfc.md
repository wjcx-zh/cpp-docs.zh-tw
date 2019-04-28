---
title: 動態連結至 MFC 的標準 MFC Dll
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 3bfed5f75dab4c501708950fdb99f53c40ec142c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314997"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>動態連結至 MFC 的標準 MFC Dll

MFC DLL 動態連結至 MFC 一般是在內部使用 MFC 的 DLL，而且在 DLL 中匯出的函式可以呼叫由 MFC 或非 MFC 可執行檔。 如名稱所述，這類型的 DLL 是使用 MFC （也稱為 MFC 的共用版本） 的動態連結程式庫版本。 通常與一般使用 C 介面的標準 MFC DLL 匯出函式。

您必須新增`AFX_MANAGE_STATE`巨集的動態連結至目前的模組狀態設為 DLL 的一個 MFC 的標準 MFC Dll 中匯出的函式的開頭。 這是藉由從 DLL 匯出的函式的開頭加入下列程式碼行：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

動態連結至 MFC 的標準 MFC DLL，具有下列功能：

- 這是新的視覺效果所引進的 DLL 類型C++4.0。

- 可執行的用戶端可以使用任何支援 Dll 使用的語言撰寫 (C， C++，依照 pascal 命名法、 Visual Basic 等等);它並沒有是一個 MFC 應用程式。

- 不同於以靜態方式連結的標準 MFC DLL，這種類型的 DLL 動態連結至 MFC DLL (也稱為共用 MFC DLL)。

- MFC 匯入程式庫，連結到這種類型的 DLL 是 MFC 擴充 Dll 或使用 MFC DLL 的應用程式所使用的相同：MFCxx (D).lib。

一般 MFC DLL 動態連結至 MFC 的需求如下：

- 這些 Dll 會編譯 **_AFXDLL**定義，就像動態連結至 MFC DLL 的可執行檔。 但是 **_USRDLL**也會定義，就像靜態連結至 MFC 之標準 MFC DLL。

- 這種類型的 DLL 必須具現化`CWinApp`-衍生的類別。

- 這種類型的 DLL 會使用`DllMain`MFC 提供。 將所有的特定 DLL 的初始化程式碼中放`InitInstance`成員函式和終止程式碼中的`ExitInstance`如同正常的 MFC 應用程式。

由於這種 DLL 使用 MFC 的動態連結程式庫版本，您必須明確設定目前的模組狀態到的 DLL。 若要這樣做，請使用[AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)從 DLL 匯出的每個函式開頭的巨集。

MFC 的標準 Dll 必須`CWinApp`-衍生類別，該應用程式類別的單一物件，MFC 應用程式一樣。 不過， `CWinApp` DLL 的物件沒有的主要訊息幫浦，如同`CWinApp`應用程式的物件。

請注意，`CWinApp::Run`機制不會套用到 DLL，因為應用程式擁有的主要訊息幫浦。 如果您的 DLL 顯示非強制回應對話方塊，或有自己的主框架視窗，您的應用程式的主要訊息幫浦必須呼叫所呼叫的 DLL 匯出常式`CWinApp::PreTranslateMessage`。

將所有 DLL 特定的初始化`CWinApp::InitInstance`如同正常的 MFC 應用程式的成員函式。 `CWinApp::ExitInstance`成員函式您`CWinApp`衍生的類別呼叫從提供的 MFC`DllMain`函式卸載 DLL 之前。

您必須使用您的應用程式發佈共用的 Dll MFCx0.dll 和 Msvcr*0.dll （或類似檔案）。

動態連結至 MFC 的 DLL 不能也以靜態方式連結至 MFC。 應用程式連結至 MFC 的標準 Dll 動態連結至 MFC 它就像任何其他 DLL。

一般 MFC DLL 使用標準的 C 介面，通常被匯出符號。 從 MFC DLL 匯出函式的宣告看起來像這樣：

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

MFC DLL 內的所有記憶體配置都應該都留在該 DLL;DLL 不應該傳遞至或接收呼叫的可執行檔從下列其中一項：

- MFC 物件的指標

- MFC 所配置的記憶體的指標

如果您需要執行任何上述項目，或如果您要呼叫的可執行檔和 DLL 之間傳遞的 MFC 衍生的物件，您必須建置 MFC 擴充 DLL。

它是只有當您建立一份資料時，將指標傳遞到所配置的記憶體的 C 執行階段程式庫的應用程式和 DLL 之間的安全。 您必須刪除或調整這些指標的大小或使用它們，而建立複本的記憶體。

建置 MFC DLL，以動態方式連結至 MFC，當您需要使用巨集[AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)正確地切換 MFC 模組狀態。 這是藉由從 DLL 匯出的函式的開頭加入下列程式碼行：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

**AFX_MANAGE_STATE**巨集不應以靜態方式連結至 MFC 的標準 MFC Dll 或 MFC 擴充 Dll 中。 如需詳細資訊，請參閱 <<c0> [ 管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)。

如需如何撰寫、 建置及使用 MFC 的標準 DLL 的範例，請參閱範例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。 如需有關動態連結至 MFC 的標準 MFC Dll 的詳細資訊，請參閱 < 在抽象概念中範例的 「 轉換 DLLScreenCap 到動態連結與 MFC DLL 」 一節。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [初始化 MFC 的標準 Dll](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [動態連結至 MFC 的標準 MFC DLL 的模組狀態](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

- [在 MFC DLL 中使用資料庫、OLE 和通訊端 MFC 延伸模組 DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [將 MFC 當成 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>另請參閱

[DLL 的種類](kinds-of-dlls.md)
