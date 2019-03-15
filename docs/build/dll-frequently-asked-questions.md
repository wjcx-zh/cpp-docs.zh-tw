---
title: MFC DLL 常見問題集
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 33a0c9dd1abbfb9375ce1aef53fd152a521ac97d
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57821933"
---
# <a name="dll-frequently-asked-questions"></a>DLL 常見問題集

下列是一些常見問題 (FAQ) 的 Dll。

- [MFC DLL 可以建立多個執行緒嗎？](#mfc_multithreaded_1)

- [多執行緒應用程式可以存取不同的執行緒中的 MFC DLL 嗎？](#mfc_multithreaded_2)

- [是否有任何 MFC 類別或函式，不能用於 MFC DLL？](#mfc_prohibited_classes)

- [若要改善用戶端應用程式的效能，載入時應該使用何項最佳化技術？](#mfc_optimization)

- [在 我的標準 MFC DLL，沒有記憶體流失，但我的程式碼看起來沒問題。如何尋找記憶體流失的問題？](#memory_leak)

## <a name="mfc_multithreaded_1"></a> MFC DLL 可以建立多個執行緒嗎？

但是在初始化期間，MFC DLL 可以安全地建立多個執行緒，只要它會使用 Win32 執行緒區域儲存區 (TLS) 這類函式**TlsAlloc**配置執行緒區域儲存區。 不過，如果使用 MFC DLL **__declspec （thread)** 配置執行緒區域儲存區，用戶端應用程式必須以隱含方式連結至 DLL。 如果用戶端應用程式明確地連結至 DLL 時，呼叫**LoadLibrary**將無法成功載入的 DLL。 如需 Dll 中的執行緒本機變數的詳細資訊，請參閱 <<c0> [ 執行緒](../cpp/thread.md)。

MFC DLL 會在啟動期間建立新的 MFC 執行緒將會停止回應的應用程式載入時。 這包括每當呼叫建立的執行緒`AfxBeginThread`或`CWinThread::CreateThread`內：

- `InitInstance`的`CWinApp`-衍生的標準 MFC DLL 中的物件。

- 提供`DllMain`或是**RawDllMain** MFC DLL 中的函式。

- 提供`DllMain`或是**RawDllMain** MFC 擴充 DLL 中的函式。

## <a name="mfc_multithreaded_2"></a> 多執行緒應用程式可以存取不同的執行緒中的 MFC DLL 嗎？

多執行緒應用程式可以從不同的執行緒存取的動態連結至 MFC 的標準 MFC Dll 和 MFC 擴充 Dll。 和 Visual c + + 4.2 版，從應用程式可以存取從應用程式中建立的多個執行緒以靜態方式連結至 MFC 的標準 MFC Dll。

4.2 之前的版本，只有一個外部執行緒，可以將附加到靜態連結至 MFC 之標準 MFC DLL。

請注意，詞彙 USRDLL 不再使用 Visual c + + 文件中。 靜態連結至 MFC 之標準 MFC DLL 有相同的特性，與之前的 usrdll。

## <a name="mfc_prohibited_classes"></a> 是否有任何 MFC 類別或函式，不能用於 MFC DLL？

延伸模組 Dll 使用`CWinApp`-衍生的類別，用戶端應用程式。 它們不能自己`CWinApp`-衍生的類別。

MFC 的標準 Dll 必須`CWinApp`-衍生類別，該應用程式類別的單一物件，MFC 應用程式一樣。 不同於`CWinApp`物件的應用程式，`CWinApp`之 dll 的物件沒有的主要訊息幫浦。

請注意，因為`CWinApp::Run`機制不會套用至 DLL、 應用程式擁有的主要訊息幫浦。 如果 DLL 開啟非強制回應對話方塊，或有自己的主框架視窗，應用程式的主要訊息幫浦就必須呼叫匯出的 DLL，而呼叫的常式`CWinApp::PreTranslateMessage`DLL 的應用程式物件的成員函式。

## <a name="mfc_optimization"></a> 何項最佳化技術應該使用以改善用戶端應用程式&#39;載入時效能？

如果您的 DLL 是以靜態方式連結至 MFC，將它變更為一般的標準 MFC DLL 動態連結至 MFC 的 MFC DLL 會減少檔案大小。

如果 DLL 有大量匯出的函式，使用.def 檔匯出的函式 (而不是使用 **__declspec （dllexport)**)，並使用.def 檔[NONAME 屬性](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)上每個匯出的函式。 NONAME 屬性會導致只有序數的值而不是儲存在 DLL 的匯出表中，以減少檔案大小的函式名稱。

應用程式載入時，會載入以隱含方式連結至應用程式的 Dll。 若要改善效能，載入時，嘗試將 DLL 分割成不同的 Dll。 將一個 DLL 載入之後，立即呼叫的應用程式所需的所有函式，而且有呼叫會隱含地連結到該 DLL 的應用程式。 將其他函式呼叫的應用程式不需要立即放入另一個 DLL 並讓應用程式明確地連結到該 DLL。 如需詳細資訊，請參閱 <<c0> [ 連結至 DLL 的可執行檔](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。

## <a name="memory_leak"></a> 那里&#39;s 記憶體流失，在我的標準 MFC DLL，但我的程式碼看起來沒問題。 如何尋找記憶體流失的問題？

記憶體流失的一個可能的原因是，MFC 會建立訊息處理常式函式內所使用的暫存物件。 在 MFC 應用程式，這些暫存物件會自動清除在`CWinApp::OnIdle()`之間處理訊息所呼叫函式。 不過，在 MFC 動態連結程式庫 (Dll)、`OnIdle()`函式不會自動呼叫。 如此一來，暫存物件不會自動清除。 若要清除暫存物件，該 DLL 必須明確地呼叫`OnIdle(1)`定期。

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
