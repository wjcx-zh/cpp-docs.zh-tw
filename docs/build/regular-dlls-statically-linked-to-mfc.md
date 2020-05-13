---
title: 靜態連結至 MFC 的標準 MFC DLL
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 1f05b5e3c268935cf3161fb7184e04b3e3ea1446
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314776"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>靜態連結至 MFC 的標準 MFC DLL

以靜態方式連結至 MFC 的標準 MFC DLL 是在內部使用 MFC 的 DLL，而 DLL 中匯出的函式可以由 MFC 或非 MFC 可執行檔呼叫。 如名稱所述，這種 DLL 是使用 MFC 的靜態程式庫版本所建立的。 函式通常會使用標準 C 介面從一般 MFC DLL 匯出。 如需如何撰寫、建立和使用一般 MFC DLL 的範例，請參閱範例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。

請注意，Visual C++ 檔中不再使用「USRDLL」一詞。 以靜態方式連結至 MFC 的一般 MFC DLL 與先前的 USRDLL 具有相同的特性。

以靜態方式連結至 MFC 的標準 MFC DLL 具有下列功能：

- 用戶端可執行檔可使用任何支援 Dll （C、c + +、Pascal、Visual Basic 等）的語言來撰寫;它不一定要是 MFC 應用程式。

- DLL 可以連結至應用程式所使用的相同 MFC 靜態程式庫。 Dll 已不再有個別的靜態程式庫版本。

- 在4.0 版的 MFC 之前，USRDLLs 提供了與以靜態方式連結至 MFC 的一般 MFC Dll 相同的功能類型。 從 Visual C++ 版本4.0，USRDLL 一詞已經過時。

以靜態方式連結至 MFC 的標準 MFC DLL 具有下列需求：

- 這種類型的 DLL 必須具現化衍生`CWinApp`自的類別。

- 這種類型的 DLL 會`DllMain`使用 MFC 所提供的。 將所有 DLL 特定的初始化程式碼放`InitInstance`在成員函式中， `ExitInstance`並在中終止程式碼，如同在一般 MFC 應用程式中一樣。

- 雖然 USRDLL 一詞已過時，但您仍然必須在編譯器命令列上定義 "**_USRDLL**"。 這個定義會決定從 MFC 標頭檔中提取的宣告。

一般 MFC Dll 必須擁有`CWinApp`衍生類別和該應用程式類別的單一物件，如同 MFC 應用程式一樣。 不過，DLL `CWinApp`的物件沒有主要的訊息提取，如同應用程式的`CWinApp`物件。

請注意， `CWinApp::Run`此機制不會套用至 DLL，因為應用程式會擁有主要的訊息提取。 如果 DLL 開啟非強制回應對話方塊，或有自己的主框架視窗，則應用程式的主要訊息提取必須呼叫 DLL 所匯出的常式，然後再呼叫 DLL 的`CWinApp::PreTranslateMessage`應用程式物件的成員函式。

如需此函式的範例，請參閱 DLLScreenCap 範例。

通常會使用標準 C 介面從一般 MFC DLL 匯出符號。 從一般 MFC DLL 匯出的函式宣告看起來會像這樣：

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

一般 MFC DLL 內的所有記憶體配置都應該留在 DLL 內;DLL 不應傳遞至呼叫的可執行檔，或從下列任一項接收：

- MFC 物件的指標

- MFC 所配置之記憶體的指標

如果您需要執行上述任一項，或需要在呼叫可執行檔和 DLL 之間傳遞 MFC 衍生的物件，您必須建立 MFC 擴充 DLL。

只有當您複製資料時，才可以將指標傳遞給應用程式和 DLL 之間的 C 執行時間程式庫所配置的記憶體。 您不能刪除或調整這些指標的大小，也不能在不建立記憶體複本的情況下使用它們。

以靜態方式連結至 MFC 的 DLL，也無法動態連結至共用的 MFC Dll。 以靜態方式連結至 MFC 的 DLL 會以動態方式系結至應用程式，就像任何其他 DLL 一樣。應用程式會連結到它，就像任何其他 DLL 一樣。

標準 MFC 靜態程式庫會根據[MFC dll 的命名慣例](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)中所述的慣例來命名。 不過，使用 MFC 版本3.0 和更新版本時，您不再需要手動指定連結器所要連結的 MFC 程式庫版本。 相反地，mfc 標頭檔會根據預處理器定義（例如** \_DEBUG**或 **_UNICODE**），自動決定要連結的 mfc 程式庫正確版本。 MFC 標頭檔會新增/DEFAULTLIB 指示詞，指示連結器連結至特定版本的 MFC 程式庫。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [初始化一般 MFC Dll](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [將 MFC 當做 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [在一般 MFC Dll 中使用資料庫、OLE 和通訊端 MFC 延伸 Dll](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [建立 MFC DLL](../mfc/reference/mfc-dll-wizard.md)

- [動態連結至 MFC 的標準 MFC Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 擴充 Dll](extension-dlls-overview.md)

## <a name="see-also"></a>請參閱

[DLL 的種類](kinds-of-dlls.md)
