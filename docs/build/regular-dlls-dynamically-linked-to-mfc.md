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

動態連結至 MFC 的標準 MFC DLL 是在內部使用 MFC 的 DLL，而 DLL 中匯出的函式可以透過 MFC 或非 MFC 可執行檔來呼叫。 如名稱所述，這種 DLL 是使用 MFC 的動態連結程式庫版本（也稱為 MFC 的共用版本）所建立。 函式通常會使用標準 C 介面從一般 MFC DLL 匯出。

您必須在以`AFX_MANAGE_STATE`動態方式連結至 mfc 的標準 MFC dll 中，于所有匯出函式的開頭加入宏，以便將目前的模組狀態設定為 DLL 的其中一個。 將下列程式程式碼新增至從 DLL 匯出的函式開頭，即可完成這項作業：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

動態連結至 MFC 的一般 MFC DLL 具有下列功能：

- 這是 Visual C++ 4.0 引進的新 DLL 類型。

- 用戶端可執行檔可使用任何支援 Dll （C、c + +、Pascal、Visual Basic 等）的語言來撰寫;它不一定要是 MFC 應用程式。

- 不同于靜態連結的正則 MFC DLL，這種類型的 DLL 會動態連結至 MFC DLL （也稱為共用的 MFC DLL）。

- 連結到此 DLL 類型的 MFC 匯入程式庫，與使用 MFC DLL 的 MFC 延伸 Dll 或應用程式相同： MFCxx （D） .lib。

動態連結至 MFC 的一般 MFC DLL 具有下列需求：

- 這些 Dll 是以 **_AFXDLL**定義的方式進行編譯，就像是動態連結至 MFC DLL 的可執行檔一樣。 但是也會定義 **_USRDLL** ，就像是靜態連結至 mfc 的一般 MFC DLL。

- 這種類型的 DLL 必須具`CWinApp`現化衍生的類別。

- 這種類型的 DLL 會`DllMain`使用 MFC 所提供的。 將所有 DLL 特定的初始化程式碼放`InitInstance`在成員函式中， `ExitInstance`並在中終止程式碼，如同在一般 MFC 應用程式中一樣。

因為這種 DLL 會使用 MFC 的動態連結程式庫版本，所以您必須明確地將目前的模組狀態設定為 DLL 的狀態。 若要這麼做，請在從 DLL 匯出的每個函式開頭使用[AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)宏。

一般 MFC Dll 必須擁有`CWinApp`衍生類別和該應用程式類別的單一物件，如同 MFC 應用程式一樣。 不過，DLL `CWinApp`的物件沒有主要的訊息提取，如同應用程式的`CWinApp`物件。

請注意， `CWinApp::Run`此機制不會套用至 DLL，因為應用程式會擁有主要的訊息提取。 如果您的 DLL 顯示非強制回應對話方塊或有自己的主框架視窗，則應用程式的主要訊息提取必須呼叫呼叫`CWinApp::PreTranslateMessage`的 DLL 匯出常式。

將所有 DLL 特定的初始化放在`CWinApp::InitInstance`成員函式中，如同一般的 MFC 應用程式一樣。 在`CWinApp::ExitInstance`卸載 DLL 之前， `CWinApp`會從 MFC 提供`DllMain`的函式呼叫衍生類別的成員函式。

您必須與您的應用程式一起散發共用 Dll MFCx0 和 Msvcr * 0 .dll （或類似檔案）。

動態連結至 MFC 的 DLL 也不能以靜態方式連結至 MFC。 應用程式會連結到以動態方式連結至 MFC 的標準 MFC Dll，就像任何其他 DLL 一樣。

通常會使用標準 C 介面從一般 MFC DLL 匯出符號。 從一般 MFC DLL 匯出的函式宣告看起來像這樣：

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

一般 MFC DLL 內的所有記憶體配置都應該留在 DLL 內;DLL 不應傳遞至呼叫的可執行檔，或從下列任一項接收：

- MFC 物件的指標

- MFC 所配置之記憶體的指標

如果您需要執行上述任一項，或如果您需要在呼叫可執行檔和 DLL 之間傳遞 MFC 衍生的物件，則必須建立 MFC 擴充 DLL。

只有當您複製資料時，才可以將指標傳遞給應用程式和 DLL 之間的 C 執行時間程式庫所配置的記憶體。 您不能刪除或調整這些指標的大小，也不能在不建立記憶體複本的情況下使用它們。

建立動態連結至 MFC 的標準 MFC DLL 時，您必須使用宏[AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) ，才能正確地切換 mfc 模組狀態。 將下列程式程式碼新增至從 DLL 匯出的函式開頭，即可完成這項作業：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

**AFX_MANAGE_STATE**宏不應用於以靜態方式連結至 mfc 的標準 MFC DLL 或 Mfc 擴充 dll。 如需詳細資訊，請參閱[管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)。

如需如何撰寫、建立和使用一般 MFC DLL 的範例，請參閱範例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。 如需動態連結至 MFC 之一般 MFC Dll 的詳細資訊，請參閱範例的抽象概念中的「將 DLLScreenCap 轉換為以動態方式連結 MFC DLL」一節。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [初始化一般 MFC Dll](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [動態連結至 MFC 之一般 MFC DLL 的模組狀態](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

- [在一般 MFC Dll 中使用資料庫、OLE 和通訊端 MFC 延伸 Dll](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [將 MFC 當做 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>請參閱

[DLL 的種類](kinds-of-dlls.md)
