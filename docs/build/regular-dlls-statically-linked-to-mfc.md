---
title: "一般 MFC 靜態連結至 MFC 的 Dll |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ef25785e3d1e37ee622572f03fce56b1fa236aa
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2018
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>一般 MFC 靜態連結至 MFC 的 Dll
MFC DLL 靜態連結至 MFC 一般是在內部使用 MFC 的 DLL，而且在 DLL 中匯出的函式可以由呼叫 MFC 或非 MFC 可執行檔。 如同名稱所說明，這類型的 DLL 是建置使用 MFC 靜態連結程式庫版本。 函式通常是從一般使用標準 C 介面的 MFC DLL 匯出。 如需如何撰寫、 建置及使用 MFC 的標準 DLL 的範例，請參閱範例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。  
  
 請注意，詞彙 USRDLL 不再使用 Visual c + + 文件中。 以靜態方式連結至 MFC 之標準 MFC DLL 具有先前 USRDLL 相同的特性。  
  
 靜態連結至 MFC 之標準 MFC DLL 具有下列功能：  
  
-   可執行用戶端可以使用任何支援 Dll （C、 c + +、 Pascal、 Visual Basic 等等）; 使用的語言撰寫沒有為 MFC 應用程式之用。  
  
-   DLL 連結到相同應用程式所使用的 MFC 靜態連結程式庫。 不再是 Dll 靜態連結程式庫的另一個版本。  
  
-   4.0 版之前的 MFC，USRDLLs 會提供相同的型別與靜態連結至 MFC 的標準 MFC Dll 的功能。 Visual c + + 4.0 版，詞彙 USRDLL 為過時。  
  
 靜態連結至 MFC 之標準 MFC DLL 的需求如下：  
  
-   這種類型的 DLL 必須具現化類別，衍生自`CWinApp`。  
  
-   這種類型的 DLL 會用`DllMain`MFC 提供。 所有特定 DLL 的初始化將程式都碼放入`InitInstance`成員函式和終止程式碼中的`ExitInstance`如同正常的 MFC 應用程式。  
  
-   即使一詞 USRDLL 已過時，您仍然必須定義 「**_USRDLL**"編譯器命令列上。 此定義會決定哪些宣告會提取從 MFC 標頭檔。  
  
 MFC 的標準 Dll 必須`CWinApp`-衍生的類別和單一物件，該應用程式類別，MFC 應用程式一樣。 不過， `CWinApp` DLL 的物件不具有主要訊息幫浦，如同`CWinApp`應用程式的物件。  
  
 請注意，`CWinApp::Run`機制不適用於 DLL，因為應用程式擁有主要訊息幫浦。 如果 DLL 開啟強制回應對話方塊或有它自己的主框架視窗時，應用程式的主要訊息幫浦必須呼叫常式，依序呼叫的 dll 匯出`CWinApp::PreTranslateMessage`DLL 的應用程式物件的成員函式。  
  
 如需此函式的範例，請參閱 DLLScreenCap 範例。  
  
 一般 MFC DLL 使用標準 C 介面，通常被匯出符號。 從標準的 MFC DLL 匯出的函式的宣告看起來可能像這樣：  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 標準的 MFC DLL 中的所有記憶體配置應都維持在 DLL; 內DLL 不應該傳遞至或接收呼叫的可執行檔從下列其中一項：  
  
-   MFC 物件的指標  
  
-   MFC 所配置的記憶體的指標  
  
 如果您要執行上述任一項動作，或需要呼叫的可執行檔和 DLL 之間傳遞 MFC 衍生的物件，您必須建置 MFC 擴充 DLL。  
  
 它是只有當您建立一份資料時，將指標傳遞至配置的記憶體由 C 執行階段程式庫應用程式和 DLL 之間的安全。 您必須刪除或調整這些指標的大小或使用它們，而建立複本的記憶體。  
  
 以靜態方式連結至 MFC 的 DLL 也會動態地無法共用 MFC Dll 連結。 以靜態方式連結至 MFC 的 DLL 是動態地繫結至應用程式就像任何其他 DLL;應用程式連結，就像任何其他 DLL。  
  
 標準 MFC 靜態連結程式庫會根據所述的慣例命名[MFC Dll 命名慣例](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)。 不過，mfc 3.0 版和更新版本，它不再需要手動指定連結器您要連結 MFC 程式庫的版本。 相反地，MFC 標頭檔會自動判斷正確版本的 MFC 程式庫，連結根據前置處理器定義，例如**\_偵錯**或**_UNICODE**。 MFC 標頭檔新增 /DEFAULTLIB 指示詞，指示連結器連結特定版本的 MFC 程式庫。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [初始化 MFC 的標準 Dll](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [將 MFC 當成 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [在 MFC DLL 中使用資料庫、OLE 和通訊端 MFC 延伸模組 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [建立 MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
-   [動態連結至 MFC 的標準 MFC DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 延伸模組 DLL](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>請參閱  
 [DLL 的種類](../build/kinds-of-dlls.md)