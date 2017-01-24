---
title: "TN058：MFC 模組狀態實作 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.implementation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 模組狀態"
  - "MFC [C++], 管理狀態資料"
  - "模組狀態 [C++], 管理狀態資料"
  - "模組狀態 [C++], 切換"
  - "處理序狀態 [C++]"
  - "執行緒狀態 [C++]"
  - "TN058"
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN058：MFC 模組狀態實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個技術提示描述「MFC 模組狀態」建構的實作。  對模組狀態執行的了解重要為使用 DLL \(或 OLE 同處理序伺服程式 \(In\-Process Server\) 共用的 MFC DLL。  
  
 在讀取這筆記錄前，請參閱[建立新的文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)中的 \< 處理 MFC 模組狀態資料 \> 。  本文包含重要使用方式資訊和一般相關資訊的主題。  
  
## 概觀  
 有三種 MFC 狀態資訊:模組狀態、處理狀態和執行緒狀態。  有時候這些狀態型別可以合併。  例如， MFC 的控制代碼對應是模組本機和執行緒區域。  這允許兩個不同模組中有不同的對應其每一個執行緒。  
  
 處理狀態和執行緒狀態是類似的。  這些資料項目是傳統上是全域變數的事，，但是需要專屬於特定處理序或執行緒適當的 Win32 支援的或適當的多執行緒支援的。  要分類的指定資料項目符合取決於項目和其所需的語意有關處理序和執行緒界限。  
  
 模組狀態是唯一的原因是它可以包含實際上是管理本機或執行緒區域的全域狀態或狀態。  此外，還可以迅速進行交換。  
  
## 模組狀態切換  
 每個執行緒包含指標「Current」或「Active」模組狀態 \(果然，指標是 MFC 執行緒區域狀態的一部分\)。  呼叫這個指標會變更，當執行緒傳遞模組界限時，例如應用程式到 OLE automation 控制項或 DLL 或 OLE automation 控制項回呼至應用程式。  
  
 目前模組狀態呼叫 **AfxSetModuleState**交換。  在大部分的情況下，您不應直接處理應用程式開發介面。  MFC，在許多情況下，它會呼叫您的 \(WinMain、OLE 進入點、 **AfxWndProc**等等\)。這在您透過知道的靜態連接寫在特殊 **WndProc**的所有元件進行特殊 `WinMain` \(或 `DllMain`\) 哪個模組狀態應該目前。  您可以在 MFC\\SRC 目錄的 DLLMODUL.CPP 或 APPMODUL.CPP 看到這個程式碼。  
  
 很罕見要設定模組狀態並沒有設定它。  在大多數情況下要「push」您的模組狀態設定為目前項目，因此，在您完成後，「pop」原始內容。  這是由 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 巨集和特殊類別 **AFX\_MAINTAIN\_STATE**完成。  
  
 `CCmdTarget` 不支援的模組狀態切換特殊功能。  特別是， `CCmdTarget` 是用於 OLE Automation 和 OLE COM 進入點的根類別。  就像其他進入點公開在系統中，這些進入點必須設定正確的模組狀態。  指定 `CCmdTarget` 如何知道「正確」模組狀態應該是?  答案是它會記住哪些「Current」模組狀態是建構，這樣它可以將目前模組狀態設定為該「記住」，會在之後呼叫時。  因此，指定 `CCmdTarget` 物件關聯的模組狀態設定為目前的模組狀態，當物件建構。  取得載入 INPROC 伺服器，建立物件及呼叫其方法的簡單範例。  
  
1.  使用 **LoadLibrary**， DLL 是由 OLE 載入。  
  
2.  **RawDllMain** 先被呼叫。  它會將模組狀態設定為 DLL 的已知的靜態模組狀態。  因此 **RawDllMain** DLL 靜態連結。  
  
3.  Class Factory 的建構函式與我們的物件呼叫。  `COleObjectFactory` 衍生自 `CCmdTarget` 的，因此，它在哪個模組狀態記住它具現化。  這很重要—當 Class Factory 要求建立物件時，它會出現在知道變更為使用中的哪些模組狀態。  
  
4.  `DllGetClassObject` 呼叫所取得的 Class Factory。  MFC 搜尋 Class Factory 清單與這個模組並將它傳回。  
  
5.  **COleObjectFactory::XClassFactory2::CreateInstance** 被呼叫。  在建立物件和傳回它之前，這個函式會將模組狀態設定為目前在步驟 3 中的模組狀態 \(當 `COleObjectFactory` 具現化時，目前的模組狀態\)。  這是在 [METHOD\_PROLOGUE](../Topic/METHOD_PROLOGUE.md)完成。  
  
6.  當物件建立時，它也很容易記住的模組狀態設定為作用中的 `CCmdTarget` 衍生和相同的方式，則為 `COleObjectFactory` ，新的物件也是一樣。  現在物件知道交換的哪個模組狀態，只要呼叫。  
  
7.  用戶端呼叫它從它的 `CoCreateInstance` 呼叫接收在 OLE COM 物件的函式。  當物件呼叫時使用 `METHOD_PROLOGUE` 參數模組狀態，如 `COleObjectFactory` 。  
  
 如您所見，模組狀態會在建立物件時，從物件傳送至物件。  是重要的安排模組狀態設定正確。  如果未設定，您的 DLL 或 COM 物件可能會與呼叫它的 MFC 應用程式的互動，或是找不到它的資源或可能無法其他淒慘的方式。  
  
 請注意某些 DLL， 「MFC 擴充 DLL」不明確地切換其 **RawDllMain** 的模組狀態 \(事實上，即使它們通常沒有 **RawDllMain**\)。  這是，因為它們的行為「好像」它們實際上有使用它們的應用程式。  它們是執行應用程式的一部分，並為其要修改該應用程式的全域狀態。  
  
 OLE automation 控制項和其他 DLL 有很多種。  它們不要修改呼叫應用程式的狀態;呼叫它們的應用程式可能不是偶數 MFC 應用程式和因此可能無法在未修改的狀態。  這是原因模組狀態切換時執行了。  
  
 對輸出從 DLL 函式，例如啟動 DLL 中的對話方塊的話，您必須將下列程式碼加入至函式的開頭:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 這個互換直到從目前範圍結尾的 [AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md) 傳回的這個狀態的目前模組狀態。  
  
 如果沒有使用，資源的問題在 DLL 會發生 `AFX_MODULE_STATE` 巨集。  根據預設， MFC 會使用主應用程式的資源控制代碼載入資源範本。  這個範本在 DLL 實際儲存。  原因是 MFC 模組狀態資訊由 `AFX_MODULE_STATE` 巨集交換。  資源控制代碼從 MFC 模組狀態復原。  造成錯誤的資源控制代碼不使用交換模組狀態。  
  
 `AFX_MODULE_STATE` 不需要將每個函式放在 DLL 。  例如， `InitInstance` 可以由應用程式的 MFC 程式碼呼叫，而不使用 `AFX_MODULE_STATE` ，因為 MFC 在 `InitInstance` 然後參數之前自動將模組狀態， `InitInstance` 傳回之後。  這也適用於所有訊息對應的處理常式。  標準 DLL 實際上會在傳送任何訊息之前自動切換至模組狀態的特殊主視窗程序。  
  
## 管理本機資料  
 管理本機資料不會是這種憂考慮若沒有 Win32 DLL 模型的問題。  在 Win32 DLL 共用其全域資料，，即使載入由多個應用程式。  這與「virtual」Win32 DLL 資料模型不同，每個 DLL 取得其在每個處理序的資料空間不同的複本附加至 DLL。  要加入至Win32 DLL在堆積配置的資料複雜度，實際上是處理特定程序 \(至少有擁有權是\)。  請考慮下列資料和程式碼：  
  
```  
static CString strGlobal; // at file scope  
  
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
   strGlobal = lpsz;  
}  
  
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz, size_t cb)  
{  
   StringCbCopy(lpsz, cb, strGlobal);  
}  
```  
  
 考慮發生的事情，如果上述程式碼位於 DLL，而且該 DLL 是由兩個處理序 A 和 B \(它載入可能，實際上，相同應用程式的兩個執行個體\)。  由 `SetGlobalString("Hello from A")`呼叫。  因此，記憶體為 `CString` 資料配置處理序 A. 中。  記住 `CString` 是全域的可看見 A 和 B。  現在 B 呼叫 `GetGlobalString(sz, sizeof(sz))`。  B 可以看到 set A 的資料。  這是因為， Win32 不提供在處理序之間共用保護與 Win32。  這是第一個問題;在大部分情況下有一個應用程式會影響全域資料要由不同的應用程式所擁有的是不需要的。  
  
 有其他問題。  假設 A 立即結束。  當A結束時，'`strGlobal`' 資料使用的記憶體可供系統使用，也就是所有記憶體配置管理是由作業系統自動釋放。  因為 `CString` 解構函式被呼叫，則不會釋放；他尚未被呼叫。  因為它配置的應用程式離開了位置所以它被釋放。  現在如果 B 呼叫 `GetGlobalString(sz, sizeof(sz))`，不見得為有效的資料。  其他應用程式可以做為其他使用了該記憶體。  
  
 問題清楚地存在。  MFC 或將使用了呼叫執行緒區域儲存區的技巧 \(TLS\)。  即使未呼叫該會參考以的所有資料 TLS 索引，MFC 3.x 將配置在 Win32 下實際上為流程區域儲存區 \(TLS\) 索引的 TLS 索引。  這類似於 Win32 用來儲存執行緒區域資料的 TLS 索引 \(請參閱以下有關該主題的詳細資訊\)。  這會讓每個 MFC DLL 將每個處理序至少兩個 TLS 索引。  當您處理許多載入 OLE automation 控制項 DLL \(OCXs\)，您可以快速耗盡 TLS 索引 \(只有 64 可用\)。  此外， MFC 必須在一個地方放置這些資料，單一結構的。  它不是非常擴充並不是理想之 TLS 索引的用途。  
  
 MFC 4.x 解決此與您可以「資料包裝」應該是處理區域的一組類別樣板。  例如，上述問題可以寫入方案:  
  
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
  
 MFC 實作以兩個步驟。  首先，具有圖層在只使用每個處理序兩個 TLS 索引的 Win32 API \( **Tls\*TlsAlloc**和 **TlsSetValue**和 **TlsGetValue**等等\) 上方，，無論您的 DLL。  其次，提供 `CProcessLocal` 範本存取此資料。  它會覆寫為操作員\> 何種可讓您查看上面的直覺化的使用語法。  所有`CProcessLocal` 所包裝的物件都必須衍生自 `CNoTrackObject`。  `CNoTrackObject` 提供低階配置器 \(**LocalAlloc**和**LocalFree**\) 和虛擬解構函式這類 MFC 可自動終結處理區域物件，當處理序結束時。  如果需要，這類物件可以有自訂解構函式額外清除。  因為編譯器會產生預設解構函式終結內嵌的 `CString` 物件，上述範例不需要。  
  
 這個方法有其他有趣的優點。  除了自動終結所有 `CProcessLocal` 物件外，直到需要時，它們才會建構，。  `CProcessLocal::operator->` 會在他第一次呼叫時產生關聯的物件。  在上面的範例中，這表示 '`strGlobal`' 字串第一次不會建構直到 **SetGlobalString** 或 **GetGlobalString** 呼叫。  在某些情況下，這有助於降低 DLL 啟動時間。  
  
## 執行緒區域資料  
 當資料必須是在特定執行緒時，類似於管理本機資料，執行緒區域資料。  您需要存取該資料的個別執行個體為每個執行緒。  這可能會多次使用代替廣泛的同步處理機制。  如果資料不需要由多個執行緒共用，這種機制可以是高度耗費資源和不必要的。  假設有一個 `CString` 物件 \(很像上面範例中的\)。  我們可以透過包裝它成為執行緒區域與 `CThreadLocal` 範本:  
  
```  
struct CMyThreadData : public CNoTrackObject  
{  
   CString strThread;  
};  
CThreadLocal<CMyThreadData> threadData;  
  
void MakeRandomString()  
{  
   // a kind of card shuffle (not a great one)  
   CString& str = threadData->strThread;  
   str.Empty();  
   while (str.GetLength() != 52)  
   {  
      unsigned int randomNumber;  
      errno_t randErr;  
      randErr = rand_s( &randomNumber );  
      if ( randErr == 0 )  
      {  
         TCHAR ch = randomNumber % 52 + 1;  
         if (str.Find(ch) < 0)  
            str += ch; // not found, add it  
      }  
   }  
}  
```  
  
 如果 `MakeRandomString` 從兩個不同執行緒呼叫，其中每個字串以不同的方式「拖曳」，而不會干擾其他的。  這是因為實際上有一個 `strThread` 執行個體的每個執行緒而不是全域執行個體。  
  
 請注意參考如何用來一次擷取 `CString` 位址而不是一次迴圈反覆項目。  迴圈碼可以撰寫與加入處理 `threadData->strThread` '`str`' 使用，不過，程式碼會比較慢執行。  在這類參考在迴圈時，會發生快取資料的參考是最佳的。  
  
 `CThreadLocal` 類別樣板使用相同的機制 `CProcessLocal` 做同樣實作技術。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)