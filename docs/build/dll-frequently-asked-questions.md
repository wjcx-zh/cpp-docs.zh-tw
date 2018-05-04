---
title: MFC DLL 常見問題集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f5740989562aea799f3a49adfa464e2c460acb3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="dll-frequently-asked-questions"></a>DLL 常見問題集  
  
下列是一些常見問題集 (FAQ) 有關的 Dll。  
    
-   [MFC DLL 可以建立多個執行緒嗎？](#mfc_multithreaded_1)  

-   [多執行緒應用程式可以存取不同執行緒中的 MFC DLL 嗎？](#mfc_multithreaded_2)  
  
-   [是否有任何 MFC 類別或函式不能用於 MFC DLL？](#mfc_prohibited_classes)  
  
-   [若要改善用戶端應用程式的效能，載入時應該使用何項最佳化技術？](#mfc_optimization)  
  
-   [在 我的標準 MFC DLL，沒有記憶體流失，但是我的程式碼看起來正常。如何找出記憶體流失的問題？](#memory_leak)  

## <a name="mfc_multithreaded_1"></a> MFC DLL 可以建立多個執行緒嗎？  
  
除了在初始化期間，MFC DLL 可以安全地建立多個執行緒，只要它會使用 Win32 執行緒區域儲存區 (TLS) 函式，如**TlsAlloc**配置執行緒區域儲存區。 不過，如果使用 MFC DLL **__declspec （thread)** 配置執行緒區域儲存區，用戶端應用程式必須以隱含方式連結至 DLL。 如果用戶端應用程式明確連結至 DLL 時，呼叫**LoadLibrary**將無法成功載入 DLL。 如需建立 MFC Dll 中的多個執行緒的詳細資訊，請參閱知識庫文件，而"PRB:: 呼叫 LoadLibrary() 來載入 DLL，已靜態 TLS"(Q118816)。 如需 Dll 中的執行緒本機變數的詳細資訊，請參閱[執行緒](../cpp/thread.md)。
  
 MFC DLL 會在啟動時建立新的 MFC 執行緒都會停止回應由應用程式載入時。 這包括每次呼叫建立執行緒`AfxBeginThread`或`CWinThread::CreateThread`內：  
  
-   `InitInstance`的`CWinApp`-衍生的標準 MFC DLL 中的物件。  
  
-   提供`DllMain`或**RawDllMain**標準的 MFC DLL 中函式。  
  
-   提供`DllMain`或**RawDllMain** MFC 擴充 DLL 中的函式。  
  
 如需有關建立執行緒在初始化期間的詳細資訊，請參閱知識庫文章 < PRB:: 無法建立 MFC 執行緒期間 DLL 啟動 > (Q142243)。  
  
## <a name="mfc_multithreaded_2"></a> 多執行緒應用程式可以存取不同執行緒中的 MFC DLL 嗎？
多執行緒應用程式可以存取的動態連結至 MFC 的標準 MFC Dll 和 MFC 擴充 Dll，從不同執行緒。 和 Visual c + + 4.2 版，根據應用程式可以存取從建立應用程式中的多個執行緒以靜態方式連結至 MFC 的標準 MFC Dll。  
  
 4.2 之前的版本，只有一個外部執行緒，可以將附加到靜態連結至 MFC 之標準 MFC DLL。 如需限制存取從多個執行緒 （在 Visual c + + 4.2 版） 之前以靜態方式連結至 MFC 的標準 MFC Dll 的詳細資訊，請參閱知識庫文件中，「 多個執行緒和 MFC _USRDLLs 」 (Q122676)。  
  
 請注意，詞彙 USRDLL 不再使用 Visual c + + 文件中。 以靜態方式連結至 MFC 之標準 MFC DLL 具有先前 USRDLL 相同的特性。  


## <a name="mfc_prohibited_classes"></a> 是否有任何 MFC 類別或函式不能用於 MFC DLL？
擴充 Dll 使用`CWinApp`-衍生的類別，用戶端應用程式。 它們不能自己`CWinApp`-衍生的類別。  
  
MFC 的標準 Dll 必須`CWinApp`-衍生的類別和單一物件，該應用程式類別，MFC 應用程式一樣。 不同於`CWinApp`物件的應用程式， `CWinApp` DLL 的物件不具有主要訊息幫浦。  
  
 請注意，因為`CWinApp::Run`機制不會套用到 DLL，應用程式擁有主要訊息幫浦。 如果 DLL 開啟非強制回應對話方塊或有它自己的主框架視窗時，應用程式的主要訊息幫浦必須呼叫匯出的 DLL 時，也就會呼叫常式`CWinApp::PreTranslateMessage`DLL 的應用程式物件的成員函式。  

## <a name="mfc_optimization"></a> 何項最佳化技術我應該使用來改善用戶端應用程式&#39;s 載入時的效能？
如果您的 DLL 是以靜態方式連結至 MFC，將它變更為一般的標準 MFC DLL 動態連結至 MFC 的 MFC DLL 會減少檔案大小。  
  
 如果 DLL 已大量匯出的函式，使用.def 檔案來匯出的函式 (而不是使用 **__declspec （dllexport)**)，並使用.def 檔[NONAME 屬性](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)上每個匯出函式。 NONAME 屬性會造成只有的序數值而不是儲存在 DLL 的匯出資料表，縮減檔案大小的函式名稱。  
  
 應用程式載入時，會載入至應用程式以隱含方式連結的 Dll。 若要載入時改善效能，請嘗試將 DLL 分割成不同的 Dll。 將一個 DLL 載入之後，立即呼叫的應用程式所需的所有函式，而且有呼叫以隱含方式連結至該 DLL 的應用程式。 將其他函式呼叫的應用程式不需要立即放入另一個 DLL 並讓應用程式明確地連結到該 DLL。 如需詳細資訊，請參閱[判斷要使用哪一個連結方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。  

## <a name="memory_leak"></a> 那里&#39;s 記憶體流失，我的標準 MFC DLL，但我的程式碼看起來正常。 如何找出記憶體流失的問題？  
  
記憶體流失的可能的原因是 MFC 會建立訊息處理常式函式內所使用的暫存物件。 在 MFC 應用程式，這些暫存物件會自動清除在`CWinApp::OnIdle()`之間處理訊息所呼叫函式。 不過，在 MFC 動態連結程式庫 (Dll)、`OnIdle()`函式不會自動呼叫。 如此一來，暫存物件會不會自動清除。 若要清除暫存物件，此 DLL 必須明確地呼叫`OnIdle(1)`定期。  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)