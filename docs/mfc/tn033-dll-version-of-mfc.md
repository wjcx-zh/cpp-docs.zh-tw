---
title: TN033:MFC 的 DLL 版本
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: fda256043027dbff249cedf490b150b6ad30a5fb
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611099"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033:MFC 的 DLL 版本

此提示會說明如何使用 MFCxx.DLL 和 MFCxxD.DLL （其中 x 是 MFC 版本號碼） 共用動態連結程式庫與 MFC 應用程式和 MFC 擴充 Dll。 如需有關 MFC 的標準 Dll 的詳細資訊，請參閱[將 MFC 當成 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

這個技術提示涵蓋三個層面的 Dll。 這兩個適用於更進階的使用者：

- [如何建置 MFC 擴充 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [如何建置使用 MFC 的 DLL 版本的 MFC 應用程式](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [MFC 共用動態連結程式庫的方式實作](#_mfcnotes_how_the_mfc30.dll_is_implemented)

如果您有興趣建置使用可搭配非 MFC 應用程式 （這稱為 MFC DLL） 的 MFC 的 DLL，請參閱[技術的附註 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>MFCxx.DLL 支援的概觀：術語和檔案

**MFC DLL**:您可以使用標準的 MFC DLL 來建立使用 MFC 類別的一些獨立 DLL。 跨應用程式/DLL 界限的介面"C"的介面，而且是一個 MFC 應用程式並沒有用戶端應用程式。

這是支援在 MFC 1.0 中的 DLL 支援的版本。 所述[技術提示 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)和 MFC 進階概念範例[DLLScreenCap](../overview/visual-cpp-samples.md)。

> [!NOTE]
> 截至 VisualC++版本 4.0、 詞彙**USRDLL**已經過時，已取代靜態連結至 MFC 之標準 MFC DLL。 您可能也會建立一般動態連結至 MFC 的 MFC DLL。

MFC 3.0 （和更新版本） 支援 MFC 的標準 Dll 包括 OLE 和資料庫類別的新功能。

**AFXDLL**:這也稱為共用版本的 MFC 程式庫。 這是 MFC 2.0 中加入新的 DLL 支援。 MFC 程式庫本身是數 （如下所述） 的 Dll 和用戶端應用程式或 DLL 動態連結它所需的 Dll。 跨應用程式/DLL 界限的介面是C++/MFC 類別介面。 用戶端應用程式必須是 MFC 應用程式。 這可支援所有的 MFC 3.0 功能 (例外狀況：UNICODE 不是支援資料庫類別）。

> [!NOTE]
> 截至 Visual C++ 4.0 版，這種類型的 DLL 會稱為 「 延伸模組 DLL。 」

本附註會使用 MFCxx.DLL 參考整個 MFC DLL 集合，其中包括：

- 偵錯：MFCxxD.DLL （結合） 和 MFCSxxD.LIB （靜態）。

- 版本：（合併） MFCxx.DLL 和 MFCSxx.LIB （靜態）。

- Unicode 偵錯：MFCxxUD.DLL （結合） 和 MFCSxxD.LIB （靜態）。

- Unicode 版本：MFCxxU.DLL （結合） 和 MFCSxxU.LIB （靜態）。

> [!NOTE]
> MFCSxx [U] [D]。LIB 程式庫會在與 MFC 一起共用的 Dll。 這些程式庫包含必須以靜態方式連結至 DLL 的應用程式的程式碼。

應用程式會連結至對應的匯入程式庫：

- 偵錯：MFCxxD.LIB

- 版本：MFCxx.LIB

- Unicode 偵錯：MFCxxUD.LIB

- Unicode 版本：MFCxxU.LIB

「 MFC 擴充 DLL 」 是建置在 MFCxx.DLL DLL （和/或其他 MFC 的共用 Dll）。 這裡的 MFC 元件架構就會執行。 如果您從 MFC 類別，衍生的有用類別，或建立另一個類似 MFC 的工具組，您可以將它放在 DLL 中。 DLL 使用 MFCxx.DLL，，做為執行 ultimate 的用戶端應用程式。 如此可重複使用的分葉類別、 可重複使用的基底類別，以及可重複使用的檢視/文件類別。

## <a name="pros-and-cons"></a>優缺點

為什麼您應該使用 MFC 的共用的版本

- 使用共用的程式庫，可能會導致較小的應用程式 （使用大部分的 MFC 程式庫的最小應用程式會是小於 10 K）。

- 共用的版本的 MFC 支援 MFC 擴充 Dll 和 MFC 的標準 Dll。

- 建立使用共用的 MFC 程式庫的應用程式的速度比建置靜態連結的 MFC 應用程式，因為它不需要連結 MFC 本身。 這是特別**偵錯**其中連結器必須壓縮偵錯資訊的組建 — 藉由連結的 DLL 已經包含偵錯資訊，有較少的偵錯訊息至精簡您的應用程式內。

為什麼您不應該使用 MFC 的共用的版本：

- 傳送使用共用的程式庫的應用程式需要您在出貨 MFCxx.DLL （以及其他） 與您的程式庫。 MFCxx.DLL 等許多 Dll，可以自由轉散發，但您仍然必須安裝此 DLL 中您的安裝程式。 此外，您必須將 MSVCRTxx.DLL，其中包含會使用您的程式和 MFC Dll 本身的 C 執行階段程式庫。

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> 如何撰寫 MFC 擴充 DLL

MFC 擴充 DLL 是包含類別和函式寫入美化它們的 MFC 類別功能的 DLL。 MFC 擴充 DLL 會使用共用的 MFC Dll 相同的方式，應用程式所使用的是，使用一些其他考量：

- 建置程序是類似於建立使用共用的 MFC 程式庫有幾個其他編譯器和連結器選項的應用程式。

- MFC 擴充 DLL 並沒有`CWinApp`-衍生的類別。

- MFC 擴充 DLL 必須提供一種特殊`DllMain`。 AppWizard 提供`DllMain`函式，您可以修改。

- MFC 擴充 DLL 通常會提供初始化常式，以建立`CDynLinkLibrary`如果 MFC 擴充 DLL 想要匯出`CRuntimeClass`es 或應用程式的資源。 在衍生的類別的`CDynLinkLibrary`如果由 MFC 擴充 DLL 必須維護每個應用程式資料可以使用。

在下面詳細說明這些考量。 您也應該參閱 MFC 進階概念範例[DLLHUSK](../overview/visual-cpp-samples.md)因為它也說明了：

- 建立使用共用的程式庫的應用程式。 (DLLHUSK。EXE 是動態連結至 MFC 程式庫，以及其他 Dll 的 MFC 應用程式。）

- 建置 MFC 擴充 DLL。 (請注意特殊旗標時，例如`_AFXEXT`，用於建置 MFC 擴充 DLL)

- 兩個範例 MFC 擴充 Dll。 其中說明 MFC 擴充 DLL 與限制的匯出 (TESTDLL1) 和其他顯示匯出整個類別介面 (TESTDLL2) 的基本結構。

用戶端應用程式和任何 MFC 擴充 Dll 必須使用 MFCxx.DLL 相同版本。 您應該遵循的慣例 MFC DLL，並提供這兩個偵錯和零售 (/release) MFC 延伸模組 DLL 的版本。 這可讓用戶端程式，來建置應用程式的偵錯和零售版本，並將它們連結與適當的偵錯或零售版本的所有 Dll。

> [!NOTE]
>  因為C++名稱的損害以及匯出問題，從 MFC 擴充 DLL 的 [匯出] 清單可能會不同相同 DLL 的偵錯和零售版本和 Dll 之間的不同平台。 零售 MFCxx.DLL 有大約 2000年匯出的進入點，偵錯 MFCxxD.DLL 大約 3000 已匯出進入點。

### <a name="quick-note-on-memory-management"></a>記憶體管理上的快速提示

標題為 「 記憶體管理，」 這個技術提示結尾附近的章節將說明 MFC 的共用版本 MFCxx.DLL 的實作。 您需要知道實作只是 MFC 延伸模組 DLL 此處所述的資訊。

MFCxx.DLL 和所有 MFC 擴充 Dll 載入到用戶端應用程式的位址空間會使用相同的記憶體配置器、 資源載入和其他 MFC 的 「 全域 」 狀態，彷彿在相同的應用程式中。 這十分重要，因為非 MFC DLL 程式庫和以靜態方式連結至 MFC 的標準 MFC Dll 執行完全相反的且有移出它自己的記憶體集區每個配置的 DLL。

如果 MFC 擴充 DLL 中配置記憶體，然後該記憶體可以自由地相互摻雜與其他應用程式配置的物件。 此外，如果使用共用的 MFC 程式庫的應用程式當機，作業系統的保護會維護共用 DLL 任何其他 MFC 應用程式的完整性。

同樣地其他 「 全域 」 的 MFC 狀態，例如目前的可執行檔載入資源，也會用戶端應用程式和所有 MFC 擴充 Dll，以及 MFCxx.DLL 本身之間共用。

### <a name="building-an-mfc-extension-dll"></a>建置 MFC 擴充 DLL

您可以使用 AppWizard 建立 MFC 擴充 DLL 專案，而且它會自動產生適當的編譯器和連結器設定。 這是也會產生`DllMain`函式，您可以修改。

如果您要將現有的專案轉換成 MFC 擴充 DLL，開始建置應用程式使用共用的版本的 MFC 的標準規則，然後執行下列動作：

- 新增 **/D_AFXEXT**編譯器旗標。 在 專案屬性 對話方塊中，選取 C /C++節點。 然後選取前置處理器的類別。 新增`_AFXEXT`到定義的巨集 欄位中，每個項目以分號分隔。

- 移除 **/Gy**編譯器參數。 在 專案屬性 對話方塊中，選取 C /C++節點。 然後選取程式碼產生類別。 請確定未啟用 「 啟用函式階層連結 」 的選項。 這會讓您更輕鬆地匯出類別，因為連結器將不會移除未參考的函式。 如果原始的專案用來建置一般 MFC DLL 以靜態方式連結至 MFC，變更 **[d] /MT**編譯器選項，來 **/MD [d]**。

- 建置使用匯出程式庫 **/DLL**連結選項。 這會設定當您建立新的目標指定為目標類型的 Win32 動態連結程式庫。

### <a name="changing-your-header-files"></a>變更標頭檔

MFC 擴充 DLL 的目標通常是匯出一些通用的功能，可以使用該功能的一或多個應用程式。 這全然取決於要匯出的類別和全域函式可供用戶端應用程式。

若要這樣做，您必須確定每個成員函式已標示為匯入或匯出為適當。 這需要特殊宣告：`__declspec(dllexport)`和`__declspec(dllimport)`。 當用戶端應用程式使用您的類別時，您想要宣告為`__declspec(dllimport)`。 建置 MFC 擴充 DLL 本身時，它們應該宣告為`__declspec(dllexport)`。 此外，函式必須實際上匯出，以便在載入時用戶端程式繫結至它們。

若要匯出整個類別，使用`AFX_EXT_CLASS`類別定義中。 定義此巨集可以是 framework 所`__declspec(dllexport)`時`_AFXDLL`並`_AFXEXT`定義，但定義為`__declspec(dllimport)`時`_AFXEXT`未定義。 `_AFXEXT` 建置您的 MFC 擴充 DLL 時，只定義如上面所述。 例如: 

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>不會匯出整個類別

有時候您可能要匯出只是必要的個別成員您的類別。 例如，如果您要匯出`CDialog`-衍生的類別，您可能只需要將匯出的建構函式和`DoModal`呼叫。 您可以匯出使用 DLL 的這些成員。DEF 檔案，但您也可以使用`AFX_EXT_CLASS`中相同的方式在您要匯出的個別成員。

例如: 

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

當您這樣做時，您可能會遇到其他問題，因為您不再想要匯出類別的所有成員。 問題的方式是 MFC 巨集工作。 有幾個 MFC 的協助程式巨集實際宣告或定義的資料成員。 因此，這些資料成員也必須從您的 DLL 匯出。

比方說，DECLARE_DYNAMIC 巨集定義，如下所示建置 MFC 擴充 DLL 時：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

開頭的 「 靜態`AFX_DATA`」 宣告在您的類別內的靜態物件。 若要正確匯出這個類別，並從用戶端存取的執行階段資訊。EXE，您需要匯出這個靜態物件。 因為靜態物件會使用修飾詞宣告`AFX_DATA`，您只需要定義`AFX_DATA`要`__declspec(dllexport)`建置 DLL 時，它定義為`__declspec(dllimport)`建置您的用戶端可執行檔時。

如上所述，`AFX_EXT_CLASS`已定義以這種方式。 您只需要重新定義`AFX_DATA`是與相同`AFX_EXT_CLASS`解決您的類別定義。

例如: 

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS
class CExampleView : public CView
{
    DECLARE_DYNAMIC()
    // ... class definition ...
};
#undef  AFX_DATA
#define AFX_DATA
```

一律會使用 MFC`AFX_DATA`符號定義在其巨集，因此這項技術可用於所有這類案例的資料項目。 比方說，它適用於 DECLARE_MESSAGE_MAP。

> [!NOTE]
> 如果您要匯出整個類別，而不是所選的類別的成員，靜態資料成員會自動匯出。

您可以使用相同的技巧，自動匯出`CArchive`擷取運算子使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 巨集的類別。 匯出封存運算子的類別宣告方括號 (位於。H 檔案中） 為下列程式碼：

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>_AFXEXT 的限制

您可以使用 _**AFXEXT** MFC 延伸模組 Dll 只要您不需要多個圖層的 MFC 擴充 Dll 的前置處理器符號。 如果您有 MFC 擴充 Dll 呼叫，或衍生自類別，在您自己的 MFC 擴充 Dll，然後從 MFC 類別衍生，您必須使用您自己的前置處理器符號，以避免模稜兩可。

問題是，在 Win32 中，您必須明確宣告為任何資料`__declspec(dllexport)`它是否要從 DLL 匯出和`__declspec(dllimport)`它是否要從 DLL 匯入。 當您定義`_AFXEXT`，MFC 標頭，確定`AFX_EXT_CLASS`正確定義。

當您擁有多個圖層，一個符號這類`AFX_EXT_CLASS`並不足夠，因為 MFC 擴充 DLL 可能會匯出新的類別，以及從另一個 MFC 擴充 DLL 匯入其他類別。 為了解決這個問題，使用特殊的前置處理器符號，指出您要建置 DLL 本身而非使用 DLL。 例如，假設有兩個 MFC 擴充 Dll，A.DLL、 B.DLL。 每個分別匯出 A.H 和 B.H 中的某些類別。 B.DLL 使用 A.DLL 的類別。 標頭檔看起來像這樣：

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

建置 A.DLL 時，它以 **/DA_IMPL**而且 B.DLL 建置時，它會根據 **/DB_IMPL**。 藉由使用不同的符號，每個 DLL，CExampleB 匯出且 CExampleA 建置 B.DLL 時匯入。 CExampleA 是匯出時建置 A.DLL 和 B.DLL （或是某些其他用戶端） 使用時，匯入。

使用內建時，就無法執行這種分層`AFX_EXT_CLASS`和`_AFXEXT`前置處理器符號。 上面所述的技巧可解決此問題的方式沒有不同於建置其 OLE、 資料庫和網路 MFC 擴充 Dll 時，會使用 MFC 本身的機制。

### <a name="not-exporting-the-entire-class"></a>不會匯出整個類別

同樣地，您必須採取特別注意，當您不想要匯出整個類別。 您必須確定建立的 MFC 巨集的必要資料項目都正確匯出。 這可以藉由重新定義`AFX_DATA`特定類別的巨集。 這應該不會匯出整個類別的任何時間。

例如: 

```cpp
// A.H
#ifdef A_IMPL
    #define CLASS_DECL_A  _declspec(dllexport)
#else
    #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
    DECLARE_DYNAMIC()
    CLASS_DECL_A int SomeFunction();
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

以下是您應該為您的 MFC 延伸模組 DLL 將放在主要原始程式檔的實際程式碼。 它應該會包含標準之後。 請注意，當您使用 AppWizard 建立的 MFC 擴充 DLL 的起始檔案時，它提供`DllMain`您。

```cpp
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      // MFC extension DLL one-time initialization
      if (!AfxInitExtensionModule(
             extensionDLL, hInstance))
         return 0;

      // TODO: perform other initialization tasks here
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      // MFC extension DLL per-process termination
      AfxTermExtensionModule(extensionDLL);

      // TODO: perform other cleanup tasks here
   }
   return 1;   // ok
}
```

呼叫`AfxInitExtensionModule`擷取模組執行階段類別 (`CRuntimeClass`結構) 以及其物件處理站 (`COleObjectFactory`物件) 使用更新版本時`CDynLinkLibrary`建立物件。 （選擇性） 呼叫`AfxTermExtensionModule`可讓 MFC 清理 MFC 擴充 DLL 時每個處理序中斷連結 (或的卸載 DLL 時的處理序結束時，恰好`FreeLibrary`呼叫) 從 MFC 擴充 DLL。 因為大部分的 MFC 擴充 Dll 不會以動態方式載入 （通常，他們所連結透過其匯入程式庫），呼叫`AfxTermExtensionModule`通常並不需要。

如果您的應用程式載入，並動態釋放 MFC 擴充 Dll，務必呼叫`AfxTermExtensionModule`如上所示。 也請務必使用`AfxLoadLibrary`並`AfxFreeLibrary`(而不是 Win32 函式`LoadLibrary`和`FreeLibrary`) 如果您的應用程式使用多個執行緒，或以動態方式載入 MFC 擴充 DLL。 使用`AfxLoadLibrary`和`AfxFreeLibrary`確保執行載入和卸載 MFC 擴充 DLL 時的啟動和關閉程式碼不損毀的通用的 MFC 狀態。

標頭檔 AFXDLLX 中。H 包含特殊的定義，在 MFC 擴充 Dll，例如的定義中使用的結構`AFX_EXTENSION_MODULE`和`CDynLinkLibrary`。

全域*extensionDLL*必須宣告所示。 不同於 MFC 的 16 位元版本，您可以配置記憶體，並在此期間，呼叫 MFC 的函式，因為 MFCxx.DLL 完全初始化時您`DllMain`呼叫。

### <a name="sharing-resources-and-classes"></a>共用資源和類別

簡單的 MFC 擴充 Dll 需要只將少數低頻寬函式匯出至用戶端應用程式而不需要其他。 大量的 Dll 可能會想要匯出的資源更多使用者介面和C++用戶端應用程式的類別。

匯出資源是透過資源的清單。 每個應用程式是單向連結的清單`CDynLinkLibrary`物件。 大部分的標準的 MFC 實作載入資源時尋找資源，尋找第一個在目前的資源模組 (`AfxGetResourceHandle`)，如果找不到查核行程的清單`CDynLinkLibrary`嘗試載入所要求的資源的物件。

動態建立C++物件指定C++類別名稱是類似。 MFC 物件還原序列化機制必須將所有`CRuntimeClass`物件註冊，讓它可以重新建構所動態建立C++已儲存的內容稍早根據所需型別物件。

如果您想要使用您的 MFC 擴充 DLL 中的類別，用戶端應用程式`DECLARE_SERIAL`，則您必須匯出您的類別會顯示用戶端應用程式。 這也是藉由查核`CDynLinkLibrary`清單。

在 MFC 進階概念範例的情況下[DLLHUSK](../overview/visual-cpp-samples.md)，清單看起來像：

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

MFCxx.DLL 是根據資源和類別清單，通常是最後一個項目。 MFCxx.DLL 包含所有的標準 MFC 資源，包括所有標準命令 id 的提示字串。 Dll 和用戶端應用程式本身不需要將它放在清單結尾可讓他們自己的標準 MFC 資源，但若要依賴 MFCxx.DLL 中的共用資源而的複本。

將資源和所有 dll 的類別名稱合併到用戶端應用程式的命名空間有的缺點是，您必須小心什麼識別碼或您選擇的名稱。 您可以不用說停用這項功能不會匯出您的資源或`CDynLinkLibrary`用戶端應用程式的物件。 [DLLHUSK](../overview/visual-cpp-samples.md)範例使用多個標頭檔來管理共用的資源命名空間。 請參閱[技術的附註 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)如需有關使用共用的資源檔的秘訣。

### <a name="initializing-the-dll"></a>初始化 DLL

如先前所述，您通常會想要建立`CDynLinkLibrary`才能匯出您的資源和類別，用戶端應用程式的物件。 您必須提供初始化的 DLL 匯出的進入點。 最低限度，這是 void 的常式，它會採用任何引數，並傳回任何內容，但它可以是您喜歡的任何項目。

每個想要使用您的 DLL 的用戶端應用程式必須呼叫此初始化常式中，如果您使用此方法。 您可能也會配置這`CDynLinkLibrary`物件在您`DllMain`後方呼叫`AfxInitExtensionModule`。

初始化常式必須建立`CDynLinkLibrary`物件中目前的應用程式堆積，連線到您的 MFC 延伸模組 DLL 的資訊。 這可以透過下列來完成：

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

常式的名稱， *InitXxxDLL*在此範例中，可以是任何您想要的項目。 不需要**extern"C"**，但如此可讓您更輕鬆地維護的 [匯出] 清單。

> [!NOTE]
> 如果您使用您從一般 MFC DLL 的 MFC 擴充 DLL 時，您必須匯出此初始化函式。 使用任何延伸模組 DLL 的 MFC 類別或資源之前，必須與一般 MFC DLL 呼叫此函數。

### <a name="exporting-entries"></a>匯出的項目

若要匯出您的類別的簡單方式是使用`__declspec(dllimport)`和`__declspec(dllexport)`的每個類別和您想要匯出的全域函式。 這可讓您更輕鬆，但效率比命名 （如下所述） 的每個進入點，因為您可以控制哪些函式會匯出較少，而且您無法依序數匯出的函式。 TESTDLL1 和 TESTDLL2 使用這個方法將其項目。

更有效率的方法 （和 MFCxx.DLL 所使用的方法） 是藉由命名每個項目中的以手動方式匯出每個項目。DEF 檔案。 因為我們要從我們 （也就是並非所有功能） 的 DLL 匯出選擇性的匯出，我們必須決定我們想要匯出哪一個特定介面。 這是很困難，因為您必須指定至連結器損害的名稱中的項目表單中。DEF 檔案。 不會匯出任何C++類別，除非您真的需要對此符號連結。

如果您嘗試匯出C++類別使用。DEF 檔案之前，您可能想要開發的工具，以自動產生這份清單。 這可以使用兩階段連結程序。 連結您一次使用沒有匯出的 DLL，並讓連結器產生。對應檔。 。對應檔案可以用來產生一份應匯出的函式，因此與一些重新排列，它可以用來產生您的匯出項目，如您。DEF 檔案。 （雖然它不是完全自動的而且需要某些手動微調每隔一段時間），MFCxx.DLL 和 OLE 及數千在數目、 資料庫 MFC 擴充 Dll 的 [匯出] 清單所產生的程序。

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs。CDynLinkLibrary

MFC 擴充 DLL 並沒有`CWinApp`-衍生自己的物件; 而是它必須能與`CWinApp`-衍生的用戶端應用程式的物件。 這表示用戶端應用程式擁有的主要訊息幫浦，閒置迴圈，依此類推。

如果您的 MFC 擴充 DLL 需要維護額外的資料，每個應用程式，您可以衍生新的類別，從`CDynLinkLibrary`和 InitXxxDLL 常式上方的描述中建立它。 DLL 執行時，可以檢查目前的應用程式清單`CDynLinkLibrary`來找出該特定的 MFC 延伸模組 DLL 的物件。

### <a name="using-resources-in-your-dll-implementation"></a>您的 DLL 實作中使用的資源

如上所述，預設資源負載，將逐步引導的清單`CDynLinkLibrary`尋找第一個 EXE 或 DLL，具有所要求的資源的物件。 MFC 的所有 Api，以及內部的程式碼會使用所有`AfxFindResourceHandle`從頭到尾參與以找出任何資源，無論它可能在此對話方塊位於 [資源] 清單。

如果您想要只從特定位置載入資源，使用 Api`AfxGetResourceHandle`和`AfxSetResourceHandle`儲存舊的控制代碼，並設定新的控制代碼。 請務必還原舊的資源控制代碼，然後返回用戶端應用程式。 此範例 TESTDLL2 會使用這種方法來明確載入功能表。

逐一查看清單也有缺點，它會稍微慢一點，而且需要管理資源 ID 範圍。 它的優點是連結到數個 MFC 擴充 Dll 用戶端應用程式可以使用任何提供 DLL 的資源，而不需要指定 DLL 的執行個體控制代碼。 `AfxFindResourceHandle` API 用於逐一查看 [資源] 清單，尋找指定的相符項。 它會使用名稱和資源類型，並傳回其第一次發現所在的資源控制代碼 （或 NULL）。

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> 撰寫的應用程式使用的 DLL 版本

### <a name="application-requirements"></a>應用程式的需求

使用 MFC 的共用的版本的應用程式必須遵循一些簡單的規則：

- 它必須要有`CWinApp`物件，並依照訊息幫浦的標準規則。

- 必須將其編譯使用一組必要的編譯器旗標 （請參閱下文）。

- 它必須連結 MFCxx 匯入程式庫。 藉由設定必要的編譯器旗標，MFC 標頭在連結階段決定應用程式應該連結的程式庫。

- 若要執行可執行檔，MFCxx.DLL 必須在路徑上或在 Windows 系統目錄中。

### <a name="building-with-the-development-environment"></a>建置與開發環境

如果您使用標準的預設值的最內部的 makefile，您可以輕鬆地將專案變更為建置的 DLL 版本。

下列步驟假設您有與 NAFXCWD 連結正常運作的 MFC 應用程式。LIB （適用於偵錯） 和 NAFXCW。LIB （適用於零售版），而且您想要將它轉換成使用共用的版本的 MFC 程式庫。 您正在執行視覺效果C++環境，而且有內部的專案檔。

1. 在 **專案**功能表上，按一下**屬性**。 在 **一般**頁面**專案預設值**，設定為 Microsoft Foundation Classes**使用 MFC 的共用 dll** (MFCxx(d).dll)。

### <a name="building-with-nmake"></a>使用 NMAKE 來建置

如果您使用外部 makefile 功能的視覺效果C++，或使用 NMAKE 直接，您必須編輯您的 makefile，來支援編譯器和連結器選項

必要的編譯器旗標：

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

標準的 MFC 標頭需要這個符號定義：

- **/MD**應用程式必須使用 C 執行階段程式庫的 DLL 版本

所有其他編譯器旗標會遵循 MFC 預設值 (例如進行偵錯 _DEBUG)。

編輯程式庫連結器清單。 變更 NAFXCWD。以 MFCxxD.LIB LIB，並變更 NAFXCW。MFCxx.LIB LIB。 取代 LIBC。LIB MSVCRT 使用。LIB。 當使用任何其他的 MFC 程式庫是很重要，要放置 MFCxxD.LIB**之前**任何 C 執行階段程式庫。

選擇性地加入 **/D_AFXDLL**至您的零售和偵錯資源編譯器選項 (實際上會編譯具有資源的那個 **/R**)。 這可讓您最終可執行檔較小共用 MFC Dll 中的資源。

進行這些變更之後，需要完整的重建。

### <a name="building-the-samples"></a>建置範例

大部分的 MFC 範例程式可以從 視覺效果來建立C++或從共用的 NMAKE 相容 MAKEFILE，從命令列。

若要轉換的這些範例，以使用 MFCxx.DLL 任何，您可以載入。MAK 檔案到視覺效果C++，並設定專案選項，如上面所述。 如果您使用 NMAKE 組建，您可以指定"AFXDLL = 1"上 NMAKE 命令列，並且會建立使用共用的 MFC 程式庫範例。

MFC 進階概念範例[DLLHUSK](../overview/visual-cpp-samples.md)使用 MFC 的 DLL 版本所建置。 此範例不只說明如何建置使用 MFCxx.DLL，連結的應用程式，但它也會說明 MFC DLL 的封裝選項，例如 MFC 擴充 Dll，這個技術提示稍後所述的其他功能。

### <a name="packaging-notes"></a>封裝資訊

零售版本的 Dll (MFCxx [U]。DLL) 都可以自由轉散發。 不能自由轉散發 Dll 的偵錯版本，並應該僅在您的應用程式開發期間使用。

提供偵錯 Dll 的偵錯資訊。 藉由使用視覺效果C++偵錯工具，您可以追蹤您的應用程式，以及 DLL 執行。 版本的 Dll (MFCxx [U]。DLL) 並包含偵錯資訊。

如果您自訂或重建 Dll 時，您應呼叫它們的項目"MFCxx 「 MFC SRC 檔 MFCDLL 以外。MAK 描述組建選項，並包含重新命名 DLL 的邏輯。 重新命名這些檔案是必要的因為這些 Dll 有可能共用許多的 MFC 應用程式。 讓您自訂的 MFC Dll 取代版本安裝在系統上可能會中斷另一個使用共用的 MFC Dll 的 MFC 應用程式。

建議您不要重建 MFC Dll。

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> 如何實作 MFCxx.DLL

下節將說明如何實作 MFC DLL （MFCxx.DLL 和 MFCxxD.DLL）。 了解的詳細資料也不很重要，如果您想要執行是使用您的應用程式中的 MFC DLL。 詳細資料不是不可或缺的了解如何撰寫 MFC 擴充 DLL，但了解此實作可能會協助您撰寫您自己的 DLL。

### <a name="implementation-overview"></a>實作概觀

MFC DLL 其實 MFC 擴充 DLL 的特殊案例，如上面所述。 它有非常大量的大量類別的匯出。 有其他幾點我們只不過在 MFC DLL，可讓您更多特殊比一般的 MFC 擴充 DLL。

### <a name="win32-does-most-of-the-work"></a>Win32 會負責大部分的工作

MFC 的 16 位元版本需要一些特殊的技術，包括每個應用程式資料在堆疊區段中，某些 80x86 組譯程式碼，每個處理序例外狀況內容和其他技術所建立的特殊區段。 Win32 直接支援同處理序資料在 DLL 中，您想大部分的情況。 大部分的情況下 MFCxx.DLL 是只要 NAFXCW。封裝在 DLL 中的程式庫。 如果您查看 MFC 原始碼時，您會發現很少 #ifdef _AFXDLL，因為有很少需要進行的特殊情況。 會有特別處理 Win32，Windows 3.1 （亦稱為 win32） 的特殊案例。 Win32 並不支援每個處理程序 DLL 的資料，因此 MFC DLL 必須使用執行緒區域儲存區 (TLS) 來取得處理程序的本機資料的 Win32 Api 直接。

### <a name="impact-on-library-sources-additional-files"></a>在 程式庫來源、 其他檔案的影響

所產生的影響 **_AFXDLL**上正常的 MFC 類別程式庫來源和標頭版本是相當小。 沒有特殊版的檔案 (AFXV_DLL。H），以及額外的標頭檔 (AFXDLL_。H） 包含主要 AFXWIN。H 標頭。 AFXDLL_。H 標頭都會併入`CDynLinkLibrary`類別和其他實作詳細資料，這兩者的`_AFXDLL`應用程式和 MFC 擴充 Dll。 AFXDLLX。建置 MFC 擴充 Dll （如需詳細資訊請參閱以上） 提供 H 標頭。

MFC SRC 的 MFC 程式庫的一般來源具有一些額外的條件式程式碼底下`_AFXDLL`#ifdef。 其他的原始程式檔 (DLLINIT。CPP) 包含額外的 DLL 初始化程式碼和其他 MFC 的共用版本的連接。

若要建置 MFC 的共用的版本，提供額外的檔案。 （請參閱下列有關如何建置 DLL 的詳細資料。）

- 兩個。DEF 檔案用來匯出 MFC DLL 的進入點，供偵錯 (MFCxxD.DEF)，然後放開 (MFCxx.DEF) 版本的 DLL。

- 。RC 檔 (MFCDLL。RC) 會包含所有標準的 MFC 資源和 VERSIONINFO 資源 dll。

- 答:。CLW 檔案 (MFCDLL。CLW) 會提供使用 ClassWizard 允許瀏覽的 MFC 類別。 注意： 這項功能不是專門針對 MFC 的 DLL 版本。

### <a name="memory-management"></a>記憶體管理

使用 MFCxx.DLL 的應用程式會使用常見的記憶體配置器 MSVCRTxx.DLL，共用的 C 執行階段 DLL 所提供。 應用程式、 任何 MFC 擴充 Dll 和 MFC Dll 本身以及使用此共用的記憶體配置器。 藉由使用共用的 DLL 進行記憶體配置，MFC Dll 可以配置應用程式，反之亦然，稍後會釋放的記憶體。 因為應用程式和 DLL 必須使用相同的配置器，您不應該覆寫C++全域**new 運算子**或是**運算子 delete**。 相同的規則會套用到其餘的 C 執行階段記憶體配置常式 (例如**malloc**， **realloc**，**免費**，等等)。

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>序數和類別 __declspec （dllexport） 和 DLL 命名

我們不會使用`class` **__declspec （dllexport)** 功能C++編譯器。 相反地，匯出清單會包含的類別程式庫來源 （MFCxx.DEF 和 MFCxxD.DEF）。 會匯出這些選取集合的進入點 （函式和資料）。 其他符號，例如 MFC 私用實作函式或類別，不會匯出所有匯出都由序數沒有常駐 」 或 「 非常駐名稱表格中的字串名稱。

使用`class` **__declspec （dllexport)** 可能可行的替代方案建置較小的 Dll，但若為大型的 DLL，例如 MFC 中，預設值匯出機制具有效率和容量限制。

這全都表示是功能的什麼，我們可以將封裝大量版本僅約 800 KB，而不會影響多項執行或載入速度的 MFCxx.DLL 中。 MFCxx.DLL 會較大的 100 K 這項技術尚未使用。 這也讓您能夠新增其他的進入點的結尾。允許簡單的版本控制，而不會危害速度和規模的效率依序數匯出的定義檔。 MFC 類別庫中的主要版本修訂，將程式庫名稱。 也就是 MFC30。DLL 是包含 3.0 版的 MFC 類別程式庫的可轉散發 DLL。 此 dll，升級說，假設的 MFC 3.1 中，DLL 就會命名為 MFC31。DLL 改。 同樣地，如果您修改以產生自訂版本的 MFC DLL 的 MFC 原始程式碼時，便需要使用不同的名稱 （，最好是一個不在名稱中的 「 MFC 」）。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
