---
title: MFC DLL 的常見問題
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417345"
---
# <a name="dll-frequently-asked-questions"></a>DLL 常見問題集

以下是一些關於 Dll 的常見問題（FAQ）。

- [MFC DLL 可以建立多個執行緒嗎？](#mfc_multithreaded_1)

- [多執行緒應用程式可以存取不同執行緒中的 MFC DLL 嗎？](#mfc_multithreaded_2)

- [有任何 MFC 類別或函式不能用於 MFC DLL 嗎？](#mfc_prohibited_classes)

- [載入時，我應該使用何項最佳化技術來改善用戶端應用程式的效能？](#mfc_optimization)

- [我的一般 MFC DLL 中有記憶體流失，但我的程式碼看起來沒問題。如何找出記憶體流失的情況？](#memory_leak)

## <a name="can-an-mfc-dll-create-multiple-threads"></a><a name="mfc_multithreaded_1"></a>MFC DLL 可以建立多個執行緒嗎？

除了在初始化期間，MFC DLL 可以安全地建立多個執行緒，只要它使用 Win32 執行緒區域儲存區（TLS）函數（例如**TlsAlloc** ）來配置執行緒區域儲存區。 不過，如果 MFC DLL 使用 **__declspec （thread）** 來配置執行緒區域儲存區，則用戶端應用程式必須隱含地連結到 DLL。 如果用戶端應用程式明確連結到 DLL，對**LoadLibrary**的呼叫將無法成功載入 dll。 如需 Dll 中線程區域變數的詳細資訊，請參閱[thread](../cpp/thread.md)。

在啟動期間建立新的 MFC 執行緒的 MFC DLL，會在應用程式載入時停止回應。 這包括每當呼叫`AfxBeginThread`或`CWinThread::CreateThread`在內建立執行緒時：

- `InitInstance`一般 MFC DLL 中衍生物件`CWinApp`的。

- 一般 MFC `DllMain` DLL 中提供的或**RawDllMain**函式。

- MFC 擴充`DllMain` DLL 中提供的或**RawDllMain**函式。

## <a name="can-a-multithreaded-application-access-an-mfc-dll-in-different-threads"></a><a name="mfc_multithreaded_2"></a>多執行緒應用程式可以存取不同執行緒中的 MFC DLL 嗎？

多執行緒應用程式可以存取從不同執行緒動態連結至 MFC 和 MFC 延伸 Dll 的標準 MFC Dll。 應用程式可以從應用程式中建立的多個執行緒，存取以靜態方式連結至 MFC 的標準 MFC Dll。

## <a name="are-there-any-mfc-classes-or-functions-that-cannot-be-used-in-an-mfc-dll"></a><a name="mfc_prohibited_classes"></a>MFC DLL 中是否有任何無法使用的 MFC 類別或函數？

擴充 Dll 會使用`CWinApp`用戶端應用程式的衍生類別。 它們不能有自己`CWinApp`的衍生類別。

一般 MFC Dll 必須擁有`CWinApp`衍生類別和該應用程式類別的單一物件，如同 MFC 應用程式一樣。 不同于`CWinApp`應用程式的物件，DLL `CWinApp`的物件沒有主要的訊息提取。

請注意，由於`CWinApp::Run`機制並不適用于 DLL，因此應用程式會擁有主要的訊息提取。 如果 DLL 開啟非強制回應對話方塊，或有自己的主框架視窗，則應用程式的主要訊息提取必須呼叫 DLL 所匯出的常式，然後再呼叫 DLL 之應用程式`CWinApp::PreTranslateMessage`物件的成員函式。

## <a name="what-optimization-techniques-should-i-use-to-improve-the-client-application39s-performance-when-loading"></a><a name="mfc_optimization"></a>載入時，我應該使用哪些優化技術來改善用戶端應用程式&#39;效能？

如果您的 DLL 是以靜態方式連結至 MFC 的一般 MFC DLL，則將它變更為動態連結至 MFC 的一般 MFC DLL 會減少檔案大小。

如果 DLL 有大量的匯出函式，請使用 .def 檔案來匯出函式（而不是使用 **__declspec （dllexport）**），並在每個匯出的函式上使用 .Def 檔案[NONAME 屬性](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。 NONAME 屬性只會導致序數值，而不會將函數名稱儲存在 DLL 的匯出資料表中，以減少檔案大小。

當應用程式載入時，會載入隱含連結至應用程式的 Dll。 若要在載入時改善效能，請嘗試將 DLL 分割成不同的 Dll。 將呼叫應用程式在載入至一個 DLL 後立即需要的所有函式放在一起，並讓呼叫應用程式隱含連結至該 DLL。 將呼叫應用程式不需要的其他函式，直接放在另一個 DLL 中，並讓應用程式明確連結到該 DLL。 如需詳細資訊，請參閱將[可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。

## <a name="there39s-a-memory-leak-in-my-regular-mfc-dll-but-my-code-looks-fine-how-can-i-find-the-memory-leak"></a><a name="memory_leak"></a>我的一般 MFC DLL 中有&#39;的記憶體流失，但是我的程式碼看起來沒問題。 如何找出記憶體流失的情況？

記憶體流失的其中一個可能原因是 MFC 建立了在訊息處理函式內部使用的暫存物件。 在 MFC 應用程式中，這些暫存物件會自動在處理`CWinApp::OnIdle()`訊息之間呼叫的函式中清除。 不過，在 MFC 動態連結程式庫（Dll）中， `OnIdle()`不會自動呼叫函式。 因此，不會自動清除暫存物件。 若要清除暫存物件，DLL 必須定期明確呼叫`OnIdle(1)` 。

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
