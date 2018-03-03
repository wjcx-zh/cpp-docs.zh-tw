---
title: "TN058: MFC 模組狀態實作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.implementation
dev_langs:
- C++
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed7bc195c771026ff3e58d53f9e3936791810e76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058：MFC 模組狀態實作
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個技術提示描述 MFC 「 模組狀態 」 建構的實作。 使用 MFC 共用 Dll 從 DLL 模組狀態實作了解相當重要 （或 OLE 中處理序伺服器）。  
  
 再讀取這個註解，請參閱 「 管理資料的 MFC 模組狀態 」 中[建立新文件、 視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)。 這份文件包含重要的使用方式資訊與此主題的概觀資訊。  
  
## <a name="overview"></a>總覽  
 有三種類型的 MFC 狀態資訊： 模組狀態、 程序狀態和執行緒狀態。 有時候可以結合這些狀態類型。 比方說，MFC 控制代碼對應是本機的模組和本機執行緒。 這可讓兩個不同的模組，若要在其執行緒的每個有不同的對應。  
  
 處理序狀態和執行緒狀態很類似。 這些資料的項目是傳統上已全域變數，但需要針對指定的處理序或執行緒支援適當的 win32 或適當的多執行緒支援的事。 指定的資料的項目納入的類別取決於這個項目和其所需的語意與處理序和執行緒界限。  
  
 模組狀態是唯一的因為它可以包含遍佈全球的狀態或本機的處理序或執行緒區域的狀態。 此外，它可以快速地切換。  
  
## <a name="module-state-switching"></a>切換模組狀態  
 每個執行緒都包含 「 目前 」 或 「 作用中 」 的模組狀態的指標 （如預期，指標是 MFC 的執行緒區域狀態的一部分）。 此指標會變更執行的執行緒會傳遞模組界限，例如呼叫 OLE 控制項、 DLL 或 OLE 控制項回呼的應用程式的應用程式。  
  
 藉由呼叫切換目前的模組狀態**AfxSetModuleState**。 大部分的情況下，您將永遠不會直接處理應用程式開發介面。 MFC 中，在許多情況下，會呼叫它為您 (WinMain，OLE 項目點，在**AfxWndProc**等。)。 這是您撰寫靜態連結中的特殊任何元件**WndProc**，和一個特殊`WinMain`(或`DllMain`)，知道哪一個模組狀態應該是目前。 您可以藉由查看 DLLMODUL 查看這個程式碼。CPP 或 APPMODUL。CPP MFC\SRC 目錄中。  
  
 很少您要將模組狀態設回未設定它。 大部分的情況下您想要在 「 推送 」 您自己的模組與目前狀態，然後完成之後，"pop"回原始的內容。 這是由巨集[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)和特殊類別**AFX_MAINTAIN_STATE**。  
  
 `CCmdTarget`具有特殊的功能，以支援模組狀態切換。 特別是，`CCmdTarget`是使用 OLE automation 和 OLE COM 的進入點的根類別。 像任何其他的進入點公開至系統，這些項目點必須設定正確的模組狀態。 如何未指定`CCmdTarget`知道 「 正確 」 的模組狀態應該是什麼辦法就是，它 「 記住 」 功能的 「 目前 」 的模組狀態時，它由建構，使它可以設定目前的模組狀態的 「 記住 」 呼叫更新時的值。 如此一來，模組狀態的給定`CCmdTarget`的物件是目前物件建構時將模組狀態。 需要載入 INPROC 伺服器、 建立物件，並呼叫其方法的簡單範例。  
  
1.  載入 DLL ole 使用**LoadLibrary**。  
  
2. **RawDllMain**稱為第一次。 它會將模組狀態設定為已知的靜態模組狀態的 dll。 基於這個理由**RawDllMain**以靜態方式連結至 DLL。  
  
3.  我們物件相關聯的 class factory 的建構函式會呼叫。 `COleObjectFactory`衍生自`CCmdTarget`，如此一來，它會記住具現化中的模組狀態。 這一點非常重要，當要求的 class factory 來建立物件，它現在知道哪些讓目前的模組狀態。  
  
4. `DllGetClassObject`呼叫以取得 class factory。 MFC 搜尋此模組相關聯的類別處理站清單，並傳回它。  
  
5. **COleObjectFactory::XClassFactory2::CreateInstance**呼叫。 之前建立的物件，並將其傳回，此函式的模組狀態設定為在步驟 3 中目前的模組狀態 (於目前時`COleObjectFactory`未具現化)。 這是內部[METHOD_PROLOGUE](com-interface-entry-points.md)。  
  
6.  建立物件時，它也是`CCmdTarget`衍生和相同的方式`COleObjectFactory`記住的模組狀態下，活躍，也會跟著這個新的物件。 現在物件知道切換到哪一個模組狀態時呼叫。  
  
7.  用戶端呼叫的函式，它收到來自 OLE COM 物件上其`CoCreateInstance`呼叫。 呼叫物件時它會使用`METHOD_PROLOGUE`一樣切換模組狀態`COleObjectFactory`沒有。  
  
 如您所見，將模組狀態從傳送物件至物件建立時。 它是一定要有適當地設定將模組狀態。 如果未設定，您的 DLL 或 COM 物件可能狀況不佳互動的 MFC 應用程式正在呼叫它，或可能是找不到它自己的資源，或在其他這些方法可能會失敗。  
  
 請注意，某些類型的 Dll，特別是 < MFC 延伸模組 > Dll 不會轉換中的模組狀態及其**RawDllMain** (事實上，它們通常甚至不必**RawDllMain**)。 這是因為它們是 「 如同 「 實際存在於它們使用的應用程式的行為。 它們非常正在執行的應用程式的一部分，而且他們来修改應用程式的全域狀態。  
  
 OLE 控制項和其他 Dll 也非常不同。 它們不會想要修改呼叫的應用程式檢視狀態。正在呼叫的應用程式即使可能不 MFC 應用程式，因此可能有無修改狀態。 這是模組的狀態切換所發明的原因。  
  
 匯出的函式，從 DLL，例如啟動對話方塊，在您的 DLL，您需要將下列程式碼加入至函式開頭：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState())  
```  
  
 這會將目前的模組狀態與從傳回的狀態[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)到目前的範圍結束為止。  
  
 如果沒有使用 `AFX_MODULE_STATE` 巨集，就會發生在 DLL 中使用資源的問題。 根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 這個範本實際上會儲存在 DLL 中。 其根本原因是 MFC 的模組狀態資訊並未由 `AFX_MODULE_STATE` 巨集交換。 資源控制代碼是從 MFC 的模組狀態復原。 由於未切換模組狀態而導致使用錯誤的資源控制代碼。  
  
 `AFX_MODULE_STATE`不需要放在 DLL 中的每個函式。 例如，`InitInstance` 可以由應用程式中的 MFC 程式碼呼叫，而不需使用 `AFX_MODULE_STATE`，因為 MFC 會在 `InitInstance` 之前將模組狀態自動位移，然後在 `InitInstance` 傳回之後再將其切換回來。 也適用於所有的訊息對應處理常式。 MFC 的標準 Dll 實際上具有特殊的主視窗程序，會自動切換模組狀態，再傳送訊息。  
  
## <a name="process-local-data"></a>處理本機資料  
 本機資料的程序就無法這類相當大的問題已使其不受的 win32 DLL 模型的困難度。 在 win32 中所有 Dll 都共用其全域資料，即使是由多個應用程式載入。 這是非常不同的 「 實際 」 的 Win32 DLL 資料模型，其中每個 DLL 中取得的資料空間的每個程序，將附加到 DLL 的個別複本。 若要加入的複雜度，配置在堆積的 win32 DLL 中的資料事實上是特定的處理序 （至少目前為止的擁有權會）。 請考慮下列的資料和程式碼：  
  
```  
static CString strGlobal; // at file scope  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz,
    size_t cb)  
{  
    StringCbCopy(lpsz,
    cb,
    strGlobal);

}  
```  
  
 請考慮如果上述程式碼中位於 DLL，DLL 由 A 和 B （無法，事實上，是相同的應用程式的兩個執行個體） 的兩個處理序載入，會發生什麼事。 呼叫`SetGlobalString("Hello from A")`。 如此一來，將記憶體配置給`CString`A.將保留在程序的內容中的資料，請記住，`CString`本身是全域設定，都可以看到這兩個 A 和 b現在，呼叫 B `GetGlobalString(sz, sizeof(sz))`。 B 會看到一組資料。 這是因為 win32 中提供類似 Win32 處理序之間沒有保護。 這是第一個問題;在許多情況下不希望有一個會影響被視為不同的應用程式所擁有的全域資料的應用程式。  
  
 有其他的問題。 例如，假設現在會結束。 當 A 存在時，所使用的記憶體 '`strGlobal`' 字串供系統 — 也就是所有處理程序所配置的記憶體自動釋放由作業系統。 它不會釋放因為`CString`呼叫解構函式，它尚未被尚未進行呼叫。 它只會釋出配置給它的應用程式已離開場景因為。 現在，如果 B 呼叫`GetGlobalString(sz, sizeof(sz))`，它可能不會收到有效的資料。 某些其他應用程式可能使用該記憶體的其他項目。  
  
 清楚地有問題存在。 MFC 3.x 使用呼叫執行緒區域儲存區 (TLS) 的技術。 MFC 3.x 會配置的 TLS 索引在 win32 中真正做為處理序區域儲存區索引，即使它不會呼叫的然後會參考該 TLS 索引為基礎的所有資料。 這是用於儲存執行緒區域資料在 Win32 TLS 索引類似 （請參閱下方有關該主題的詳細資訊）。 這會造成利用至少兩個 TLS 索引，每個處理序的每個 MFC DLL。 當您考量載入多個 OLE 控制項 Dll (Ocx) 時，您快速完 TLS 索引 （有可用的只有 64）。 此外，MFC 就必須將所有這些資料放在單一結構中的一個位置。 它不是擴充性很高，且不理想方面的 TLS 索引使用。  
  
 MFC 4.x 可應付這一組類別範本，您可以 「 包裝 」 應該是本機的程序在資料周圍。 例如，可以藉由撰寫修正上述問題：  
  
```  
struct CMyGlobalData : public CNoTrackObject  
{  
    CString strGlobal;  
};  
CProcessLocal<CMyGlobalData> globalData;  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    globalData->strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz, size_t cb)  
{  
    StringCbCopy(lpsz, cb, globalData->strGlobal);

}  
```  
  
 MFC 實作這兩個步驟。 首先是 Win32 之上的層級**Tls\*** 應用程式開發介面 (**TlsAlloc**， **TlsSetValue**， **TlsGetValue**等等) 的使用每個處理序，不論您有多少 Dll 只有兩個 TLS 索引。 第二個，`CProcessLocal`存取這項資料就會提供範本。 它會覆寫運算子-> 這是功能可讓您看到上述語法。 所有的物件會包裝`CProcessLocal`必須衍生自`CNoTrackObject`。 `CNoTrackObject`提供較低層級的配置器 (**LocalAlloc**/**LocalFree**) 和虛擬解構函式，MFC 也可以在程序時自動終結程序的本機物件終止。 如果需要額外的清除，則這類物件可以有自訂的解構函式。 上述範例中不需要其中一個，因為編譯器會產生預設解構函式終結內嵌`CString`物件。  
  
 還有其他有趣的優點，這種方法。 不只是所有`CProcessLocal`終結自動物件不建構直到需要時才。 `CProcessLocal::operator->`相關聯的物件第一次呼叫，並立即，會具現化。 在上述範例中，這表示 '`strGlobal`' 字串不會等到第一次建構**SetGlobalString**或**GetGlobalString**呼叫。 在某些情況下，這可協助減少 DLL 啟動時間。  
  
## <a name="thread-local-data"></a>執行緒區域資料  
 類似於處理本機資料，執行緒區域資料時使用的資料必須是本機給定的執行緒。 也就是說，您需要存取該資料的每個執行緒資料的個別執行個體。 這可以多次使用這個廣泛的同步處理機制。 如果資料不需要由多個執行緒共用，這類機制可以是高度耗費資源，而非必要。 假設我們`CString`（類似上述範例） 的物件。 我們可以將執行緒本機包裝它與`CThreadLocal`範本：  
  
```  
struct CMyThreadData : public CNoTrackObject  
{  
    CString strThread;  
};  
CThreadLocal<CMyThreadData> threadData;  
 
void MakeRandomString()  
{ *// a kind of card shuffle (not a great one)  
    CString& str = threadData->strThread;  
    str.Empty();
while (str.GetLength() != 52)  
 {  
    unsigned int randomNumber;  
    errno_t randErr;  
    randErr = rand_s(&randomNumber);

    if (randErr == 0)  
 {  
    TCHAR ch = randomNumber % 52 + 1;  
    if (str.Find(ch) <0)  
    str += ch; // not found, add it  
 }  
 }  
}  
```  
  
 如果`MakeRandomString`呼叫從兩個不同的執行緒，每個會 「 隨機播放"字串以不同的方式而不會干擾其他。 這是因為沒有實際`strThread`每個執行緒，而不只一個全域執行個體的執行個體。  
  
 請注意如何使用參考來擷取`CString`解決一次而非一次每個迴圈反覆項目。 迴圈的程式碼可能已撰寫與`threadData->strThread`everywhere '`str`' 使用，但該程式碼會在執行要慢很多。 您最好在迴圈中發生這類的參考時，快取資料的參考。  
  
 `CThreadLocal`類別樣板會使用相同的機制，`CProcessLocal`功能以及相同的實作技術。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

