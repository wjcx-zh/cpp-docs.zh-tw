---
title: 擴充 DLL
ms.date: 11/04/2016
f1_keywords:
- afxdll
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
ms.openlocfilehash: 2d9b23871cedd93c4145c79d2c22240b9ae2e775
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429233"
---
# <a name="mfc-extension-dlls"></a>MFC 擴充 Dll

MFC 擴充 DLL 是 DLL，通常會實作衍生自現有 Mfc 程式庫類別的可重複使用類別。

MFC 擴充 DLL 具有下列功能和需求：

- 用戶端可執行檔必須是 MFC 應用程式編譯`_AFXDLL`定義。

- 動態連結至 MFC 之標準 MFC DLL 可以也使用 MFC 擴充 DLL。

- MFC 擴充 Dll 應該使用編譯`_AFXEXT`定義。 這會強制`_AFXDLL`也定義，並確保適當的宣告，從 MFC 標頭檔提取。 它也可確保`AFX_EXT_CLASS`定義為`__declspec(dllexport)`同時建置的 DLL，這是必要條件，如果您使用這個巨集來宣告在您的 MFC 擴充 DLL 中的類別。

- MFC 擴充 Dll 應該具現化類別，衍生自`CWinApp`，但應依賴用戶端應用程式 （或 DLL），來提供這個物件。

- MFC 擴充 Dll 應該不過，提供`DllMain`函式，並進行必要初始化那里。

擴充 Dll 是建置使用 MFC （也稱為 MFC 的共用版本） 的動態連結程式庫版本。 只有 MFC 可執行檔 （應用程式或 MFC 的標準 Dll） 建立的 MFC 的共用版本可以使用 MFC 擴充 DLL。 用戶端應用程式和 MFC 擴充 DLL 必須使用相同版本的 MFCx0.dll。 使用 MFC 擴充 DLL，您可以從 MFC 衍生新的自訂類別，並接著提供這個擴充的版本的 MFC 呼叫 DLL 的應用程式。

擴充 Dll 也可用來傳遞應用程式和 DLL 之間的 MFC 衍生的物件。 傳遞的物件相關聯的成員函式會存在於物件建立所在的模組。 因為使用共用的 MFC 的 DLL 版本時，這些函式會正確匯出，您可以自由地傳遞 MFC 或 MFC 延伸模組載入的 Dll 和應用程式之間的 MFC 衍生的物件指標。

MFC 擴充 DLL 會使用共用的版本的 MFC 應用程式會使用共用的 MFC 的 DLL 版本，與一些其他考量的方式相同：

- 它並沒有`CWinApp`-衍生物件。 它必須使用`CWinApp`-衍生的用戶端應用程式的物件。 這表示用戶端應用程式擁有的主要訊息幫浦，閒置迴圈，依此類推。

- 它會呼叫`AfxInitExtensionModule`在其`DllMain`函式。 應檢查此函式的傳回值。 如果從傳回值為零`AfxInitExtensionModule`，會傳回 0，從您`DllMain`函式。

- 它會建立**CDynLinkLibrary**物件在初始化期間，如果 MFC 擴充 DLL 所要匯出`CRuntimeClass`物件或應用程式的資源。

之前版本的 MFC 4.0，這種類型的 DLL 呼叫 AFXDLL。 AFXDLL 指`_AFXDLL`建置 DLL 時定義的前置處理器符號。

MFC 的共用版本的匯入程式庫會根據所述的慣例命名[MFC Dll 命名慣例](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)。 Visual c + + 提供預先建置的版本，MFC Dll，再加上數字的非 MFC Dll，您可以使用並與您的應用程式一起散發。 這些會記載於 Redist.txt，其會安裝到 Program Files\Microsoft Visual Studio 資料夾。

如果您要匯出使用.def 檔，將下列程式碼的開頭和結尾標頭檔：

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

這四行，請確定您的程式碼正確編譯 MFC 擴充 DLL。 離開這四行程式碼可能會導致您編譯或連結不正確的 DLL。

如果您需要傳遞 MFC 或 MFC 衍生的物件指標，或從 MFC DLL，DLL 應該是 MFC 擴充 DLL。 傳遞的物件相關聯的成員函式會存在於物件建立所在的模組。 因為使用共用的 MFC 的 DLL 版本時，這些函式會正確匯出，您可以自由地傳遞 MFC 或 MFC 延伸模組載入的 Dll 和應用程式之間的 MFC 衍生的物件指標。

由於 c + + 名稱的損害以及匯出的問題，[匯出] 清單，從 MFC 延伸模組 DLL 可能會不同相同 DLL 的偵錯和零售版本和 Dll 之間不同平台。 零售 MFCx0.dll 有大約 2000 匯出的進入點，偵錯 MFCx0D.dll 有大約 3,000 已匯出的進入點。

## <a name="memory-management"></a>記憶體管理

MFCx0.dll 和 Dll 載入到用戶端應用程式的位址空間的所有 MFC 延伸模組使用相同的記憶體配置器、 資源載入和其他 MFC 全域狀態，如同它們是相同的應用程式。 這十分重要，因為非 MFC DLL 程式庫和標準 MFC Dll 執行完全相反的且有移出它自己的記憶體集區每個配置的 DLL。

如果 MFC 擴充 DLL 中配置記憶體，記憶體可以自由地相互摻雜與其他應用程式配置的物件。 此外，如果動態連結至 MFC 的應用程式失敗，作業系統的保護會維護共用 DLL 任何其他 MFC 應用程式的完整性。

同樣的其他全域的 MFC 狀態，例如目前的可執行檔載入資源，也會共用用戶端應用程式和所有 MFC 擴充 Dll，以及 MFCx0.dll 本身之間。

## <a name="sharing-resources-and-classes"></a>共用資源和類別

匯出資源是透過資源的清單。 每個應用程式包含的單向連結的清單**CDynLinkLibrary**物件。 大部分的標準的 MFC 實作載入資源時尋找資源，尋找第一個在目前的資源模組 (`AfxGetResourceHandle`)，如果找不到時逐步清單**CDynLinkLibrary**物件嘗試載入要求的資源。

逐一查看清單也有缺點，它會稍微慢一點，而且需要管理資源 ID 範圍。 它的優點是連結到數個 MFC 擴充 Dll 用戶端應用程式可以使用任何提供 DLL 的資源，而不需要指定 DLL 的執行個體控制代碼。 `AfxFindResourceHandle` API 用於逐一查看 [資源] 清單，尋找指定的相符項。 它會使用名稱和資源類型，並傳回其第一次發現所在的資源控制代碼 （或 NULL）。

如果您不想要逐步清單，並只從特定位置載入資源，請使用函式`AfxGetResourceHandle`和`AfxSetResourceHandle`儲存舊的控制代碼，並設定新的控制代碼。 請務必還原舊的資源控制代碼，然後返回用戶端應用程式。 若要明確載入功能表使用這個方法的範例，請參閱 MFC 範例中的 Testdll2.cpp [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。

動態建立 MFC 物件提供 MFC 名稱很類似。 MFC 物件還原序列化機制必須將所有`CRuntimeClass`物件註冊，讓它可以藉由以動態方式建立所需的型別，根據儲存的內容稍早的 c + + 物件建構。

在 MFC 範例的情況下[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)，清單看起來像：

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

何處*xx*是版本號碼; 比方說，42 代表 4.2 版。

MFCxx.dll 是根據資源和類別清單，通常是最後一個項目。 MFCxx.dll 包含所有的標準 MFC 資源，包括所有標準命令 Id 的提示字串。 將它放在清單結尾處，可讓 Dll 和用戶端應用程式本身不具有自己的標準 MFC 資源中，複本，但改為依賴 MFCxx.dll 中的共用資源。

合併入用戶端應用程式的命名空間的資源和類別名稱的所有 Dll 的缺點是需要您注意 Id 或您選擇的名稱。

[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)範例使用多個標頭檔來管理共用的資源命名空間。

如果您的 MFC 擴充 DLL 需要維護額外的資料，每個應用程式，您可以衍生新的類別，從**CDynLinkLibrary** ，然後建立它在`DllMain`。 DLL 執行時，可以檢查目前的應用程式清單**CDynLinkLibrary**來找出該特定的 MFC 延伸模組 DLL 的物件。

### <a name="what-do-you-want-to-do"></a>請您指定選項。

- [初始化 MFC 擴充 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [使用共用的資源檔的秘訣](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)

- [靜態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [在 MFC DLL 中使用資料庫、OLE 和通訊端 MFC 延伸模組 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)