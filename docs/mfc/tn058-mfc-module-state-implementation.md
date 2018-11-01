---
title: TN058：MFC 模組狀態實作
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.implementation
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: db34f528e70a7dcc437836684656b3ce8a4078fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626040"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058：MFC 模組狀態實作

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

這個技術提示描述 MFC"模組狀態 「 建構的實作。 模組狀態實作了解在使用 MFC 的共用 Dll 從 DLL 為重大 （或 OLE 同處理序伺服器）。

之前讀取這個附註，請參閱 「 管理資料的 MFC 模組狀態 」 中[建立新的文件中，Windows，並檢視](../mfc/creating-new-documents-windows-and-views.md)。 這份文件包含重要的使用方式資訊以及有關此主題的概觀資訊。

## <a name="overview"></a>總覽

有三種類型的 MFC 狀態資訊： 模組狀態、 處理序狀態和執行緒的狀態。 有時可以結合這些狀態類型。 例如，MFC 的處理常式對應是本機的模組和執行緒區域。 這可讓兩個不同的模組可以有不同的對應中的每個其執行緒。

處理序狀態和執行緒狀態很類似。 這些資料項目會向來全域變數，但有專屬於特定的處理序或執行緒支援適當的 win32 或適當的多執行緒支援需要的項目。 指定的資料項目可放入哪個類別取決於這個項目和其所需的語意，關於處理序和執行緒界限。

模組狀態，因為它可以包含真正的全域狀態或本機的程序或執行緒區域狀態，則是唯一的。 此外，它可以快速地切換。

## <a name="module-state-switching"></a>切換模組狀態

每個執行緒都包含 「 目前 」 或 「 作用中 」 的模組狀態的指標 （不用多說，指標是 MFC 的執行緒本機狀態的一部分）。 此指標會變更時執行的執行緒會傳遞模組界限，例如呼叫 OLE 控制項或 DLL 或 OLE 控制項回呼至應用程式的應用程式。

目前的模組狀態切換藉由呼叫`AfxSetModuleState`。 大部分的情況下，您將永遠不會直接處理的 API。 MFC 中，在許多情況下，將它取名為您 (在 WinMain，OLE 項目點， `AfxWndProc`，依此類推。)。 這是在您撰寫以靜態方式連結在特殊的任何元件`WndProc`，和一個特殊`WinMain`(或`DllMain`) 所知道的模組狀態下，應該是目前。 您可以藉由查看 DLLMODUL 看到這段程式碼。CPP 或 APPMODUL。CPP MFC\SRC 目錄中。

很少想要設定模組狀態，並傳回未設定它。 大多數情況下您想要 「 推送 」 您自己的模組與目前狀態，並接著，完成之後，「 顯示 」 回原始的內容。 這由巨集[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)特殊的類別和`AFX_MAINTAIN_STATE`。

`CCmdTarget` 具有特殊的功能，以支援模組狀態切換。 特別是，`CCmdTarget`是使用 OLE automation 和 OLE COM 的進入點的根類別。 像其他任何進入點公開至系統，這些進入點必須設定正確的模組狀態。 如何未指定`CCmdTarget`知道 「 正確 」 的模組狀態應該是什麼答案是，它 「 記憶 」 的 「 目前 」 的模組狀態為何會在建構時，使它可以設定目前模組狀態的 「 記憶 」 值更新時呼叫。 如此一來，模組狀態的指定`CCmdTarget`的物件是建構物件時，目前的模組狀態。 需要載入的 INPROC 伺服器、 建立物件，並呼叫其方法的簡單範例。

1. OLE 所載入的 DLL 使用`LoadLibrary`。

2. `RawDllMain` 會先呼叫。 它會將模組狀態設定為已知的靜態模組狀態的 dll。 基於這個理由`RawDllMain`以靜態方式連結至 DLL。

1. 我們的物件相關聯的 class factory 的建構函式會呼叫。 `COleObjectFactory` 衍生自`CCmdTarget`，如此一來，它會記住已執行個體化的模組狀態。 這點很重要 — 當要求的 class factory 來建立物件時，它現在知道哪些模組狀態設為現用。

4. `DllGetClassObject` 呼叫以取得 class factory。 MFC 會搜尋此模組相關聯的類別處理站清單，並傳回它。

5. 呼叫 `COleObjectFactory::XClassFactory2::CreateInstance`。 之前建立的物件，並將其傳回，此函式的模組狀態設定為在步驟 3 中目前的模組狀態 (為目前時的一個`COleObjectFactory`具現化)。 這是內部[METHOD_PROLOGUE](com-interface-entry-points.md)。

1. 建立物件時，它也是`CCmdTarget`衍生，並以相同方式`COleObjectFactory`記憶中的模組狀態是作用中，跟著這個新物件。 現在物件知道若要切換至哪一個模組狀態時呼叫。

1. 用戶端從它收到的 OLE COM 物件上呼叫函式及其`CoCreateInstance`呼叫。 呼叫物件時它會使用`METHOD_PROLOGUE`如同切換模組狀態`COleObjectFactory`沒有。

如您所見，模組的狀態會傳播從物件到物件建立時。 請務必適當地設定模組狀態。 如果未設定，您的 DLL 或 COM 物件可能效能不佳互動的 MFC 應用程式正在呼叫它，或可能找不到它自己的資源，或在其他討厭的方式可能會失敗。

請注意，特定種類的 Dll，特別是 「 MFC 延伸模組 」 的 Dll，請勿切換模組狀態，在其`RawDllMain`(事實上，通常甚至不需要`RawDllMain`)。 這是因為它們能"，"彷彿實際存在於使用它們的應用程式的行為。 它們是非常正在執行的應用程式的一部分，而且他們来修改該應用程式的全域狀態。

OLE 控制項和其他 Dll 會非常不同。 它們不會想要修改呼叫的應用程式檢視狀態。正在呼叫的應用程式甚至可能沒有可 MFC 應用程式，因此可能沒有修改的狀態。 這是模組的狀態切換發明的原因。

從 DLL，例如會啟動一個對話方塊，在您的 DLL 匯出函式中，您需要將下列程式碼新增至函式開頭：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

這會從傳回的狀態與目前的模組狀態[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)直到目前的範圍結束為止。

如果 AFX_MODULE_STATE 巨集不會，會發生問題的 Dll 中的資源。 根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 這個範本實際上會儲存在 DLL 中。 根本原因是 MFC 的模組狀態資訊，無法由 AFX_MODULE_STATE 巨集切換。 資源控制代碼是從 MFC 的模組狀態復原。 由於未切換模組狀態而導致使用錯誤的資源控制代碼。

AFX_MODULE_STATE 不需要放在 DLL 中的每個函式。 例如，`InitInstance`可以在沒有 AFX_MODULE_STATE 應用程式中的 MFC 程式碼呼叫，因為 MFC 會自動移之前將模組狀態`InitInstance`，然後將其切換回來後`InitInstance`傳回。 這也適用於所有的訊息對應處理常式。 MFC 的標準 Dll 實際上有特殊的主視窗程序，會自動路由傳送任何訊息之前切換模組狀態。

## <a name="process-local-data"></a>處理本機資料

處理本機資料不是這類相當大的問題它尚未針對 win32 DLL 模型的困難度。 在 win32 中的所有 Dll 都共用其全域資料，即使在多個應用程式載入時。 這是非常不同的 「 真實 」 的 Win32 DLL 資料模型，其中每個 DLL 取得另一份其連結至 DLL 時每個處理序中的資料空間。 若要新增的複雜度，配置在堆積的 win32 DLL 中的資料實際上是特定的處理序 （至少目前為止的擁有權會）。 請考慮下列的資料和程式碼：

```cpp
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

請考慮如果上述程式碼會在位於 DLL 並載入 DLL 時，是由兩個處理序 A 和 B （可能，其實是兩個相同的應用程式執行個體），會發生什麼事。 呼叫`SetGlobalString("Hello from A")`。 如此一來，已配置的記憶體`CString`A.保留中的程序的內容中的資料記住`CString`本身是全域設定，可以看到這兩個 A 和 b。現在會呼叫 B `GetGlobalString(sz, sizeof(sz))`。 B 將能夠看到一組的資料。 這是因為 win32 不提供類似 Win32 處理序之間的任何保護。 這是第一個問題;在許多情況下不需要有一個會影響全域的資料會被視為不同的應用程式所擁有的應用程式。

有額外的問題。 例如，假設現在會結束。 A 結束時，所使用的記憶體 '`strGlobal`' 字串將可在系統 — 也就是所有配置的處理序 A 釋放記憶體自動作業系統。 它不會釋放因為`CString`呼叫解構函式，它尚未被尚未進行呼叫。 它只會釋出因為配置給它的應用程式已在場景。 現在，如果 B 呼叫`GetGlobalString(sz, sizeof(sz))`，它可能不會收到有效的資料。 某些其他應用程式可能使用其他內容的記憶體。

顯然有問題。 MFC 3.x 使用呼叫執行緒區域儲存區 (TLS) 的技巧。 MFC 3.x 會配置 TLS 索引的 win32 下作為處理序本機存放區索引，即使它不會呼叫，並接著會參考該 TLS 索引為基礎的所有資料。 這是用來儲存執行緒區域資料在 Win32 上的 TLS 索引的類似 （請參閱下列有關該主題的詳細資訊）。 這會造成利用每個處理序的至少兩個 TLS 索引的每個 MFC DLL。 當您考慮載入許多 OLE 控制項 Dll (Ocx) 時，快速地執行從 TLS 索引 （有只 64）。 此外，MFC 也必須將這些資料全都放在一個地方，在單一結構。 它不是非常有擴充性，並不是關於其使用的 TLS 索引的理想。

MFC 4.x 可應付這一組類別範本，您可以 「 環繞 」 應該是本機的程序的資料。 比方說，能夠修正上述問題，藉由撰寫：

```cpp
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

MFC 會實作這兩個步驟。 首先是 Win32 頂層__Tls\*__  Api (**TlsAlloc**， **TlsSetValue**， **TlsGetValue**等) 的使用每個處理序，不論您有多少 Dll 的只有兩個 TLS 索引。 第二個，`CProcessLocal`範本可用來存取此資料。 它會覆寫運算子-> 這是可讓您在上面看見直覺的語法。 所有的物件所包裝`CProcessLocal`必須衍生自`CNoTrackObject`。 `CNoTrackObject` 提供較低層級的配置器 (**LocalAlloc**/**LocalFree**) 和虛擬的解構函式，MFC 會自動損毀的程序的本機物件時的處理序終止。 如果需要額外的清除，則這類物件的自訂的解構函式。 上述範例中不需要其中一個，因為編譯器會產生預設解構函式終結內嵌`CString`物件。

有一些其他有趣的優點，這種方法。 不只是 所有`CProcessLocal`自動終結的物件不建構在需要時出現。 `CProcessLocal::operator->` 相關聯的物件第一次呼叫它時，以及一到，會具現化。 在上述範例中，這表示 '`strGlobal`' 字串將不會建構直到第一次`SetGlobalString`或`GetGlobalString`呼叫。 在某些情況下，這有助於減少 DLL 啟動時間。

## <a name="thread-local-data"></a>執行緒區域資料

類似於處理本機資料，執行緒區域資料時使用的資料必須是本機指定的執行緒。 也就是說，您需要個別的執行個體資料的每個執行緒用來存取該資料。 這可以多次可使用廣泛的同步處理機制。 如果資料不需要共用的多個執行緒，這類機制可能成本高昂且不需要。 假設我們有`CString`（很像上面的範例） 的物件。 我們可以使其成為執行緒本機包裝與`CThreadLocal`範本：

```cpp
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

如果`MakeRandomString`呼叫從兩個不同的執行緒，每個會"shuffle"字串以不同的方式而不會干擾其他。 這是因為有確實`strThread`每個執行緒，而非只是一個全域執行個體的執行個體。

請注意如何使用參考來擷取`CString`位址一次而不是一次每個迴圈反覆項目。 迴圈的程式碼可能已與撰寫`threadData->strThread`everywhere '`str`' 使用，但程式碼會在執行要慢很多。 最好的方式是發生在迴圈中的這類參考時，快取資料的參考。

`CThreadLocal`類別樣板會使用相同的機制，`CProcessLocal`不，而且相同的實作技術。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
