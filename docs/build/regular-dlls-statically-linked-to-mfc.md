---
title: 靜態連結至 MFC 的標準 MFC Dll
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 074cd6c9fca08261cf2333a968dce3cc83c0c860
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415979"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>靜態連結至 MFC 的標準 MFC Dll

MFC DLL 以靜態方式連結至 MFC 一般是在內部使用 MFC 的 DLL，而且在 DLL 中匯出的函式可以呼叫由 MFC 或非 MFC 可執行檔。 如名稱所述，這類型的 DLL 是使用 MFC 靜態連結程式庫版本。 通常與一般使用 C 介面的標準 MFC DLL 匯出函式。 如需如何撰寫、 建置及使用 MFC 的標準 DLL 的範例，請參閱範例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。

請注意，詞彙 USRDLL 不再使用 Visual c + + 文件中。 靜態連結至 MFC 之標準 MFC DLL 有相同的特性，與之前的 usrdll。

MFC DLL，以靜態方式連結至 MFC，具有下列功能：

- 可執行的用戶端可以使用任何支援 Dll （C、 c + +、 Pascal、 Visual Basic 中，依此類推）; 使用的語言撰寫它並沒有是一個 MFC 應用程式。

- DLL 可以連結至應用程式所使用的相同 MFC 靜態連結程式庫。 不再是靜態連結程式庫，適用於 Dll 的另一個版本。

- 之前版本的 MFC 4.0，Usrdll 會提供相同的型別與靜態連結至 MFC 的標準 MFC Dll 的功能。 截至 Visual c + + 4.0 版，詞彙 USRDLL 已經過時。

靜態連結至 MFC 之標準 MFC DLL 必須符合下列需求：

- 這種類型的 DLL 必須具現化類別，衍生自`CWinApp`。

- 這種類型的 DLL 會使用`DllMain`MFC 提供。 將所有的特定 DLL 的初始化程式碼中放`InitInstance`成員函式和終止程式碼中的`ExitInstance`如同正常的 MFC 應用程式。

- 即使一詞 USRDLL 已經過時，您仍然必須定義 」**_USRDLL**「 編譯器命令列上。 此定義會決定哪些宣告從 MFC 標頭檔提取。

MFC 的標準 Dll 必須`CWinApp`-衍生類別，該應用程式類別的單一物件，MFC 應用程式一樣。 不過， `CWinApp` DLL 的物件沒有的主要訊息幫浦，如同`CWinApp`應用程式的物件。

請注意，`CWinApp::Run`機制不會套用到 DLL，因為應用程式擁有的主要訊息幫浦。 如果 DLL 開啟非強制回應對話方塊，或有自己的主框架視窗，應用程式的主要訊息幫浦就必須呼叫接著會呼叫的 dll 匯出常式`CWinApp::PreTranslateMessage`DLL 的應用程式物件的成員函式。

如需此函式的範例，請參閱 DLLScreenCap 範例。

一般 MFC DLL 使用標準的 C 介面，通常被匯出符號。 從 MFC DLL 匯出函式的宣告看起來像這樣：

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

MFC DLL 內的所有記憶體配置都應該都留在該 DLL;DLL 不應該傳遞至或接收呼叫的可執行檔從下列其中一項：

- MFC 物件的指標

- MFC 所配置的記憶體的指標

如果您需要進行上述任一種，或要呼叫的可執行檔和 DLL 之間傳遞 MFC 衍生的物件，您必須建置 MFC 擴充 DLL。

它是只有當您建立一份資料時，將指標傳遞到所配置的記憶體的 C 執行階段程式庫的應用程式和 DLL 之間的安全。 您必須刪除或調整這些指標的大小或使用它們，而建立複本的記憶體。

靜態連結至 MFC 的 DLL 也會動態地無法連結至共用 MFC Dll 中。 靜態連結至 MFC 的 DLL 動態繫結至的應用程式，就像任何其他 DLL;應用程式連結，就像任何其他 DLL。

標準的 MFC 靜態連結程式庫會根據所述的慣例命名[MFC Dll 命名慣例](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)。 不過，mfc 3.0 版和更新版本，它不再需要手動指定連結器要在連結的 MFC 程式庫版本。 相反地，MFC 標頭檔會自動判斷正確版本的 MFC 程式庫，若要連結在根據前置處理器定義，例如**\_偵錯**或是 **_UNICODE**。 MFC 標頭檔新增 /DEFAULTLIB 指示詞，指示連結器連結特定版本的 MFC 程式庫。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [初始化 MFC 的標準 Dll](../build/run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [將 MFC 當成 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [在 MFC DLL 中使用資料庫、OLE 和通訊端 MFC 延伸模組 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [建立 MFC DLL](../mfc/reference/mfc-dll-wizard.md)

- [動態連結至 MFC 的標準 MFC DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL](../build/extension-dlls-overview.md)

## <a name="see-also"></a>另請參閱

[DLL 的種類](../build/kinds-of-dlls.md)
