---
title: TN011:將 MFC 當成 DLL 的一部分來使用
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 753612fae101708dd4f8294db121980b62af30b3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65610958"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011:將 MFC 當成 DLL 的一部分來使用

此提示說明標準 MFC Dll，可以讓您使用 MFC 程式庫做為 Windows 動態連結程式庫 (DLL) 的一部分。 它假設您熟悉 Windows DLL 並知道如何建置它們。 如需詳細資訊 MFC 擴充 Dll，您可以建立使用 MFC 程式庫中，延伸模組[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)。

## <a name="dll-interfaces"></a>DLL 介面

MFC 的標準 Dll 假設類似 C 的函式或明確匯出的類別中指定應用程式和 DLL 之間的介面。 MFC 類別介面無法匯出。

如果 DLL 和應用程式都要使用 MFC，二者均可選擇要使用共用版本的 MFC 程式庫或靜態地連結至程式庫的複本。 應用程式和 DLL 可能都使用其中一個標準版本的 MFC 程式庫。

MFC 的標準 Dll 中有幾項優點：

- 使用 DLL 的應用程式不一定要使用 MFC，而且不一定要是 Visual C++ 應用程式。

- 使用以靜態方式連結至 MFC 的標準 MFC Dll，DLL 的大小只會視 MFC 和 C 執行階段常式所使用和連結。

- 動態連結至 MFC 的標準 MFC dll，節省的記憶體使用 MFC 的共用的版本很可觀。 不過，您必須將發佈共用的 Dll、 Mfc\<*版本*>.dll 和 Msvvcrt\<*版本*>.dll，與您的 DLL。

- DLL 的設計與如何實作類別無關。 您的 DLL 設計只會匯出至您要的 API。 如此一來，如果實作變更，MFC 的標準 Dll 都仍然有效。

- 若是靜態連結至 MFC 的標準 MFC dll 如果 DLL 和應用程式使用 MFC，有沒有想 MFC DLL 或反之亦然的不同版本的應用程式的問題。 因為 MFC 程式庫是靜態連結至每個 DLL 或 EXE，所以您擁有什麼版本並不會造成任何問題。

## <a name="api-limitations"></a>API 限制

部分 MFC 功能會因為技術上的限制，或是因為這些服務通常由應用程式提供，而不適用於 DLL 版本。 若是目前版本的 MFC，唯一不適用的函式是 `CWinApp::SetDialogBkColor`。

## <a name="building-your-dll"></a>建置 DLL

當編譯靜態連結至 MFC，符號的標準 MFC Dll`_USRDLL`和`_WINDLL`必須定義。 您的 DLL 程式碼也必須使用下列編譯器參數進行編譯：

- **/ D_WINDLL**表示編譯的 dll 是

- **/ D_USRDLL**指定您要建置 MFC DLL

您也必須定義這些符號，並使用這些編譯器參數，當您編譯動態連結至 MFC 的標準 MFC Dll。 此外，符號 `_AFXDLL` 必須加以定義，而且您的 DLL 程式碼必須使用下列項目進行編譯：

- **/ D_AFXDLL**指定您要建置動態連結至 MFC 之標準 MFC DLL

應用程式和 DLL 之間的介面 (API) 必須明確地匯出。 建議您定義介面為低頻寬，並且可以的話只使用 C 介面。 直接 C 介面比較複雜的 C++ 類別容易維護。

將 API 放在 C 和 C++ 檔案都可包含的個別標頭中。 請參閱 MFC 進階概念範例中的標頭 ScreenCap.h [DLLScreenCap](../overview/visual-cpp-samples.md)的範例。 若要匯出函式，請在您的模組定義檔 (.DEF) 的 `EXPORTS` 區段中輸入那些函式，或者在您的函式定義包括 `__declspec(dllexport)`。 使用 `__declspec(dllimport)` 將這些函式匯入用戶端可執行檔。

您必須新增 AFX_MANAGE_STATE 巨集的動態連結至 MFC 的標準 MFC Dll 中匯出的函式的開頭。 這個巨集會將目前的模組狀態設定為 DLL 的狀態。 若要使用這個巨集，請將以下程式碼行加入至從 DLL 匯出的函式開頭：

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

MFC 程式庫定義標準 Win32`DllMain`進入點，以初始化您[CWinApp](../mfc/reference/cwinapp-class.md)衍生物件，如同一般的 MFC 應用程式。 將所有 DLL 特定的初始化[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)如同一般的 MFC 應用程式的方法。

請注意， [cwinapp:: Run](../mfc/reference/cwinapp-class.md#run)機制不會套用到 DLL，因為應用程式擁有的主要訊息幫浦。 如果您的 DLL 顯示非強制回應對話方塊，或具有自己的主框架視窗，您的應用程式的主要訊息幫浦必須呼叫所呼叫的 DLL 匯出常式[CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage)。

有關這個函式的使用，請參閱 DLLScreenCap 範例。

`DllMain` MFC 提供了將呼叫的函式[CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)類別衍生自方法`CWinApp`卸載 DLL 之前。

## <a name="linking-your-dll"></a>連結您的 DLL

以靜態方式連結至 MFC 的標準 MFC dll，您必須連結您的 DLL 和 Nafxcwd.lib 或者連結 Nafxcw.lib 和具名為 Libcmt.lib 的 C 執行階段版本。 這些程式庫為預先建置，並且可以透過在執行 Visual C++ 設定時進行指定來加以安裝。

## <a name="sample-code"></a>程式碼範例

如需完整的範例，請參閱 MFC 進階概念範例程式 DLLScreenCap。 此範例中的提示有以下幾點注意事項：

- DLL 的編譯器旗標和應用程式的編譯器旗標不同。

- DLL 的連結程式行和 .DEF 檔和應用程式的連結程式行和 .DEF 檔不同。

- 使用 DLL 的應用程式不一定要在 C++ 中。

- 應用程式和 DLL 之間的介面是可由 C 或 C++ 使用的 API，並且使用 DLLScreenCap.def 匯出。

下列範例說明在一般 MFC 靜態連結至 MFC 的 DLL 中定義的 API。 在此範例中，宣告是括在 C++ 使用者的 `extern "C" { }` 區塊中。 這有幾項優點。 首先，它可讓非 C++ 用戶端應用程式也能夠使用您的 DLL API。 第二，它降低了 DLL 的額外負荷，因為 C++ 名稱重整 (Name Mangling) 不會套用至已匯出的名稱。 最後，它可讓您更易明確地加入至 .DEF 檔案 (以便於依序匯出)，而不需要擔心名稱修飾。

```
#ifdef __cplusplus
extern "C" {
#endif  /* __cplusplus */

struct TracerData
{
    BOOL bEnabled;
    UINT flags;
};

BOOL PromptTraceFlags(TracerData FAR* lpData);

#ifdef __cplusplus
}
#endif
```

API 所使用的結構不是從 MFC 類別衍生，而是在 API 標頭中定義。 這可減少 DLL 和應用程式之間介面的複雜度，並讓 C 程式能夠使用 DLL。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
