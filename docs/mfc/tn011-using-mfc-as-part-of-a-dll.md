---
title: TN011：將 MFC 當成 DLL 的一部分來使用
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 0f4d4e2ed76a0fa5f8f775345fc672a1df055a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370431"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011：將 MFC 當成 DLL 的一部分來使用

本說明介紹常規 MFC DLL,它允許您將 MFC 庫用作 Windows 動態連結庫 (DLL) 的一部分。 它假設您熟悉 Windows DLL 並知道如何建置它們。 有關 MFC 擴展 DLL 的資訊(您可以使用該擴展創建 MFC 庫,請參閱[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md))。

## <a name="dll-interfaces"></a>DLL 介面

常規 MFC DLL 假定應用程式之間的介面,DLL 在 C 樣的函數或顯式匯出的類中指定。 MFC 類別介面無法匯出。

如果 DLL 和應用程式都要使用 MFC，二者均可選擇要使用共用版本的 MFC 程式庫或靜態地連結至程式庫的複本。 應用程式和 DLL 可能都使用其中一個標準版本的 MFC 程式庫。

一般 MFC DLL 有幾個優點:

- 使用 DLL 的應用程式不一定要使用 MFC，而且不一定要是 Visual C++ 應用程式。

- 對於靜態連結到 MFC 的常規 MFC DLL,DLL 的大小僅取決於使用和連結的 MFC 和 C 運行時例程。

- 使用動態連結到 MFC 的常規 MFC DLL,使用 MFC 的共用版本可以節省記憶體。 但是,您必須將共用\<的 DLL、mfc*版本*>.dll 和\<msvvcrt*版本*>.dll 分發,並與您的 DLL 一起分發。

- DLL 的設計與如何實作類別無關。 您的 DLL 設計只會匯出至您要的 API。 因此,如果實現發生更改,常規 MFC DLL 仍然有效。

- 對於靜態連結到 MFC 的常規 MFC DLL,如果 DLL 和應用程式都使用 MFC,則應用程式不需要與 DLL 不同版本的 MFC 出現問題,反之亦然。 因為 MFC 程式庫是靜態連結至每個 DLL 或 EXE，所以您擁有什麼版本並不會造成任何問題。

## <a name="api-limitations"></a>API 限制

部分 MFC 功能會因為技術上的限制，或是因為這些服務通常由應用程式提供，而不適用於 DLL 版本。 若是目前版本的 MFC，唯一不適用的函式是 `CWinApp::SetDialogBkColor`。

## <a name="building-your-dll"></a>建置 DLL

編譯靜態連結到 MFC 的常規 MFC DLL`_USRDLL`時`_WINDLL`,必須定義 符號 和符號。 您的 DLL 程式碼也必須使用下列編譯器參數進行編譯：

- **/D_WINDLL**表示編譯用於 DLL

- **/D_USRDLL**指定您正在建構一般 MFC DLL

編譯動態連結到 MFC 的常規 MFC DLL 時,還必須定義這些符號並使用這些編譯器開關。 此外，符號 `_AFXDLL` 必須加以定義，而且您的 DLL 程式碼必須使用下列項目進行編譯：

- **/D_AFXDLL**指定您正在建構一個定期 MFC DLL,該 DLL 動態連結到 MFC

應用程式和 DLL 之間的介面 (API) 必須明確地匯出。 建議您定義介面為低頻寬，並且可以的話只使用 C 介面。 直接 C 介面比較複雜的 C++ 類別容易維護。

將 API 放在 C 和 C++ 檔案都可包含的個別標頭中。 有關示例,請參閱 MFC 高級概念範例[DLLScreenCap](../overview/visual-cpp-samples.md)中的頭 ScreenCap.h。 若要匯出函式，請在您的模組定義檔 (.DEF) 的 `EXPORTS` 區段中輸入那些函式，或者在您的函式定義包括 `__declspec(dllexport)`。 使用 `__declspec(dllimport)` 將這些函式匯入用戶端可執行檔。

您必須在定期 MFC DLL 中動態連結到 MFC 的所有匯出函數的開頭添加AFX_MANAGE_STATE宏。 這個巨集會將目前的模組狀態設定為 DLL 的狀態。 若要使用這個巨集，請將以下程式碼行加入至從 DLL 匯出的函式開頭：

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>溫曼 -> 德曼

MFC 庫定義標準 Win32`DllMain`入口點,該入口點將[CWinApp](../mfc/reference/cwinapp-class.md)派生物件初始化為典型 MFC 應用程式中。 將所有特定於 DLL 的初始化放在[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)方法中,如在典型的 MFC 應用程式中。

請注意[,CWinApp::運行](../mfc/reference/cwinapp-class.md#run)機制不適用於 DLL,因為應用程式擁有主消息泵。 如果您的 DLL 顯示無模式對話框或自己的主框架視窗,則應用程式的主訊息泵必須呼叫 DLL 匯出的例程,該例程稱為[CWinApp::P重新翻譯訊息](../mfc/reference/cwinapp-class.md#pretranslatemessage)。

有關這個函式的使用，請參閱 DLLScreenCap 範例。

MFC`DllMain`提供的 函數將調用類的[CWinApp::exitInstance](../mfc/reference/cwinapp-class.md#exitinstance)方法,該`CWinApp`方法派生自 DLL 之前。

## <a name="linking-your-dll"></a>連結您的 DLL

使用靜態連結到 MFC 的常規 MFC DLL,您必須將 DLL 與 Nafxcwd.lib 或 Nafxcw.lib 以及名為 Libcmt.lib 的 C 執行時版本連結。 這些程式庫為預先建置，並且可以透過在執行 Visual C++ 設定時進行指定來加以安裝。

## <a name="sample-code"></a>範例程式碼

如需完整的範例，請參閱 MFC 進階概念範例程式 DLLScreenCap。 此範例中的提示有以下幾點注意事項：

- DLL 的編譯器旗標和應用程式的編譯器旗標不同。

- DLL 的連結程式行和 .DEF 檔和應用程式的連結程式行和 .DEF 檔不同。

- 使用 DLL 的應用程式不一定要在 C++ 中。

- 應用程式和 DLL 之間的介面是可由 C 或 C++ 使用的 API，並且使用 DLLScreenCap.def 匯出。

下面的範例展示在常規 MFC DLL 中定義的 API,該 API 以靜態方式連結到 MFC。 在此範例中，宣告是括在 C++ 使用者的 `extern "C" { }` 區塊中。 這有幾項優點。 首先，它可讓非 C++ 用戶端應用程式也能夠使用您的 DLL API。 第二，它降低了 DLL 的額外負荷，因為 C++ 名稱重整 (Name Mangling) 不會套用至已匯出的名稱。 最後，它可讓您更易明確地加入至 .DEF 檔案 (以便於依序匯出)，而不需要擔心名稱修飾。

```cpp
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
