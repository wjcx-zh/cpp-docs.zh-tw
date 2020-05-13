---
title: 擴充 DLL
ms.date: 05/06/2019
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
ms.openlocfilehash: 55b1e55a9c7bdf6daaff98a7fe3f1a2a55f68334
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220771"
---
# <a name="mfc-extension-dlls"></a>MFC 延伸模組 DLL

MFC 擴充 DLL 是一個 DLL，通常會執行衍生自現有 MFC 程式庫類別的可重複使用類別。

MFC 擴充 DLL 具有下列功能和需求：

- 用戶端可執行檔必須是以定義的`_AFXDLL`編譯的 MFC 應用程式。

- MFC 擴充 DLL 也可以由動態連結至 MFC 的一般 MFC DLL 使用。

- MFC 擴充 Dll 應使用已定義`_AFXEXT`的進行編譯。 這會`_AFXDLL`強制同時定義，並確保從 MFC 標頭檔中提取適當的宣告。 它也可確保`AFX_EXT_CLASS`在建立 DLL `__declspec(dllexport)`時定義為，如果您使用這個宏來宣告 MFC 擴充 DLL 中的類別，這就是必要的。

- MFC 擴充 Dll 不應該具現化衍生自`CWinApp`的類別，但應依賴用戶端應用程式（或 DLL）來提供此物件。

- 不過，MFC 延伸 Dll 應該提供函式`DllMain` ，並在該處執行任何必要的初始化。

擴充 Dll 是使用 MFC 的動態連結程式庫版本（也稱為 MFC 的共用版本）所建立。 只有以共用版本的 MFC 建立的 MFC 可執行檔（應用程式或一般 MFC Dll），才可以使用 MFC 擴充 DLL。 用戶端應用程式和 MFC 延伸模組 DLL 都必須使用相同版本的 MFCx0。 有了 MFC 延伸 DLL，您就可以從 MFC 衍生新的自訂類別，然後將這個擴充版本的 MFC 提供給呼叫您 DLL 的應用程式。

擴充 Dll 也可以用來在應用程式和 DLL 之間傳遞 MFC 衍生的物件。 與傳遞物件相關聯的成員函式存在於建立物件的模組中。 當使用 MFC 的共用 DLL 版本時，這些函式會正確匯出，因此您可以在應用程式和它所載入的 MFC 延伸 Dll 之間，自由地傳遞 MFC 或 MFC 衍生的物件指標。

MFC 擴充 DLL 使用 mfc 的共用版本，就像應用程式使用 MFC 的共用 DLL 版本一樣，還有一些額外的考慮：

- 它沒有衍生的`CWinApp`物件。 它必須使用用戶端`CWinApp`應用程式的衍生物件。 這表示用戶端應用程式擁有主要訊息抽取、閒置迴圈等等。

- 它會`AfxInitExtensionModule`在其`DllMain`函式中呼叫。 應檢查此函式的傳回值。 如果從`AfxInitExtensionModule`傳回零值，則會從您`DllMain`的函式傳回0。

- 如果 MFC 延伸**CDynLinkLibrary**模組 DLL 想要將物件或資源匯出`CRuntimeClass`至應用程式，它會在初始化期間建立 CDynLinkLibrary 物件。

在 MFC 的4.0 版之前，這種類型的 DLL 稱為 AFXDLL。 AFXDLL 是指建立`_AFXDLL` DLL 時所定義的預處理器符號。

MFC 共用版本的匯入程式庫會根據[Mfc dll 的命名慣例](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)中所述的慣例來命名。 Visual Studio 提供預建的 MFC Dll 版本，再加上一些可供您用來與應用程式一起散發的非 MFC Dll。 這些檔會記錄在可轉散發的 .txt 中，其已安裝到 Program Files\Microsoft Visual Studio 資料夾。

如果您使用 .def 檔案進行匯出，請將下列程式碼放在標頭檔的開頭和結尾處：

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

這四行可確保您的程式碼已針對 MFC 延伸 DLL 正確編譯。 省略這四行可能會導致您的 DLL 不正確地編譯或連結。

如果您需要在 MFC DLL 之間傳遞 MFC 或 MFC 衍生的物件指標，則 DLL 應該是 MFC 擴充 DLL。 與傳遞物件相關聯的成員函式存在於建立物件的模組中。 當使用 MFC 的共用 DLL 版本時，這些函式會正確匯出，因此您可以在應用程式和它所載入的 MFC 延伸 Dll 之間，自由地傳遞 MFC 或 MFC 衍生的物件指標。

由於 c + + 名稱重整和匯出問題，在不同平臺的相同 DLL 和 Dll 的 debug 和零售版本之間，MFC 延伸模組 DLL 的匯出清單可能會不同。 零售 MFCx0 有大約2000個匯出的進入點;debug MFCx0D 有大約3000個匯出的進入點。

## <a name="memory-management"></a>記憶體管理

載入至用戶端應用程式的位址空間的 MFCx0 和所有 MFC 延伸 Dll，都會使用相同的記憶體配置器、資源載入和其他 MFC 全域狀態，如同它們是在相同的應用程式中。 這很重要，因為非 MFC DLL 程式庫和一般 MFC Dll 會執行完全相反的動作，並將每個 DLL 配置給它自己的記憶體集區。

如果 MFC 延伸模組 DLL 配置記憶體，則該記憶體可以自由地與任何其他應用程式佈建的物件混合。 此外，如果動態連結至 MFC 的應用程式失敗，作業系統的保護會維持共用 DLL 之任何其他 MFC 應用程式的完整性。

同樣地，其他全域 MFC 狀態（像是要從中載入資源的目前可執行檔）也會在用戶端應用程式和所有 MFC 延伸 Dll 以及 MFCx0 本身之間共用。

## <a name="sharing-resources-and-classes"></a>共用資源和類別

匯出資源是透過資源清單來完成。 每個應用程式都包含一份**CDynLinkLibrary**物件的單向連結清單。 尋找資源時，大部分載入資源的標準 MFC 執行會先在目前的資源模組（`AfxGetResourceHandle`）上進行檢查，如果找不到資源，則會引導**CDynLinkLibrary**物件清單嘗試載入要求的資源。

瀏覽清單的缺點是稍微慢一點，而且需要管理資源識別碼範圍。 其優點是連結至數個 MFC 擴充 Dll 的用戶端應用程式可以使用任何 DLL 提供的資源，而不需要指定 DLL 實例控制碼。 `AfxFindResourceHandle`是用來流覽資源清單以尋找指定相符的 API。 它會採用資源的名稱和類型，並傳回第一次找到它的資源控制碼（或 Null）。

如果您不想要逐步執行清單，並且只從特定位置載入資源，請使用函式`AfxGetResourceHandle`和`AfxSetResourceHandle`來儲存舊的控制碼，並設定新的控制碼。 回到用戶端應用程式之前，請務必還原舊的資源控制碼。 如需使用此方法來明確載入功能表的範例，請參閱 MFC 範例[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)中的 Testdll2。

提供 MFC 名稱的動態建立 MFC 物件類似。 MFC 物件還原序列化機制必須已註冊所有的`CRuntimeClass`物件，以便根據稍早儲存的內容，以動態方式建立所需類型的 c + + 物件，以便重建。

在 MFC 範例[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)的案例中，清單看起來會像這樣：

```
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE
               |                      |
          TESTDLL2.DLL           TESTDLL2.DLL
               |                      |
          TESTDLL1.DLL           TESTDLL1.DLL
               |                      |
           MFCOxxD.DLL                |
               |                      |
           MFCDxxD.DLL                |
               |                      |
            MFCxxD.DLL            MFCxx.DLL
```

其中*xx*是版本號碼;例如，42代表4.2 版。

MFCxx 通常是在資源和類別清單上的最後一個。 MFCxx 包含所有標準 MFC 資源，包括所有標準命令識別碼的提示字串。 將它放在清單結尾後，Dll 和用戶端應用程式本身就不會有自己的標準 MFC 資源複本，而是依賴 MFCxx 中的共用資源。

將所有 Dll 的資源和類別名稱合併到用戶端應用程式的命名空間，有個缺點，就是要求您小心選擇所挑選的識別碼或名稱。

[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)範例會使用多個標頭檔來管理共用資源命名空間。

如果您的 MFC 延伸模組 DLL 必須為每個應用程式維護額外的資料，您可以從**CDynLinkLibrary**衍生新的類別`DllMain`，並在中建立它。 執行時，DLL 可以檢查目前應用程式的**CDynLinkLibrary**物件清單，以找出該特定 MFC 延伸模組 DLL 的物件。

### <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [初始化 MFC 延伸模組 DLL](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [使用共用資源檔的秘訣](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)

- [靜態連結至 MFC 的標準 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [在一般 MFC Dll 中使用資料庫、OLE 和通訊端 MFC 延伸 Dll](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
