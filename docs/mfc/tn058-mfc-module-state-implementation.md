---
title: TN058：MFC 模組狀態實作
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: b64fb6b97474007c44a2124315e83e1ac119f9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366614"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058：MFC 模組狀態實作

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本技術說明描述了 MFC"模組狀態"構造的實現。 瞭解模組狀態實現對於使用 DLL(或 OLE 進程內伺服器)的 MFC 共用 DLL 至關重要。

在閱讀本說明之前,請參閱[創建新文檔、Windows 和視圖](../mfc/creating-new-documents-windows-and-views.md)中的"管理 MFC 模塊的狀態數據"。 本文包含有關此主題的重要使用資訊和概述資訊。

## <a name="overview"></a>概觀

有三種類型的 MFC 狀態資訊:模組狀態、進程狀態和線程狀態。 有時可以組合這些狀態類型。 例如,MFC 的句柄映射都是模組本地和線程本地。 這允許兩個不同的模組在其每個線程中具有不同的映射。

進程狀態和線程狀態類似。 這些數據項傳統上是全域變數,但需要特定於給定的進程或線程,以便適當的 Win32s 支援或適當的多線程支援。 給定數據項適合哪個類別取決於該項及其在進程和線程邊界方面的所需語義。

模組狀態是唯一的,因為它可以包含處理本地或線程本地的真正全域狀態或狀態。 此外,它可以快速切換。

## <a name="module-state-switching"></a>模組狀態切換

每個線程包含指向"當前"或"活動"模組狀態的指標(毫不奇怪,指標是 MFC 線程本地狀態的一部分)。 當執行線程透過模組邊界(如呼叫到 OLE 控制元件或 DLL 的應用程式或呼叫回應用程式的 OLE 控制項)時,此指標將發生更改。

通過調用`AfxSetModuleState`來切換當前模組狀態。 在大多數情況下,您永遠不會直接處理 API。 在許多情況下,MFC 會為您調用它(在 WinMain、OLE`AfxWndProc`入口點等)。 這是通過靜態連結在特殊`WndProc`中寫入的任何元件,以及知道哪個模塊狀態應該是最新的`WinMain`特殊`DllMain`( 或 ) 的元件中完成的。 您可以通過查看 DLLMODUL 來查看此代碼。CPP 或 APPMODUL。MFC_SRC 目錄中的 CPP。

很少要設置模塊狀態,然後不將其設置回來。 大多數時候,您希望將自己的模塊狀態"推送"為當前模組狀態,然後在完成後將原始上下文"彈出"回來。 這是由宏[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)和特殊`AFX_MAINTAIN_STATE`類 完成的。

`CCmdTarget`具有支援模組狀態切換的特殊功能。 特別是,`CCmdTarget`是用於 OLE 自動化和 OLE COM 入口點的根類。 與向系統公開的任何其他入口點一樣,這些入口點必須設置正確的模組狀態。 給定人`CCmdTarget`如何知道"正確"模塊狀態應是什麼 答案,它"記住"構造時"當前"模組狀態,以便它可以將當前模組狀態設置為"記住"值,而稍後調用它。 因此,給定`CCmdTarget`物件關聯的模塊狀態是構造物件時當前狀態的模組狀態。 以載入 INPROC 伺服器、創建物件和調用其方法的簡單示例為例。

1. DLL 由 OLE 使用`LoadLibrary`載入。

1. `RawDllMain`首先調用。 它將模組狀態設置為 DLL 的已知靜態模組狀態。 因此`RawDllMain`,它是靜態連結到 DLL 的。

1. 調用與我們物件關聯的類工廠的構造函數。 `COleObjectFactory`派生自`CCmdTarget`,因此,它記住它實例化的模塊狀態。 這一點很重要 - 當要求類工廠創建物件時,它現在知道要使當前模組狀態。

1. `DllGetClassObject`調用以獲取類工廠。 MFC 搜索與此模組關聯的類工廠清單並返回它。

1. 呼叫 `COleObjectFactory::XClassFactory2::CreateInstance`。 在創建物件並返回物件之前,此函數將模組狀態設置為步驟 3 中的模組狀態(實例`COleObjectFactory`化時為當前狀態的模組狀態)。 這是[METHOD_PROLOGUE](com-interface-entry-points.md)內部完成的。

1. 創建物件時,它也是一個`CCmdTarget`派生,並且以相同`COleObjectFactory`的方式 記住哪個模塊狀態處於活動狀態,此新物件也是如此。 現在,物件知道在調用時要切換到哪個模塊狀態。

1. 用戶端在其從`CoCreateInstance`調用中收到的 OLE COM 物件上調用函數。 當調用物件時,它使用`METHOD_PROLOGUE`來切換模組狀態,`COleObjectFactory`就像 切換對象一樣。

如您所見,模組狀態在創建時會從物件傳播到物件。 正確設置模組狀態非常重要。 如果未設置,則 DLL 或 COM 物件可能與調用它的 MFC 應用程式交互不良,或者可能無法找到自己的資源,或者可能以其他悲慘方式失敗。

請注意,某些類型的 DLL,特別是「MFC 擴展」DLL`RawDllMain`不會在其 狀態中切換模組狀態(實際上,它們`RawDllMain`通常甚至沒有 。 這是因為它們旨在「就像」它們實際存在於使用它們的應用程式中一樣。 它們在很大程度上是正在運行的應用程式的一部分,他們打算修改該應用程式的全域狀態。

OLE 控制件和其他 DLL 非常不同。 他們不想修改調用應用程式的狀態;因此,它們不想修改調用應用程式的狀態。調用它們的應用程式可能甚至不是 MFC 應用程式,因此可能沒有要修改的狀態。 這就是模組狀態切換被發明的原因。

對於從 DLL 匯出的函數(例如在 DLL 中啟動對話框的函數),您需要向函數的開頭添加以下代碼:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

這將將當前模組狀態與從[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)返回的狀態交換,直到當前作用域結束。

如果不使用AFX_MODULE_STATE宏,則 DLL 中的資源將出現問題。 根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 這個範本實際上會儲存在 DLL 中。 根本原因是 MFC 的模組狀態資訊尚未由AFX_MODULE_STATE宏切換。 資源控制代碼是從 MFC 的模組狀態復原。 由於未切換模組狀態而導致使用錯誤的資源控制代碼。

不需要將AFX_MODULE_STATE放入 DLL 中的每個函數中。 例如,`InitInstance`可以在應用程式中的 MFC 代碼調用,而不會AFX_MODULE_STATE因為`InitInstance``InitInstance`MFC 在返回之前自動轉移模組狀態,然後切換回。 所有消息映射處理程式也是如此。 常規 MFC DLL 實際上具有特殊的主視窗過程,可在路由任何消息之前自動切換模組狀態。

## <a name="process-local-data"></a>處理本地資料

如果不是 Win32s DLL 模型的困難,處理本地數據就不會那麼令人關注。 在 Win32 中,所有 DLL 共用其全域數據,即使由多個應用程式載入也是如此。 這與「真實」Win32 DLL 資料模型非常不同,該模型在每個附加到 DLL 的進程中,每個 DLL 都會獲得其數據空間的單獨副本。 為了增加複雜性,在 Win32s DLL 中分配給堆上的數據實際上是特定於過程的(至少就擁有權而言)。 請考慮以下資料與代碼:

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

請考慮如果上述代碼位於 DLL 中,並且 DLL 由兩個進程 A 和 B 載入(實際上可能是同一應用程式的兩個實例),會發生什麼情況。 通話`SetGlobalString("Hello from A")`。 因此,在進程 A 的上下`CString`文中 為資料分配記憶體。 請記住,自身是`CString`全域的 ,A 和 B 都可見。現在`GetGlobalString(sz, sizeof(sz))`B 呼叫 。 B 將能夠看到A集的數據。 這是因為 Win32 在像 Win32 這樣的進程之間沒有提供保護。 這是第一個問題;在許多情況下,不希望一個應用程序影響被視為由其他應用程式擁有的全域數據。

還有其他問題。 假設 A 現在退出。 當 A 退出時,"'字`strGlobal`串使用的記憶體可用於系統, 即,進程 A 分配的所有記憶體都由作業系統自動釋放。 它不被釋放,`CString`因為正在調用析構函數;它還沒有被調用。 它被釋放僅僅是因為分配它的應用程式離開了場景。 現在,如果`GetGlobalString(sz, sizeof(sz))`B 調用 ,它可能得不到有效的數據。 其他應用程式可能將該記憶體用於其他內容。

顯然,存在問題。 MFC 3.x 使用了一種稱為線程本地存儲 (TLS) 的技術。 MFC 3.x 將分配一個 TLS 索引,在 Win32s 下,該索引實際上充當進程本地存儲索引,即使不調用該索引,然後根據該 TLS 索引引用所有數據。 這與用於在 Win32 上儲存線程本地數據的 TLS 索引類似(有關該主題的詳細資訊,請參閱下文)。 這導致每個 MFC DLL 每個進程至少使用兩個 TLS 索引。 當您考慮載入許多 OLE 控制 DLL (OCX) 時,您很快就會耗盡 TLS 索引(只有 64 個可用)。 此外,MFC 必須將所有這些數據放在一個位置,在單個結構中。 它不是很可擴展,在使用TLS指數方面並不理想。

MFC 4.x 使用一組類範本來解決此問題,您可以圍繞應處理本地處理的數據"包裝"。 例如,上述問題可以通過書面解決:

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

MFC 分兩步實現此功能。 首先,Win32 __Tls\* __ API(TlsAlloc、TlsSetValue、TlsGetValue**TlsGetValue**等) 頂部有一個層,無論您有多少 DLL,每個進程只使用兩個**TlsAlloc****TlsSetValue**TLS 索引。 其次,`CProcessLocal`提供範本來存取此資料。 它覆蓋運算符>這是允許上面看到的直觀語法的原因。 所有由`CProcessLocal`換行的物件都必須派生自`CNoTrackObject`。 `CNoTrackObject`提供較低等級的分配器(**LocalAlloc**/**LocalFree**) 和虛擬析構函數,以便 MFC 可以在行程終止時自動銷毀進程本地物件。 如果需要其他清理,此類物件可以具有自定義析構函數。 上述示例不需要一個,因為編譯器將生成預設析構函數來銷毀嵌入`CString`的物件。

這種方法還有其他有趣的優點。 不僅所有`CProcessLocal`物件都自動銷毀,而且直到需要它們才構造它們。 `CProcessLocal::operator->`將在首次調用關聯物件時實例化它,並且不會很快。 在上面的示例中,這意味著在第一次`strGlobal``SetGlobalString``GetGlobalString`或調用之前不會構造 ''字串。 在某些情況下,這有助於減少 DLL 啟動時間。

## <a name="thread-local-data"></a>執行緒資料

與處理本地數據類似,當數據必須是給定線程的本地時,將使用線程本地數據。 也就是說,您需要訪問該數據的每個線程的單獨數據實例。 這可以多次用於代替廣泛的同步機制。 如果數據不需要由多個線程共用,則此類機制可能非常昂貴且沒有必要。 假設我們有一個`CString`物件(與上面的示例類似)。 我們可以透過用樣本包裝它來使其成為本地線程`CThreadLocal`:

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

如果`MakeRandomString`從兩個不同的線程調用,每個線程將以不同的方式"洗牌"字串,而不會干擾另一個線程。 這是因為實際上每個線程有一個`strThread`實例,而不僅僅是一個全域實例。

請注意如何使用引用捕獲`CString`位址一次,而不是每個迴圈反覆運算一次。 循環代碼可能使用`threadData->strThread`「無處不在」`str`, 但代碼的執行速度會慢得多。 當此類引用在循環中出現時,最好緩存對數據的引用。

類`CThreadLocal`範本使用相同的機制`CProcessLocal`, 執行和相同的實現技術。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
