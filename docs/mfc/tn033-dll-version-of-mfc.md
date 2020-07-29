---
title: TN033：MFC 的 DLL 版本
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: c627f891efc893f4eb8dae4bfb0b3b78f7af1a46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215929"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033：MFC 的 DLL 版本

此附注說明如何使用 MFCxx.DLL 和 MFCxxD.DLL （其中 x 是 MFC 版本號碼）與 MFC 應用程式和 MFC 延伸 Dll 共用動態連結程式庫。 如需一般 MFC Dll 的詳細資訊，請參閱[使用 MFC 做為 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

本技術提示涵蓋 Dll 的三個層面。 最後兩個適用于較先進的使用者：

- [如何建立 MFC 延伸模組 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [如何建立使用 MFC DLL 版本的 MFC 應用程式](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [如何實作為 MFC 共用動態連結程式庫](#_mfcnotes_how_the_mfc30.dll_is_implemented)

如果您想要使用可搭配非 MFC 應用程式使用的 MFC 來建立 DLL （這稱為一般的 MFC DLL），請參閱[技術附注 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>MFCxx.DLL 支援的總覽：術語和檔案

**標準 MFC dll**：您可以使用一般 mfc dll，利用一些 mfc 類別來建立獨立 DLL。 跨應用程式/DLL 界限的介面是 "C" 介面，而用戶端應用程式不一定要是 MFC 應用程式。

這是 MFC 1.0 中支援的 DLL 支援版本。 如[技術提示 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)和 MFC Advanced 概念範例[DLLScreenCap](../overview/visual-cpp-samples.md)中所述。

> [!NOTE]
> 從 Visual C++ 版本4.0， **USRDLL**一詞已過時，並已由以靜態方式連結至 mfc 的標準 MFC DLL 取代。 您也可以建立可動態連結至 MFC 的標準 MFC DLL。

MFC 3.0 （和更新版本）支援具有所有新功能的標準 MFC Dll，包括 OLE 和資料庫類別。

**AFXDLL**：這也稱為「MFC 程式庫」的共用版本。 這是 MFC 2.0 中新增的新 DLL 支援。 MFC 程式庫本身位於數個 Dll 中（如下所述），而用戶端應用程式或 DLL 會動態地連結所需的 Dll。 跨應用程式/DLL 界限的介面是 c + +/MFC 類別介面。 用戶端應用程式必須是 MFC 應用程式。 這支援所有 MFC 3.0 功能（例外狀況：資料庫類別不支援 UNICODE）。

> [!NOTE]
> 從 Visual C++ 版本4.0，這種類型的 DLL 稱為「延伸 DLL」。

此附注會使用 MFCxx.DLL 來參考整個 MFC DLL 集，其中包括：

- Debug： MFCxxD.DLL （結合）和 MFCSxxD （靜態）。

- 版本： MFCxx.DLL （結合）和 MFCSxx （靜態）。

- Unicode Debug： MFCxxUD.DLL （結合）和 MFCSxxD （靜態）。

- Unicode 版本： MFCxxU.DLL （結合）和 MFCSxxU （靜態）。

> [!NOTE]
> MFCSxx [U] [D]。LIB 程式庫會與 MFC 共用 Dll 搭配使用。 這些程式庫包含必須以靜態方式連結至應用程式或 DLL 的程式碼。

應用程式會連結至對應的匯入程式庫：

- Debug： MFCxxD. LIB

- 版本： MFCxx .LIB

- Unicode Debug： MFCxxUD. LIB

- Unicode 版本： MFCxxU

「MFC 延伸 DLL」是以 MFCxx.DLL （和/或其他 MFC 共用 Dll）為基礎的 DLL。 這裡的 MFC 元件架構會在中啟動。 如果您從 MFC 類別衍生有用的類別，或建立另一個類似 MFC 的工具組，您可以將它放在 DLL 中。 該 DLL 會使用 MFCxx.DLL，就像旗艦版用戶端應用程式一樣。 這允許可重複使用的分葉類別、可重複使用的基類，以及可重複使用的視圖/檔類別。

## <a name="pros-and-cons"></a>優缺點

為什麼要使用 MFC 的共用版本

- 使用共用程式庫可能會產生較小的應用程式（使用大部分 MFC 程式庫的最小應用程式小於10K）。

- 共用版本的 MFC 支援 MFC 延伸 Dll 和一般 MFC Dll。

- 建立使用共用 MFC 程式庫的應用程式，比建立靜態連結的 MFC 應用程式更快速，因為不需要連結 MFC 本身。 這在連結器必須壓縮 debug 資訊的**調試**程式中特別有用，因為連結的 DLL 已包含了偵錯工具資訊，所以在您的應用程式中會有較少的 DEBUG 資訊可精簡。

為何您不應該使用 MFC 的共用版本：

- 運送使用共用程式庫的應用程式時，您必須隨程式寄送 MFCxx.DLL （及其他）程式庫。 MFCxx.DLL 可以自由轉散發，就像許多 Dll 一樣，但您仍然必須在安裝程式中安裝 DLL。 此外，您還必須寄送 MSVCRTxx.DLL，其中包含您的程式和 MFC Dll 本身所使用的 C 執行時間程式庫。

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>如何撰寫 MFC 延伸模組 DLL

MFC 擴充 DLL 是包含類別和函式的 DLL，而這些函式是撰寫來美化 MFC 類別的功能。 MFC 擴充 DLL 會以應用程式使用共用的 MFC Dll 的相同方式來使用它，但有一些額外的考慮：

- 建立程式類似于建立一個使用共用 MFC 程式庫的應用程式，以及一些額外的編譯器和連結器選項。

- MFC 擴充 DLL 沒有 `CWinApp` 衍生的類別。

- MFC 擴充 DLL 必須提供特殊的 `DllMain` 。 `DllMain`程式會提供您可以修改的函式。

- `CDynLinkLibrary`如果 mfc 延伸模組 dll 希望將 `CRuntimeClass` es 或資源匯出至應用程式，MFC 延伸 dll 通常會提供初始化常式來建立。 `CDynLinkLibrary`如果每個應用程式的資料必須由 MFC 延伸模組 DLL 維護，則可以使用的衍生類別。

以下將更詳細地說明這些考慮。 您也應該參閱 MFC Advanced 概念範例[DLLHUSK](../overview/visual-cpp-samples.md) ，因為它會說明：

- 使用共用程式庫建立應用程式。 （DLLHUSK.EXE 是 MFC 應用程式，可動態連結至 MFC 程式庫以及其他 Dll）。

- 建立 MFC 擴充 DLL。 （請注意 `_AFXEXT` 用來建立 MFC 延伸 DLL 的特殊旗標，例如）

- MFC 擴充 Dll 的兩個範例。 其中一個顯示具有有限匯出（TESTDLL1）之 MFC 延伸 DLL 的基本結構，另一個則顯示匯出整個類別介面（TESTDLL2）。

用戶端應用程式和任何 MFC 延伸模組 Dll 都必須使用相同版本的 MFCxx.DLL。 您應遵循 MFC DLL 的慣例，並提供 MFC 延伸模組 DLL 的 debug 和 retail （/release）版本。 這可讓用戶端程式建立其應用程式的 debug 和 retail 版本，並將它們與所有 Dll 的適當 debug 或 retail 版本連結。

> [!NOTE]
> 因為 c + + 名稱重整和匯出問題，所以不同平臺的相同 DLL 和 Dll 的 debug 和 retail 版本之間可能會有不同的匯出清單。 零售 MFCxx.DLL 大約有2000個匯出的進入點;debug MFCxxD.DLL 大約有3000個匯出的進入點。

### <a name="quick-note-on-memory-management"></a>記憶體管理的快速注意事項

本技術提示結尾附近的「記憶體管理」一節說明如何使用 MFC 的共用版本來執行 MFCxx.DLL。 此處說明只執行 MFC 延伸模組 DLL 所需知道的資訊。

MFCxx.DLL 和載入至用戶端應用程式的位址空間的所有 MFC 延伸 Dll，都會使用相同的記憶體配置器、資源載入和其他 MFC 「全域」狀態，如同它們是在相同的應用程式中一樣。 這很重要，因為靜態連結至 MFC 的非 MFC DLL 程式庫和一般 MFC Dll 會執行完全相反的動作，並將每個 DLL 配置給它自己的記憶體集區。

如果 MFC 延伸模組 DLL 配置記憶體，則該記憶體可以自由地與任何其他應用程式佈建的物件混合。 此外，如果使用共用 MFC 程式庫的應用程式損毀，作業系統的保護將會維持共用 DLL 之任何其他 MFC 應用程式的完整性。

同樣地，其他「全域」 MFC 狀態（例如從載入資源的目前可執行檔）也會在用戶端應用程式和所有 MFC 延伸 Dll 以及 MFCxx.DLL 本身之間共用。

### <a name="building-an-mfc-extension-dll"></a>建立 MFC 延伸模組 DLL

您可以使用執行程式來建立 MFC 延伸 DLL 專案，而且它會自動產生適當的編譯器和連結器設定。 它也會產生可供您修改的函式 `DllMain` 。

如果您要將現有的專案轉換成 MFC 延伸模組 DLL，請從使用 MFC 共用版本建立應用程式的標準規則開始，然後執行下列動作：

- 將 **/D_AFXEXT**新增至編譯器旗標。 在 [專案屬性] 對話方塊中，選取 [C/c + +] 節點。 然後選取 [預處理器] 分類。 將新增 `_AFXEXT` 至 [定義宏] 欄位，並以分號分隔每個專案。

- 移除 **/gy**編譯器參數。 在 [專案屬性] 對話方塊中，選取 [C/c + +] 節點。 然後選取 [程式碼產生] 類別。 確定未啟用 [啟用函式層級連結] 選項。 這可讓您更輕鬆地匯出類別，因為連結器不會移除未參考的函式。 如果原始專案是用來建立靜態連結至 MFC 的標準 MFC DLL，請將 **/mt [d]** 編譯器選項變更為 **/md [d]**。

- 使用 [ **/DLL** ] 選項來建立匯出程式庫。 這會在您建立新的目標時設定，並將 Win32 動態連結程式庫指定為目標型別。

### <a name="changing-your-header-files"></a>變更您的標頭檔

MFC 擴充 DLL 的目標通常是要將一些通用功能匯出到一個或多個可以使用該功能的應用程式。 這會讓您的用戶端應用程式能夠匯出類別和全域功能。

若要這麼做，您必須確定每個成員函式都會適當地標示為匯入或匯出。 這需要特殊宣告： `__declspec(dllexport)` 和 `__declspec(dllimport)` 。 當用戶端應用程式使用您的類別時，您會想要將它們宣告為 `__declspec(dllimport)` 。 建立 MFC 擴充 DLL 本身時，應該將它們宣告為 `__declspec(dllexport)` 。 此外，必須實際匯出函式，讓用戶端程式在載入時系結至這些函式。

若要匯出整個類別，請 `AFX_EXT_CLASS` 在類別定義中使用。 當定義了和時，架構會定義此宏 `__declspec(dllexport)` `_AFXDLL` `_AFXEXT` ，但定義為 `__declspec(dllimport)` `_AFXEXT` 未定義時。 `_AFXEXT`如上所述，只有在建立 MFC 延伸模組 DLL 時才會定義。 例如：

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>不匯出整個類別

有時候，您可能只想要匯出類別的個別必要成員。 例如，如果您要匯出衍生的 `CDialog` 類別，您可能只需要匯出該函數和 `DoModal` 呼叫。 您可以使用 DLL 的來匯出這些成員。DEF 檔案，但您也可以在 `AFX_EXT_CLASS` 需要匯出的個別成員上使用相同的方式。

例如：

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

當您這麼做時，可能會遇到額外的問題，因為您不再匯出類別的所有成員。 問題在於 MFC 宏的工作方式。 MFC 的幾個 helper 宏實際上會宣告或定義資料成員。 因此，這些資料成員也需要從您的 DLL 匯出。

例如，建立 MFC 延伸 DLL 時，DECLARE_DYNAMIC 宏的定義如下：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

開頭為「靜態」的程式程式碼， `AFX_DATA` 是在您的類別內宣告靜態物件。 若要正確匯出此類別，並從用戶端存取執行時間資訊。EXE，您需要匯出這個靜態物件。 因為靜態物件是使用修飾詞所宣告 `AFX_DATA` ，所以您只需要在 `AFX_DATA` `__declspec(dllexport)` 建立 DLL 時定義為，並在 `__declspec(dllimport)` 建立用戶端可執行檔時將它定義為。

如上所述， `AFX_EXT_CLASS` 已以這種方式定義。 您只需要重新定義，就 `AFX_DATA` 可以與 `AFX_EXT_CLASS` 您的類別定義大致相同。

例如：

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

MFC 一律 `AFX_DATA` 會在其宏內定義的資料項目上使用符號，因此這項技術適用于所有這類情況。 例如，它將適用于 DECLARE_MESSAGE_MAP。

> [!NOTE]
> 如果您要匯出整個類別，而不是類別的選取成員，則會自動匯出靜態資料成員。

您可以使用相同的技巧，自動匯出 `CArchive` 使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏之類別的抽取運算子。 藉由括弧類別宣告（位於，來匯出封存運算子）。H 檔案），包含下列程式碼：

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>_AFXEXT 的限制

只要您沒有 MFC 擴充 Dll 的多個層級，您就可以針對 MFC 延伸模組 Dll 使用 _**afxext.h**前置處理器符號。 如果您的 MFC 延伸 Dll 會呼叫或衍生自您自己的 MFC 擴充 Dll 中的類別，然後再衍生自 MFC 類別，則您必須使用自己的預處理器符號來避免不明確。

問題在於，在 Win32 中，您必須明確宣告任何資料，就像 `__declspec(dllexport)` 是要從 dll 匯出一樣， `__declspec(dllimport)` 如果是從 dll 匯入則為。 當您定義時 `_AFXEXT` ，MFC 標頭會確保 `AFX_EXT_CLASS` 已正確定義。

當您有多個層級時，一個符號（例如） `AFX_EXT_CLASS` 並不夠，因為 MFC 延伸 dll 可能會匯出新的類別，以及從另一個 MFC 延伸 dll 匯入其他類別。 為了解決這個問題，請使用特殊的預處理器符號，表示您要建立 DLL 本身，而不是使用 DLL。 例如，假設有兩個 MFC 延伸 Dll、A.DLL 和 B.DLL。 它們會分別匯出. H 和 b. H 中的一些類別。 B.DLL 使用 A.DLL 的類別。 標頭檔看起來會像這樣：

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

建立 A.DLL 時，它是以 **/DA_IMPL**建立，而且在建立 B.DLL 時，它是以 **/DB_IMPL**建立的。 藉由使用每個 DLL 的個別符號，會匯出 CExampleB，並在建立 B.DLL 時匯入 CExampleA。 建立 A.DLL 並在 B.DLL （或其他用戶端）使用時匯入時，會匯出 CExampleA。

使用內建 `AFX_EXT_CLASS` 和預處理器符號時，無法完成這種類型的分層 `_AFXEXT` 。 上述技術可解決這個問題，方法與建立 OLE、Database 和 Network MFC 延伸 Dll 時，MFC 本身所使用的機制不同。

### <a name="not-exporting-the-entire-class"></a>不匯出整個類別

同樣地，當您不想要匯出整個類別時，就必須特別小心。 您必須確定已正確匯出 MFC 宏所建立的必要資料項目。 這可以藉由重新定義 `AFX_DATA` 至您的特定類別 ' 宏來完成。 當您不想要匯出整個類別時，應該執行此動作。

例如：

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

以下是您應該在 MFC 延伸模組 DLL 的主要原始程式檔中放置的確切程式碼。 它應該會在標準包含之後。 請注意，當您使用執行程式來建立 MFC 延伸 DLL 的起始檔案時，它會 `DllMain` 為您提供。

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

的呼叫 `AfxInitExtensionModule` 會捕獲模組執行時間類別（ `CRuntimeClass` 結構）以及其物件 factory （ `COleObjectFactory` 物件），以便稍後在建立物件時使用 `CDynLinkLibrary` 。 （選擇性）呼叫，可 `AfxTermExtensionModule` 讓 mfc 在每個進程卸離時（當進程結束時，或從 MFC 延伸模組 dll 卸載 DLL 時），清除 mfc 擴充 dll `FreeLibrary` 。 由於大部分的 MFC 擴充 Dll 都不會動態載入（通常是透過其匯入程式庫來連結），因此 `AfxTermExtensionModule` 通常不需要呼叫。

如果您的應用程式會以動態方式載入和釋放 MFC 延伸 Dll，請務必呼叫 `AfxTermExtensionModule` ，如上所示。 `AfxLoadLibrary` `AfxFreeLibrary` `LoadLibrary` `FreeLibrary` 如果您的應用程式使用多個執行緒，或如果它以動態方式載入 MFC 延伸 DLL，也請務必使用和（而不是 Win32 函數和）。 使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 可確保在載入和卸載 MFC 延伸模組 DLL 時執行的啟動和關閉程式碼不會損毀全域 MFC 狀態。

標頭檔 AFXDLLX。H 包含 MFC 延伸 Dll 中使用之結構的特殊定義，例如和的定義 `AFX_EXTENSION_MODULE` `CDynLinkLibrary` 。

全域*extensionDLL*必須依照所示的方式宣告。 不同于 MFC 的16位版本，您可以在這段期間配置記憶體並呼叫 MFC 函式，因為 MFCxx.DLL 會在呼叫時完全初始化 `DllMain` 。

### <a name="sharing-resources-and-classes"></a>共用資源和類別

簡單的 MFC 延伸 Dll 只需要將幾個低頻寬的函式匯出至用戶端應用程式即可。 更多使用者介面密集 Dll 可能會想要將資源和 c + + 類別匯出至用戶端應用程式。

匯出資源是透過資源清單來完成。 在每個應用程式中，都是單向連結的 `CDynLinkLibrary` 物件清單。 尋找資源時，大部分載入資源的標準 MFC 執行會先在目前的資源模組（）上進行檢查，如果找不到，則會在 `AfxGetResourceHandle` `CDynLinkLibrary` 嘗試載入所要求資源的物件清單中進行。

以動態建立 c + + 物件，指定的 c + + 類別名稱類似。 MFC 物件還原序列化機制必須已註冊所有的 `CRuntimeClass` 物件，讓它可以根據稍早儲存的內容，以動態方式建立所需類型的 c + + 物件，以便重建。

如果您想要讓用戶端應用程式使用 MFC 擴充功能 DLL 中的類別 `DECLARE_SERIAL` ，則您必須將您的類別匯出為用戶端應用程式可見的。 這也可以透過瀏覽清單來完成 `CDynLinkLibrary` 。

在 MFC Advanced 概念範例[DLLHUSK](../overview/visual-cpp-samples.md)的案例中，清單看起來會像這樣：

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

MFCxx.DLL 通常是在資源和類別清單上的最後一個。 MFCxx.DLL 包含所有標準的 MFC 資源，包括所有標準命令識別碼的提示字串。 將它放在清單的結尾，可以讓 Dll 和用戶端應用程式本身不具有自己的標準 MFC 資源複本，而是改為依賴 MFCxx.DLL 中的共用資源。

將所有 Dll 的資源和類別名稱合併到用戶端應用程式的命名空間，有個缺點，就是您必須小心選擇哪些識別碼或名稱。 當然，您也可以停用這項功能，方法是不要將您的資源或 `CDynLinkLibrary` 物件匯出至用戶端應用程式。 [DLLHUSK](../overview/visual-cpp-samples.md)範例會使用多個標頭檔來管理共用資源命名空間。 如需使用共用資源檔的更多秘訣，請參閱[技術提示 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) 。

### <a name="initializing-the-dll"></a>初始化 DLL

如前所述，您通常會想要建立物件，以便將 `CDynLinkLibrary` 您的資源和類別匯出至用戶端應用程式。 您將需要提供已匯出的進入點來初始化 DLL。 這至少是一個不接受任何引數的 void 常式，而且不會傳回任何專案，但它可以是您喜歡的任何專案。

如果您使用此方法，每個想要使用您的 DLL 的用戶端應用程式都必須呼叫此初始化常式。 您也可以 `CDynLinkLibrary` 在呼叫之後，在中配置此物件 `DllMain` `AfxInitExtensionModule` 。

初始化常式必須 `CDynLinkLibrary` 在目前應用程式的堆積中建立物件，並將其連接到您的 MFC 延伸 DLL 資訊。 這可以透過下列方式來完成：

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

此範例中的常式名稱（ *InitXxxDLL* ）可以是您想要的任何專案。 它不需要是**extern "C"**，但這樣做會讓匯出清單更容易維護。

> [!NOTE]
> 如果您使用來自一般 MFC DLL 的 MFC 延伸模組 DLL，您必須匯出這個初始化函數。 您必須先從一般 MFC DLL 呼叫此函式，才能使用任何 MFC 延伸 DLL 類別或資源。

### <a name="exporting-entries"></a>匯出專案

匯出類別的簡單方式，是 `__declspec(dllimport)` `__declspec(dllexport)` 在您想要匯出的每個類別和全域函式上使用和。 這讓它變得更簡單，但比命名每個進入點更有效率（如下所述），因為您對匯出哪些函式不會有太大的控制權，而且您無法依序數匯出函數。 TESTDLL1 和 TESTDLL2 會使用這個方法來匯出其專案。

更有效率的方法（以及 MFCxx.DLL 所使用的方法）是藉由命名中的每個專案，以手動方式匯出每個專案。DEF 檔案。 因為我們是從 DLL 匯出選擇性匯出（也就是並非所有專案），所以我們必須決定要匯出哪些特定介面。 這很麻煩，因為您必須以中的專案形式，將損壞的名稱指定至連結器。DEF 檔案。 除非您真的需要有其符號連結，否則請勿匯出任何 c + + 類別。

如果您已嘗試使用匯出 c + + 類別。DEF 檔案之前，您可能會想要開發工具來自動產生這份清單。 這可以使用兩階段連結程式來完成。 連結您的 DLL 一次而不匯出，並允許連結器產生。對應檔。 該.對應檔可以用來產生應該匯出的函式清單，因此在進行一些重新排列時，可以使用它來產生的匯出專案。DEF 檔案。 MFCxx.DLL 和 OLE 和 Database MFC 延伸模組 Dll 的匯出清單（數個數字）是使用這類程式產生的（雖然它不是完全自動的，而且在一段時間內每次都需要進行一些微調）。

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp 與 CDynLinkLibrary 的比較

MFC 擴充 DLL 不具有 `CWinApp` 本身的衍生物件，而是必須使用 `CWinApp` 用戶端應用程式的衍生物件。 這表示用戶端應用程式擁有主要訊息抽取、閒置迴圈等等。

如果您的 MFC 延伸模組 DLL 必須為每個應用程式維護額外的資料，您可以從衍生新的類別， `CDynLinkLibrary` 並在上述的 InitXxxDLL 常式中加以建立。 執行時，DLL 可以檢查目前應用程式的物件清單， `CDynLinkLibrary` 以找出該特定 MFC 延伸模組 DLL 的物件。

### <a name="using-resources-in-your-dll-implementation"></a>在您的 DLL 執行中使用資源

如先前所述，預設資源負載將會引導物件清單， `CDynLinkLibrary` 以尋找具有所要求資源的第一個 EXE 或 DLL。 所有的 MFC Api 以及所有內部程式碼都會使用 `AfxFindResourceHandle` 來逐步解說資源清單，以尋找任何資源，而不論其所在位置為何。

如果您只想要從特定位置載入資源，請使用 Api `AfxGetResourceHandle` 和 `AfxSetResourceHandle` 來儲存舊的控制碼，並設定新的控制碼。 回到用戶端應用程式之前，請務必還原舊的資源控制碼。 範例 TESTDLL2 會使用這種方法來明確載入功能表。

瀏覽清單的缺點是稍微慢一點，而且需要管理資源識別碼範圍。 其優點是連結至數個 MFC 擴充 Dll 的用戶端應用程式可以使用任何 DLL 提供的資源，而不需要指定 DLL 實例控制碼。 `AfxFindResourceHandle`是用來流覽資源清單以尋找指定相符的 API。 它會採用資源的名稱和類型，並傳回第一次找到它的資源控制碼（或 Null）。

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>撰寫使用 DLL 版本的應用程式

### <a name="application-requirements"></a>應用程式需求

使用 MFC 共用版本的應用程式必須遵循幾個簡單的規則：

- 它必須具有 `CWinApp` 物件，並遵循訊息提取的標準規則。

- 它必須以一組必要的編譯器旗標進行編譯（請參閱下文）。

- 它必須與 MFCxx 匯入程式庫連結。 藉由設定所需的編譯器旗標，MFC 標題會決定應用程式應連結的程式庫連結時間。

- 若要執行可執行檔，MFCxx.DLL 必須位於路徑或 Windows 系統目錄中。

### <a name="building-with-the-development-environment"></a>在開發環境中建立

如果您使用具有大部分標準預設值的內部 makefile，您可以輕鬆地變更專案以建立 DLL 版本。

下列步驟假設您已正確運作的 MFC 應用程式與 NAFXCWD.LIB 連結。LIB （用於 debug）和 NAFXCW。LIB （適用于零售），而且您想要將它轉換成使用共用版本的 MFC 程式庫。 您正在執行 Visual C++ 環境，並具有內部專案檔案。

1. 在 [**專案**] 功能表上，按一下 [**屬性**]。 在 [**一般**] 頁面的 [**專案預設值**] 底下，將 [Microsoft Foundation 類別] 設定為在**共用 DLL 中使用 MFC** （MFCxx （d） .dll）。

### <a name="building-with-nmake"></a>使用 NMAKE 建立

如果您使用 Visual C++ 的外部 makefile 功能，或直接使用 NMAKE，您就必須編輯 makefile 以支援編譯器和連結器選項

必要的編譯器旗標：

- **/D_AFXDLL/MD** 
   **/D_AFXDLL**

標準 MFC 標頭需要定義此符號：

- **/Md**應用程式必須使用 C 執行時間程式庫的 DLL 版本

所有其他編譯器旗標會遵循 MFC 預設值（例如，_DEBUG 來進行 DEBUG）。

編輯程式庫的連結器清單。 變更 NAFXCWD.LIB。LIB 至 MFCxxD，並變更 NAFXCW。LIB 至 MFCxx。 取代 LIBC。具有 MSVCRT.LIB 的 LIB。LIB. 如同任何其他 MFC 程式庫，MFCxxD 必須放在任何 C 執行時間程式庫**之前**。

選擇性地將 **/D_AFXDLL**新增至您的零售和 debug 資源編譯器選項（實際以 **/r**編譯資源的選項）。 這會藉由共用 MFC Dll 中的資源，讓您的最終可執行檔變得更小。

進行這些變更之後，需要完整重建。

### <a name="building-the-samples"></a>建立範例

大部分的 MFC 範例程式都可以從命令列 Visual C++ 或從共用的 NMAKE 相容 MAKEFILE 建立。

若要將這些範例中的任何一個轉換成使用 MFCxx.DLL，您可以載入。MAK 檔案進入 Visual C++，並如上面所述設定專案選項。 如果您使用 NMAKE 組建，您可以在 NMAKE 命令列上指定 "AFXDLL = 1"，這會使用共用的 MFC 程式庫來建立範例。

MFC Advanced 概念範例[DLLHUSK](../overview/visual-cpp-samples.md)是以 MFC 的 DLL 版本來建立。 這個範例不只會說明如何建立與 MFCxx.DLL 連結的應用程式，也會說明 MFC DLL 封裝選項的其他功能，例如本技術提示稍後所述的 MFC 擴充 Dll。

### <a name="packaging-notes"></a>封裝附注

Dll 的零售版（MFCxx [U]。DLL）可自由轉散發。 Dll 的偵錯工具版本無法自由轉散發，而且只能在開發應用程式期間使用。

調試的 Dll 會提供調試資訊。 藉由使用 Visual C++ 偵錯工具，您可以追蹤應用程式的執行以及 DLL。 發行 Dll （MFCxx [U]。DLL）不包含調試資訊。

如果您自訂或重建 Dll，則應該將它們稱為「MFCxx」 MFC SRC file MFCDLL 以外的專案。MAK 描述組建選項，並包含重新命名 DLL 的邏輯。 需要重新命名檔案，因為許多 MFC 應用程式可能會共用這些 Dll。 讓自訂版本的 MFC Dll 取代系統上所安裝的，可能會使用共用的 MFC Dll 來中斷另一個 MFC 應用程式。

不建議您重建 MFC Dll。

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>如何執行 MFCxx.DLL

下一節將說明如何實作為 MFC DLL （MFCxx.DLL 和 MFCxxD.DLL）。 如果您只想要在應用程式中使用 MFC DLL，則瞭解這裡的詳細資料也不重要。 這裡的詳細資料並不是瞭解如何撰寫 MFC 延伸 DLL，但是瞭解這種實現可能可以協助您撰寫自己的 DLL。

### <a name="implementation-overview"></a>執行總覽

MFC DLL 其實是 MFC 延伸 DLL 的特殊案例，如上所述。 對於大量的類別，它有很多的匯出。 在 MFC DLL 中還有幾項額外的功能，讓它比一般 MFC 延伸 DLL 更特殊。

### <a name="win32-does-most-of-the-work"></a>Win32 會執行大部分的工作

MFC 的16位版本需要一些特殊技術，包括堆疊區段上的每個應用程式資料、某些80x86 的元件程式碼所建立的特殊區段、個別處理的例外狀況內容，以及其他技術。 Win32 會直接支援 DLL 中的每個進程資料，這是您在大部分的時間所要的。 在大部分的情況中，MFCxx.DLL 只是 NAFXCW。包裝在 DLL 中的 LIB。 如果您查看 MFC 原始程式碼，就會發現非常少的 #ifdef _AFXDLL，因為需要進行的特殊案例很少。 特殊案例特別是處理 Windows 3.1 上的 Win32 （也稱為 Win32）。 Win32 不支援直接處理個別進程的 DLL 資料，因此 MFC DLL 必須使用執行緒區域儲存區（TLS） Win32 Api 來取得處理常式本機資料。

### <a name="impact-on-library-sources-additional-files"></a>對程式庫來源、其他檔案的影響

**_AFXDLL**版本對一般 MFC 類別庫來源和標頭的影響相對較小。 有一個特殊的版本檔案（AFXV_DLL。H）以及額外的標頭檔（AFXDLL_。H）包含在主要 AFXWIN.H 中。H 標頭。 AFXDLL_。H 標頭包含 `CDynLinkLibrary` `_AFXDLL` 應用程式和 MFC 延伸模組 dll 的類別和其他執行詳細資料。 AFXDLLX。H 標頭是用來建立 MFC 延伸 Dll （如需詳細資訊，請參閱上述內容）。

MFC SRC 中 MFC 程式庫的一般來源在 #ifdef 下有一些額外的條件式程式碼 `_AFXDLL` 。 其他原始程式檔（DLLINIT。CPP）包含額外的 DLL 初始化程式碼，以及 MFC 共用版本的其他粘附。

為了建立 MFC 的共用版本，會提供額外的檔案。 （如需如何建立 DLL 的詳細資訊，請參閱下文）。

- 兩個.DEF 檔案是用來匯出 DLL 的 debug （MFCxxD）和 release （MFCxx）版本的 MFC DLL 進入點。

- ，.RC 檔案（MFCDLL。RC）包含所有標準 MFC 資源和 DLL 的 VERSIONINFO 資源。

- 為.CLW 檔（MFCDLL。CLW）是為了允許使用 ClassWizard 流覽 MFC 類別而提供的。 注意：這項功能並非 MFC 的 DLL 版本特有的。

### <a name="memory-management"></a>記憶體管理

使用 MFCxx.DLL 的應用程式會使用共用的 C 執行時間 DLL MSVCRTxx.DLL 所提供的通用記憶體配置器。 應用程式、任何 MFC 延伸 Dll，以及 MFC Dll 本身會使用此共用記憶體配置器。 藉由使用共用 DLL 進行記憶體配置，MFC Dll 可以配置應用程式稍後釋放的記憶體，反之亦然。 因為應用程式和 DLL 都必須使用相同的配置器，所以您不應該覆寫 c + + 全域**operator new**或**運算子 delete**。 相同的規則適用于其餘的 C 執行時間記憶體配置常式（例如**malloc**、 **realloc**、 **free**和其他）。

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>序數和類別 __declspec （dllexport）和 DLL 命名

我們不會使用 `class` **`__declspec(dllexport)`** c + + 編譯器的功能。 相反地，匯出清單會包含在類別庫來源中（MFCxx .DEF 和 MFCxxD）。 只會匯出這組選取的進入點（函數和資料）。 不會匯出其他符號（例如 MFC 私用執行函式或類別），所有匯出都是由不含字串名稱的序數在常駐或非常駐名稱資料表中執行。

使用 `class` **`__declspec(dllexport)`** 可能是建立較小 dll 的可行替代方案，但在大型 dll （例如 MFC）的情況下，預設的匯出機制具有效率和容量限制。

這就是我們可以在發行 MFCxx.DLL 封裝大量的功能，而這只是 800 KB，而不會危及執行或載入速度的太多。 MFCxx.DLL 已超過10倍，則不會使用這項技術。 這也可以在結尾新增額外的進入點。DEF 檔案，允許簡單的版本控制，而不會危害依序數匯出的速度和大小效率。 MFC 類別庫中的主要版本修訂將會變更程式庫名稱。 也就是說，MFC30.DLL 是包含 MFC 類別庫3.0 版的可轉散發 DLL。 此 DLL 的升級（例如，在假設的 MFC 3.1 中），DLL 的名稱會改 MFC31.DLL。 同樣地，如果您修改 MFC 原始程式碼來產生自訂版本的 MFC DLL，請使用不同的名稱（最好是在名稱中沒有 "MFC"）。

## <a name="see-also"></a>另請參閱

[依數位的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依類別區分的技術提示](../mfc/technical-notes-by-category.md)
