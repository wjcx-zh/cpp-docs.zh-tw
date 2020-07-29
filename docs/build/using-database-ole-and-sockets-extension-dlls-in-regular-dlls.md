---
title: 在一般 MFC Dll 中使用資料庫、OLE 和通訊端 MFC 延伸 Dll
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: 3d516f7923144f0e24bda676147ed529546def25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213758"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>在一般 MFC Dll 中使用資料庫、OLE 和通訊端 MFC 延伸 Dll

從一般 MFC DLL 使用 MFC 擴充 DLL 時，如果 MFC 延伸 DLL 未連接到一般 MFC DLL 的**CDynLinkLibrary**物件鏈，您可能會遇到一或多個相關的問題。 由於 MFC 資料庫、OLE 和通訊端支援 Dll 的偵錯工具版本會實作為 MFC 延伸 Dll，因此，如果您使用這些 MFC 功能，您可能會看到類似的問題，即使您未明確使用任何自己的 MFC 延伸 Dll 也一樣。 一些徵兆如下：

- 當您嘗試還原序列化 MFC 延伸模組 DLL 中定義之類別類型的物件時，會出現訊息「警告：無法從封存載入 CYourClass。 類別未定義。」 會出現在追蹤的 [調試] 視窗中，而且物件無法序列化。

- 指出可能會擲回錯誤類別的例外狀況。

- 儲存在 MFC 延伸模組 DLL 中的資源無法載入，因為傳回 `AfxFindResourceHandle` **Null**或不正確的資源控制碼。

- `DllGetClassObject`、 `DllCanUnloadNow` 和的、、和成員函式 `UpdateRegistry` `Revoke` `RevokeAll` 找不 `RegisterAll` `COleObjectFactory` 到 MFC 延伸 DLL 中定義的 Class Factory。

- `AfxDoForAllClasses`不適用於 MFC 延伸模組 DLL 中的任何類別。

- 無法載入標準 MFC 資料庫、通訊端或 OLE 資源。 例如， **AfxLoadString**（**AFX_IDP_SQL_CONNECT_FAIL**）會傳回空字串，即使正則 MFC DLL 正確使用 mfc 資料庫類別也一樣。

這些問題的解決方法是，在建立**CDynLinkLibrary**物件的 MFC 延伸 DLL 中建立及匯出初始化函數。 從使用 MFC 延伸 DLL 的每個一般 MFC DLL，只呼叫這個初始化函式一次。

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE、MFC 資料庫（或 DAO），或 MFC 通訊端支援

如果您使用任何 MFC OLE、MFC 資料庫（或 DAO），或您的一般 MFC DLL 中的 MFC 通訊端支援，則 MFC debug MFC 延伸 Dll MFCOxxD.dll、MFCDxxD.dll 和 MFCNxxD.dll （其中 xx 是版本號碼）會自動連結。 您必須針對您所使用的每個 Dll，呼叫預先定義的初始化函數。

如需資料庫支援，請將對的呼叫新增 `AfxDbInitModule` 至您的一般 MFC DLL 函式 `CWinApp::InitInstance` 。 請確定這個呼叫發生在任何基類呼叫之前，或任何已加入的程式碼，以存取 MFCDxxD.dll。 此函式不接受任何參數，且會傳回 void。

如需 OLE 支援，請將對的呼叫新增 `AfxOleInitModule` 至您的一般 MFC DLL `CWinApp::InitInstance` 。 請注意， **COleControlModule InitInstance**函數 `AfxOleInitModule` 已經呼叫，因此，如果您要建立 OLE 控制項並使用 `COleControlModule` ，則不應該將這個呼叫加入至 `AfxOleInitModule` 。

如需通訊端支援，請將對的呼叫新增 `AfxNetInitModule` 至您的一般 MFC DLL `CWinApp::InitInstance` 。

請注意，MFC Dll 和應用程式的發行組建不會針對資料庫、通訊端或 OLE 支援使用個別的 Dll。 不過，您可以放心地在發行模式中呼叫這些初始化函數。

## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary 物件

在本主題一開始所提到的每項作業期間，MFC 需要搜尋所需的值或物件。 例如，在還原序列化期間，MFC 需要搜尋所有目前可用的執行時間類別，以符合封存中的物件與其適當的執行時間類別。

在這些搜尋中，MFC 會藉由流覽**CDynLinkLibrary**物件的鏈，來掃描使用中的所有 MFC 延伸 dll。 **CDynLinkLibrary**物件會在其結構中自動附加至鏈，並在初始化期間依每個 MFC 延伸模組 DLL 來建立。 此外，每個模組（應用程式或一般 MFC DLL）都有自己的**CDynLinkLibrary**物件鏈。

若要讓 MFC 延伸模組 DLL 進入**CDynLinkLibrary**鏈，必須在每個使用 MFC 延伸 dll 的模組內容中建立**CDynLinkLibrary**物件。 因此，如果要從一般 MFC Dll 使用 MFC 延伸模組 DLL，它必須提供已匯出的初始化函式來建立**CDynLinkLibrary**物件。 每個使用 MFC 延伸模組 DLL 的一般 MFC DLL 都必須呼叫匯出的初始化函數。

如果 MFC 延伸 DLL 只會從 MFC 應用程式（.exe）使用，而不是從一般的 MFC DLL，則在 MFC 延伸 DLL 的中建立**CDynLinkLibrary**物件就已足夠 `DllMain` 。 這是 MFC DLL Wizard MFC 延伸模組 DLL 程式碼所執行的工作。 以隱含方式載入 MFC 延伸模組 DLL 時，會在 `DllMain` 應用程式啟動前載入並執行。 任何**CDynLinkLibrary**建立都是以 mfc DLL 保留給 mfc 應用程式的預設鏈來進行。

請注意，在任何一個鏈中有一個 MFC 延伸模組 DLL 的多個**CDynLinkLibrary**物件，特別是如果 mfc 延伸模組 dll 會從記憶體中動態卸載，這是個不錯的主意。 不要從任何一個模組呼叫初始化函數一次以上。

## <a name="sample-code"></a>範例程式碼

這個範例程式碼假設正則 MFC DLL 會隱含地連結至 MFC 延伸 DLL。 這是藉由在建立一般 MFC DLL 時連結至 MFC 延伸模組 DLL 的匯入程式庫（.lib）來完成。

下列幾行應該位於 MFC 延伸模組 DLL 的來源中：

```
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    if (dwReason == DLL_PROCESS_ATTACH)
    {
        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(extensionDLL, hInstance))
           return 0;
    }
    return 1;   // ok
}

// Exported DLL initialization is run in context of
// application or regular MFC DLL
extern "C" void WINAPI InitYourExtDLL()
{
    // create a new CDynLinkLibrary for this app
    new CDynLinkLibrary(extensionDLL);

    // add other initialization here
}
```

請務必匯出**InitYourExtDLL**函數。 這可以使用 **`__declspec(dllexport)`** 或在 DLL 的 .def 檔案中完成，如下所示：

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

使用 MFC 延伸 DLL，將呼叫新增至 `InitInstance` `CWinApp` 每個一般 MFC DLL 中衍生物件的成員：

```
// YourRegularDLL.cpp:

class CYourRegularDLL : public CWinApp
{
public:
    virtual BOOL InitInstance(); // Initialization
    virtual int ExitInstance();  // Termination

    // nothing special for the constructor
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }
};

BOOL CYourRegularDLL::InitInstance()
{
    // any DLL initialization goes here
    TRACE0("YOUR regular MFC DLL initializing\n");

    // wire any MFC extension DLLs into CDynLinkLibrary chain
    InitYourExtDLL();

    return TRUE;
}
```

### <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [初始化 MFC 延伸模組 DLL](run-time-library-behavior.md#initializing-extension-dlls)

- [初始化一般 MFC Dll](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [MFC 延伸模組 DLL](extension-dlls.md)

- [靜態連結至 MFC 的標準 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [將 MFC 當做 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>另請參閱

[MFC 延伸模組 DLL](extension-dlls.md)
