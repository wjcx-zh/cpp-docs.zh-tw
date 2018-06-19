---
title: 擴充 Dll |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afxdll
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f60540735be44adf4305dcda77373faf8a83514
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377127"
---
# <a name="mfc-extension-dlls"></a>MFC 擴充 Dll
MFC 擴充 DLL 是通常會實作可重複使用的類別衍生自現有 Mfc 程式庫的 DLL。  
  
 MFC 擴充 DLL 具有下列功能和需求：  
  
-   用戶端可執行檔必須以編譯 MFC 應用程式`_AFXDLL`定義。  
  
-   MFC 擴充 DLL 也可供動態連結至 MFC 之標準 MFC DLL。  
  
-   MFC 擴充 Dll 必須以編譯`_AFXEXT`定義。 這會強制`_AFXDLL`也定義，並確保適當的宣告提取從 MFC 標頭檔。 它也可以確保`AFX_EXT_CLASS`定義為`__declspec(dllexport)`時建置 DLL，而這是必要，如果您使用這個巨集來宣告在您的 MFC 擴充 DLL 中的類別。  
  
-   MFC 擴充 Dll 應該不具現化類別衍生自`CWinApp`，但應該依賴用戶端應用程式 （或 DLL），以提供此物件。  
  
-   不過，應該提供 MFC 擴充 Dll`DllMain`函式，並進行任何必要的初始化發生。  
  
 擴充 Dll 會使用 MFC （也稱為 MFC 的共用版本） 的動態連結程式庫版本建立。 只有 MFC 可執行檔 （應用程式或 MFC 的標準 Dll） 所建置的 MFC 的共用版本可以使用 MFC 擴充 DLL。 用戶端應用程式和 MFC 擴充 DLL 必須使用相同版本的 MFCx0.dll。 使用 MFC 擴充 DLL，可以從 MFC 衍生新的自訂類別，然後提供這個擴充的版本的 MFC 應用程式呼叫 DLL。  
  
 擴充 Dll 也可以用於應用程式和 DLL 之間傳遞 MFC 衍生的物件。 傳入物件相關聯的成員函式存在於物件建立所在的模組。 因為使用共用的 MFC 的 DLL 版本時，這些函式會正確匯出，您可以自由地傳遞 MFC 或應用程式與 MFC 擴充 Dll 載入之間的 MFC 衍生物件指標。  
  
 MFC 擴充 DLL 使用共用的版本的 MFC 應用程式會使用共用的 MFC 的 DLL 版本，與一些其他考量的方式相同：  
  
-   它並沒有`CWinApp`-衍生物件。 必須使用`CWinApp`-衍生的用戶端應用程式的物件。 這表示用戶端應用程式擁有主要訊息幫浦，閒置迴圈，以及等等。  
  
-   它會呼叫`AfxInitExtensionModule`中其`DllMain`函式。 應該檢查此函式的傳回值。 如果為零的值會傳回從`AfxInitExtensionModule`，傳回從 0 您`DllMain`函式。  
  
-   它會建立**CDynLinkLibrary**物件初始化期間，如果 MFC 擴充 DLL 想要匯出`CRuntimeClass`物件或應用程式的資源。  
  
 4.0 版之前的 MFC，這種類型的 DLL 呼叫 AFXDLL。 AFXDLL 指`_AFXDLL`建置 DLL 時，會定義的前置處理器符號。  
  
 MFC 的共用版本的匯入程式庫會根據中所述的慣例來命名[MFC Dll 命名慣例](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)。 Visual c + + 會提供預先建立的版本的 MFC Dll，再加上數字的非 MFC Dll，您可以使用並與您的應用程式一起散發。 這些案例記載 Redist.txt，其會安裝到 Program Files\Microsoft Visual Studio 資料夾中。  
  
 如果您要匯出使用.def 檔，將下列程式碼放在開頭和結尾的標頭檔：  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 這四行，確保您的程式碼正確編譯 MFC 擴充 DLL。 遺漏這些四行可能會導致您編譯或連結不正確的 DLL。  
  
 如果您需要將 MFC 或 MFC 衍生的物件指標，或從 MFC DLL，DLL 應該是 MFC 擴充 DLL。 傳入物件相關聯的成員函式存在於物件建立所在的模組。 因為使用共用的 MFC 的 DLL 版本時，這些函式會正確匯出，您可以自由地傳遞 MFC 或應用程式與 MFC 擴充 Dll 載入之間的 MFC 衍生物件指標。  
  
 由於 c + + 名稱修飾 （name-mangling） 和匯出問題，[匯出] 清單，從 MFC 擴充 DLL 可能會不同相同 DLL 的偵錯和零售版本和 Dll 之間不同平台。 零售 MFCx0.dll 有大約 2000 匯出進入點。偵錯 MFCx0D.dll 有大約 3000 匯出的項目點。  
  
## <a name="memory-management"></a>記憶體管理  
 MFCx0.dll 和所有的 MFC 擴充 Dll 載入到用戶端應用程式的位址空間使用相同的記憶體配置器、 資源載入和其他 MFC 全域狀態，如同它們是相同的應用程式中。 因為非 MFC DLL 程式庫和 MFC 的標準 Dll 則完全相反，而且有它自己的記憶體集區超出每個 DLL 配置，這十分重要。  
  
 如果 MFC 擴充 DLL 配置記憶體，記憶體可以自由地混合與其他應用程式配置的物件。 此外，如果動態連結至 MFC 的應用程式失敗，作業系統保護會維護其他任何 MFC 應用程式共用 DLL 的完整性。  
  
 同樣地其他全域 MFC 狀態，例如目前的可執行檔載入資源，也會用戶端應用程式和所有 MFC 擴充 Dll，以及 MFCx0.dll 本身之間共用。  
  
## <a name="sharing-resources-and-classes"></a>共用資源和類別  
 匯出資源是透過資源的清單。 每個應用程式包含單向連結的清單**CDynLinkLibrary**物件。 大部分的載入資源的標準 MFC 實作資源時，尋找在目前的資源模組的第一個 (`AfxGetResourceHandle`)，如果資源找不到查核清單**CDynLinkLibrary**物件嘗試載入要求的資源。  
  
 查核清單有缺點，它會稍微慢一點，而且必須管理資源 ID 範圍。 它的優點是連結到數個 MFC 擴充 Dll 的用戶端應用程式可以使用任何提供 DLL 的資源，而不需要指定 DLL 的執行個體控制代碼。 `AfxFindResourceHandle` API 用查核資源清單來查詢給定的相符項目。 它會使用名稱和資源類型，並傳回其第一次找到的資源控制代碼 （或 NULL）。  
  
 如果您不希望查核清單，並只從特定位置中載入資源，使用函數`AfxGetResourceHandle`和`AfxSetResourceHandle`儲存舊的控制代碼，並將新的控制代碼。 請務必還原舊的資源控制代碼傳回至用戶端應用程式之前。 使用這個方法來明確載入功能表的範例，請參閱 MFC 範例 Testdll2.cpp [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。  
  
 相似的動態建立 MFC 物件授與 MFC 的名稱。 MFC 物件還原序列化機制需要將所有`CRuntimeClass`登錄，讓它可以藉由動態建立 c + + 物件的所需的類型，根據項目先前已儲存重新建構的物件。  
  
 在 MFC 範例的情況下[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)，清單看起來像這樣：  
  
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
  
 其中*xx*是版本號碼; 例如，42 代表 4.2 版。  
  
 MFCxx.dll 是根據資源和類別清單通常是最後一個項目。 MFCxx.dll 包括所有標準 MFC 資源，包括所有標準命令 Id 的提示字串。 將它放在清單的結尾，可讓 Dll 和用戶端應用程式本身未擁有其自己的標準 MFC 資源的複本，但改為依賴 MFCxx.dll 中的共用資源。  
  
 合併入用戶端應用程式的命名空間的資源和類別名稱的所有 Dll 缺點是需要您特別注意 Id 或您選擇的名稱。  
  
 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)範例使用多個標頭檔來管理共用的資源命名空間。  
  
 如果您的 MFC 擴充 DLL，需要維護額外的資料，每個應用程式，您可以衍生新類別從**CDynLinkLibrary**並建立在`DllMain`。 DLL 執行時，可以檢查目前的應用程式清單**CDynLinkLibrary**来找到該特定 MFC 擴充 DLL 的物件。  
  
### <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [初始化 MFC 擴充 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [使用共用的資源檔的秘訣](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
  
-   [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
  
-   [以靜態方式連結至 MFC 的標準 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [在 MFC DLL 中使用資料庫、OLE 和通訊端 MFC 延伸模組 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)