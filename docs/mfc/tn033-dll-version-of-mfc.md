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
ms.openlocfilehash: ad4cb883cfe7e397cf599d659afb02b23501dc5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370318"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033：MFC 的 DLL 版本

本說明介紹如何使用 MFCxx.DLL 和 MFCxxD.DLL(其中 x 是 MFC 版本號)與 MFC 應用程式和 MFC 擴展 DLL 共用動態連結庫。 有關常規 MFC DLL 的詳細資訊,請參閱[使用 MFC 作為 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

本技術說明涵蓋 DLL 的三個方面。 後兩個適用於更進階的使用者:

- [如何建構 MFC 延伸 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [如何使用 MFC 的 DLL 版本的 MFC 應用程式](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [如何實現 MFC 分享動態連結庫](#_mfcnotes_how_the_mfc30.dll_is_implemented)

如果您有興趣使用可用於非 MFC 應用程式的 MFC 建構 DLL(這稱為常規 MFC DLL),請參閱[技術說明 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>MFCxx.DLL 支援的概述:術語和檔

**一般 MFC DLL**:使用常規 MFC DLL 使用某些 MFC 類構建獨立 DLL。 跨 App/DLL 邊界的介面是"C"介面,用戶端應用程式不必是 MFC 應用程式。

這是 MFC 1.0 中支援的 DLL 支援版本。 它描述了[技術說明11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)和MFC高級概念示例[DLLScreenCap。](../overview/visual-cpp-samples.md)

> [!NOTE]
> 從 Visual C++ 版本 4.0 起,**術語 USRDLL**已過時,並已由靜態連結到 MFC 的常規 MFC DLL 替換。 您還可以構建一個定期 MFC DLL,動態連結到 MFC。

MFC 3.0(及以上)支援常規 MFC DLL,具有所有新功能,包括 OLE 和資料庫類。

**AFXDLL**:這也稱為 MFC 庫的共用版本。 這是 MFC 2.0 中添加的新 DLL 支援。 MFC 庫本身位於多個 DLL 中(如下所述),用戶端應用程式或 DLL 動態連結所需的 DLL。 跨應用程式/DLL 邊界的介面是C++/MFC 類介面。 用戶端應用程式必須是 MFC 應用程式。 這支援所有 MFC 3.0 功能(例外情況:資料庫類不支援 UNICODE)。

> [!NOTE]
> 從 Visual C++ 版本 4.0 起,這種類型的 DLL 稱為"擴展 DLL"。

此說明將使用 MFCxx.DLL 來參考整個 MFC DLL 集,其中包括:

- 調試:MFCxxD.DLL(組合)和MFCSxxD.LIB(靜態)。

- 發佈:MFCxx.DLL(組合)和MFCSxx.LIB(靜態)。

- Unicode 調試:MFCxxUD.DLL(組合)和 MFCSxxD.LIB(靜態)。

- Unicode 版本:MFCxxU.DLL(組合)和 MFCSxxU.LIB(靜態)。

> [!NOTE]
> MFCSxx[U]D]。LIB 庫與 MFC 共用 DLL 結合使用。 這些庫包含必須靜態連結到應用程式或 DLL 的代碼。

指向相應匯入函式庫的應用程式連結:

- 除錯: MFCxxD.LIB

- 發布: MFCxx.LIB

- Unicode 除錯:MFCxxUD.LIB

- Unicode 版本:MFCxxU.LIB

"MFC 擴展 DLL"是基於 MFCxx.DLL(和/或其他 MFC 共用 DLL)構建的 DLL。 在這裡,MFC 元件體系結構開始生效。 如果從 MFC 類派生有用類,或者構建另一個類似 MFC 的工具組,則可以將其放置在 DLL 中。 DLL 使用 MFCxx.DLL,最終用戶端應用程式也是如此。 這允許可重用的葉類、可重用的基類和可重用的視圖/文檔類。

## <a name="pros-and-cons"></a>優點和缺點

為什麼要使用 MFC 的分享版本

- 使用共用庫可能會導致應用程式更小(使用大多數 MFC 庫的最小應用程式小於 10K)。

- MFC 的共用版本支援 MFC 擴展 DLL 和常規 MFC DLL。

- 構建使用共用 MFC 庫的應用程式比建構靜態連結的 MFC 應用程式要快,因為沒有必要連結 MFC 本身。 在**DEBUG**生成中尤其如此,其中連結器必須壓縮除錯資訊─透過連結到已包含除錯資訊的 DLL,應用程式內要壓縮的調試資訊更少。

為什麼不使用 MFC 的分享版本:

- 傳送使用共用庫的應用程式需要您將 MFCxx.DLL(和其他)庫與程式一起傳送。 MFCxx.DLL 與許多 DLL 一樣可自由再分發,但您仍必須在設置程式中安裝 DLL。 此外,您必須提供 MSVCRTxx.DLL,其中包含由您的程式和 MFC DLL 本身使用的 C 執行時庫。

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>如何寫 MFC 延伸 DLL

MFC 擴展 DLL 是一種 DLL,其中包含為修飾 MFC 類的功能而編寫的類和函數。 MFC 延伸 DLL 使用分享 MFC DLL 的方式與應用程式使用它的方式相同,還有其他一些注意事項:

- 生成過程類似於建構一個應用程式,該應用程式使用具有一些附加編譯器和連結器選項的共用 MFC 庫。

- MFC 擴展 DLL`CWinApp`沒有派生 類。

- MFC 延伸 DLL`DllMain`必須提供 特殊的 。 AppWizard 提供了`DllMain`一個可以修改的函數。

- `CDynLinkLibrary` MFC 延伸 DLL 通常會提供初始化例,以建立 MFC 延伸`CRuntimeClass`DLL 希望將 es 或資源匯出到應用程式時建立 。 如果每個應用程式的數據`CDynLinkLibrary`必須由 MFC 擴展 DLL 維護,則可以使用 派生類。

下面將更詳細地介紹這些注意事項。 您還應參考 MFC 高級概念範例[DLLHUSK,](../overview/visual-cpp-samples.md)因為它說明了:

- 使用共用庫構建應用程式。 (德胡斯克。EXE 是一個 MFC 應用程式,可動態連結到 MFC 庫以及其他 DLL。

- 構建 MFC 擴展 DLL。 ( 請注意用於建構`_AFXEXT`MFC 延伸 DLL 的特殊標誌)

- MFC 擴展 DLL 的兩個範例。 一個顯示匯出受限的 MFC 擴展 DLL 的基本結構 (TESTDLL1),另一個顯示匯出整個類介面 (TESTDLL2)。

用戶端應用程式和任何 MFC 擴展 DLL 都必須使用相同的 MFCxx.DLL 版本。 您應該遵循 MFC DLL 的約定,並提供 MFC 擴展 DLL 的調試和零售(/發佈)版本。 這允許用戶端程式構建其應用程式的調試和零售版本,並將它們與所有 DLL 的相應調試或零售版本連結。

> [!NOTE]
> 由於C++名稱管理和匯出問題,因此來自MFC擴展DLL的匯出清單可能因不同平臺的相同DLL和DLL的調試和零售版本而異。 零售 MFCxx.DLL 擁有約 2000 個出口入口點;調試 MFCxxD.DLL 擁有約 3000 個導出的入口點。

### <a name="quick-note-on-memory-management"></a>關於記憶體管理的快速說明

本技術說明末尾的標題為「記憶體管理」的部分介紹了 MFCxx.DLL 與 MFC 共用版本的實現。 此處介紹了實現 MFC 擴展 DLL 所需的資訊。

MFCxx.DLL 和載入到用戶端應用程式位址空間中的所有 MFC 擴展 DLL 將使用相同的記憶體配置器、資源載入和其他 MFC"全域"狀態,就像它們在同一應用程式中一樣。 這一點非常重要,因為靜態連結到 MFC 的非 MFC DLL 庫和常規 MFC DLL 完全相反,並且每個 DLL 都從自己的記憶體池中分配出來。

如果 MFC 擴展 DLL 分配記憶體,則該記憶體可以自由地與任何其他應用程式分配的物件混合。 此外,如果使用共用 MFC 庫的應用程式崩潰,操作系統的保護將保持共用 DLL 的任何其他 MFC 應用程式的完整性。

同樣,其他"全域"MFC 狀態(如當前可執行檔以載入資源)也在用戶端應用程式和所有 MFC 擴展 DLL 以及 MFCxx.DLL 本身之間共用。

### <a name="building-an-mfc-extension-dll"></a>建構 MFC 延伸 DLL

您可以使用 AppWizard 創建 MFC 擴展 DLL 專案,它將自動生成相應的編譯器和連結器設定。 它還生成了一個`DllMain`函數,您可以修改。

如果要將現有項目轉換為 MFC 延伸 DLL,請從使用 MFC 的分享版本建構應用程式的標準規則開始,然後執行以下操作:

- 將 **/D_AFXEXT**添加到編譯器標誌。 在"專案屬性"對話框中,選擇 C/C++節點。 然後選擇預處理器類別。 添加到`_AFXEXT`「定義宏」欄位,將每個具有分號的項分隔開來。

- 刪除 **/Gy**編譯器開關。 在"專案屬性"對話框中,選擇 C/C++節點。 然後選擇"代碼生成" 確保未啟用"啟用功能級別連結"選項。 這將更容易匯出類,因為連結器不會刪除未引用的函數。 如果原始項目用於建構與 MFC 靜態連結的一般 MFC DLL,則將 **/MT_d_** 編譯器選項更改為 **/MD_d}**。

- 使用 **/DLL**選項建置匯出庫以連結。 這將在創建新目標時設置,指定 Win32 動態連結庫為目標類型。

### <a name="changing-your-header-files"></a>變更標題檔案

MFC 擴展 DLL 的目標通常是將一些通用功能匯出到一個或多個可以使用該功能的應用程式。 這歸結為匯出可用於用戶端應用程式的類和全域函數。

為此,必須確保每個成員函數都標記為適當的導入或匯出。 這需要特殊的聲明:`__declspec(dllexport)``__declspec(dllimport)`與 。 當客戶端應用程式使用類別時,您希望將它們聲明`__declspec(dllimport)`為 。 在建構 MFC 延伸 DLL 本身`__declspec(dllexport)`時,應聲明它們為 。 此外,必須實際匯出函數,以便用戶端程式在載入時綁定到它們。

要匯出整個類,請使用`AFX_EXT_CLASS`類定義。 此宏由框架`__declspec(dllexport)`定義為何`_AFXDLL`時`_AFXEXT`定義和 定義,`__declspec(dllimport)`但定義為`_AFXEXT`未定義時。 `_AFXEXT`如上所述,僅在構建 MFC 擴展 DLL 時定義。 例如：

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>未匯出整個類別

有時,您可能希望只匯出類的單個必要成員。 例如,如果要匯出`CDialog`派生類,可能只需要匯出構造函數`DoModal`和調用。 您可以使用 DLL 匯出這些成員。DEF 檔,但您也可以以大致`AFX_EXT_CLASS`相同 的方式對需要匯出的各個成員使用。

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

執行此操作時,可能會遇到其他問題,因為您不再匯出類的所有成員。 問題在於 MFC 宏的工作方式。 MFC 的幾個幫助宏實際上聲明或定義了數據成員。 因此,這些數據成員也需要從 DLL 匯出。

例如,DECLARE_DYNAMIC宏的定義如下:生成 MFC 擴展 DLL 時:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

開始「靜態`AFX_DATA`」的行是在類內聲明靜態物件。 要正確匯出此類並從用戶端訪問運行時資訊。EXE,您需要匯出此靜態物件。 由於靜態物件是使用修飾`AFX_DATA`符聲明的,因此在構建`AFX_DATA`DLL 時`__declspec(dllexport)`只需定義為 ,並將`__declspec(dllimport)`其定義為構建用戶端 可執行檔時。

如上所述,`AFX_EXT_CLASS`已經以這種方式定義。 您只需重新定義`AFX_DATA`,與類`AFX_EXT_CLASS`定義 相同。

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

MFC 始終`AFX_DATA`在其宏中定義的數據項上使用符號,因此此技術適用於所有此類方案。 例如,它將適用於DECLARE_MESSAGE_MAP。

> [!NOTE]
> 如果要匯出整個類而不是類的選定成員,則會自動匯出靜態數據成員。

可以使用相同的技術自動匯出使用DECLARE_SERIAL和IMPLEMENT_SERIAL宏`CArchive`的類的提取運算符。 通過包圍類聲明(位於 中)匯出存檔運算符。H 檔案與以下代碼:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>_AFXEXT限制

只要沒有多層 MFC 擴展 DLL,就可以為 MFC 擴展 DLL 使用 #**AFXEXT**預處理器符號。 如果 MFC 擴展 DLL 呼叫或派生自您自己的 MFC 擴展 DLL 中的類,然後從 MFC 類派生,則必須使用您自己的預處理器符號以避免歧義。

問題是,在 Win32 中,必須顯式聲明任何數據`__declspec(dllexport)`,就像從 DLL 匯出`__declspec(dllimport)`數據一樣, 以及如果要從 DLL 導入數據。 定義`_AFXEXT`時,MFC 標`AFX_EXT_CLASS`頭確保 正確定義。

當您有多個圖層時,一個符號(如`AFX_EXT_CLASS`是不夠的),因為 MFC 擴展 DLL 可能正在匯出新類,以及從其他 MFC 擴展 DLL 導入其他類。 為了解決此問題,請使用一個特殊的前處理器符號,指示您正在構建 DLL 本身,而不是使用 DLL。 例如,假設兩個 MFC 擴展 DLL A.DLL 和 B.DLL。 它們各自分別匯出 A.H 和 B.H 中的一些類。 B.DLL 使用 A.DLL 中的類。 標頭檔如下所示:

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

當 A.DLL 產生時,它使用 **/DA_IMPL**構建,當 B.DLL 生成時,它使用 **/DB_IMPL**生成。 通過為每個 DLL 使用單獨的符號,將匯出 CExampleB 並在建構 B.DLL 時導入 CExampleA。 CExampleA 在生成 A.DLL 時匯出,並在 B.DLL(或其他用戶端)使用時導入。

使用內置`AFX_EXT_CLASS``_AFXEXT`和 預處理器符號時,無法進行這種類型的分層。 上述技術以 MFC 本身在構建其 OLE、資料庫和網路 MFC 擴展 DLL 時使用的機制的方式解決了此問題。

### <a name="not-exporting-the-entire-class"></a>未匯出整個類別

同樣,當您不匯出整個類時,您必須特別注意。 您必須確保正確匯出 MFC 宏創建的必要數據項。 這可以通過重新`AFX_DATA`定義 到特定類的宏來實現。 這應在您不匯出整個類時執行。

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

以下是您應該在 MFC 副檔名 DLL 的主源檔中放置的確切代碼。 它應該在標準包含之後。 請注意,當您使用 AppWizard 為 MFC 延伸名 DLL 建立啟動檔時`DllMain`,它會為您提供 .

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

捕獲`AfxInitExtensionModule`模組執行時類別`CRuntimeClass`(結構)及其物件工廠`COleObjectFactory`(物件)的調用,供以後`CDynLinkLibrary`創建 物件時使用。 (可選)調用允許`AfxTermExtensionModule`MFC 在每個行程從 MFC 分機 DLL 分離時清理 MFC 分機 DLL(當行程退出時發生,或者由於`FreeLibrary`調用而卸載 DLL 時)。 由於大多數 MFC 擴展 DLL 不是動態載入的(通常,它們透過其匯入庫連結`AfxTermExtensionModule`),因此通常不需要呼叫 。

如果應用程式動態載入並釋放 MFC 擴展 DLL,請`AfxTermExtensionModule`確保呼叫 ,如上所示。 如果應用程式使用多個線程`AfxLoadLibrary``AfxFreeLibrary`或動態載入 MFC 擴展`LoadLibrary``FreeLibrary`DLL,請確保使用和 (而不是 Win32 函數和)。 使用`AfxLoadLibrary`並`AfxFreeLibrary`確保 在載入和卸載 MFC 擴展 DLL 時執行的啟動和關閉代碼不會損壞全域 MFC 狀態。

頭檔 AFXDLLX。H 包含 MFC 延伸 DLL 中使用的結構的`AFX_EXTENSION_MODULE``CDynLinkLibrary`特殊定義,例如和 的定義。

全域*擴展 DLL*必須聲明為如圖所示。 與 16 位元版本的 MFC 不同,您可以在這段時間內分配記憶體並調用 MFC 函數,因為 MFCxx.DLL 在調用時`DllMain`已完全初始化。

### <a name="sharing-resources-and-classes"></a>共用資源和類

簡單的 MFC 擴展 DLL 只需要將幾個低頻寬函數匯出到用戶端應用程式,而僅需向用戶端應用程式匯出。 更多使用者介面密集型 DLL 可能需要將資源和C++類匯出到用戶端應用程式。

匯出資源是通過資源清單完成的。 在每個應用程式中,都是`CDynLinkLibrary`一個單獨連結的物件清單。 尋找資源時,載入資源的大多數標準 MFC 實現首先查看目前資源模組 (),`AfxGetResourceHandle`如果未找到,則遍歷嘗試載入`CDynLinkLibrary`請求的資源 的物件清單。

給定C++類名稱C++對象的動態創建是相似的。 MFC 物件反序列化機制需要註冊`CRuntimeClass`所有 物件,以便可以通過根據之前存儲的內容動態創建所需類型的C++物件來重建。

如果希望客戶端應用程式在 MFC 擴展 DLL 中使用 類`DECLARE_SERIAL`,則需要匯出類才能對用戶端應用程式可見。 這也是透過走過清單來完成的`CDynLinkLibrary`。

在 MFC 高級概念範例[DLLHUSK](../overview/visual-cpp-samples.md)中,清單如下所示:

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

MFCxx.DLL 通常在資源和類清單中排在最後。 MFCxx.DLL 包括所有標準 MFC 資源,包括所有標準命令指示的提示字串。 將其放在清單的尾部允許 DLL 和用戶端應用程式本身沒有自己的標準 MFC 資源副本,而是依賴於 MFCxx.DLL 中的共享資源。

將所有 DLL 的資源和類名稱合併到用戶端應用程式的名稱空間中,缺點是必須小心您選擇什麼的代表或名稱。 當然,您可以通過不將資源`CDynLinkLibrary`或物件匯出到用戶端應用程式來禁用此功能。 [DLLHUSK](../overview/visual-cpp-samples.md)示例使用多個標頭檔管理共享資源名稱空間。 有關使用共用資源檔的更多提示[,請參閱技術說明 35。](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

### <a name="initializing-the-dll"></a>初始化 DLL

如上所述,您通常需要創建一個`CDynLinkLibrary`物件,以便將資源和類匯出到用戶端應用程式。 您需要提供匯出的入口點才能初始化 DLL。 最小,這是一個無效例程,不需要任何參數,也不返回任何內容,但它可以是任何你喜歡的。

如果要使用 DLL 的每個用戶端應用程式都必須呼叫此初始化例程(如果使用此方法)。 您也可以在調用`CDynLinkLibrary``AfxInitExtensionModule`後在`DllMain`您的 中分配此物件。

初始化例程必須在當前應用程式的堆`CDynLinkLibrary`中創建一個物件,並連接到 MFC 擴展 DLL 資訊。 這可以通過以下操作完成:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

本示例中的例程名稱*InitXxxDLL*可以是所需的任何內容。 它不需要**外部「C」,** 但這樣做會使匯出清單更易於維護。

> [!NOTE]
> 如果使用常規 MFC DLL 的 MFC 擴展 DLL,則必須匯出此初始化函數。 在使用任何 MFC 擴展 DLL 類或資源之前,必須從常規 MFC DLL 調用此功能。

### <a name="exporting-entries"></a>匯出項目

匯出類的簡單方法是在要匯出的每個類和`__declspec(dllimport)`全域`__declspec(dllexport)`函數上使用和。 這使得它更容易,但比命名每個入口點(如下所述)的效率要低,因為您不太瞭解匯出哪些函數,並且不能按 ddinal 匯出函數。 TESTDLL1 和 TESTDLL2 使用此方法匯出其條目。

更有效的方法(以及 MFCxx.DLL 使用的方法)是透過命名中的每個項目來手動匯出每個項目。DEF 檔。 由於我們從 DLL 匯出選擇性匯出(即不是所有介面),因此我們必須決定要匯出的特定介面。 這很困難,因為您必須以中的條目的形式將混亂的名稱指定給連結器。DEF 檔。 不要匯出任何C++類,除非您確實需要為其提供符號連結。

如果嘗試使用 匯出C++類。DEF 檔之前,您可能需要開發一個工具來自動生成此清單。 這可以使用兩階段連結過程來完成。 連結 DLL,無需匯出,並允許連結器產生 。MAP 檔。 .MAP 檔案可用於生成應匯出的函數清單,因此,對於某些重新排列,它可用於為生成的 EXPORT 條目。DEF 檔。 MFCxx.DLL 和 OLE 和資料庫 MFC 擴展 DLL 的匯出清單(數為數千)是使用此過程生成的(儘管它不是完全自動的,需要偶爾進行一次手動調整)。

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLink圖書館

MFC 擴展 DLL`CWinApp`沒有其 自己的派生物件;相反,`CWinApp`它必須與用戶端應用程式的派生物件一起工作。 這意味著客戶端應用程式擁有主消息泵、空閒環路等。

如果您的 MFC 擴展 DLL 需要為每個應用程式維護額外的數據`CDynLinkLibrary`,則可以從 派生新類並在上面描述的 InitXxxDLL 例程中創建它。 執行時,DLL 可以檢查當前`CDynLinkLibrary`應用程式的物件清單,以查找該特定 MFC 擴展 DLL 的物件。

### <a name="using-resources-in-your-dll-implementation"></a>在 DLL 上使用資源

如上所述,默認資源負載將遍歷查找具有請求資源的第`CDynLinkLibrary`一個 EXE 或 DLL 的物件清單。 所有 MFC API 以及所有內部`AfxFindResourceHandle`代碼都用於 遍曆資源清單以查找任何資源,無論資源可能駐留在何處。

如果只想從特定位置載入資源,請使用`AfxGetResourceHandle`API`AfxSetResourceHandle`並 保存舊句柄並設置新句柄。 在返回到用戶端應用程式之前,請確保還原舊資源句柄。 示例 TESTDLL2 使用此方法顯式載入功能表。

遍行清單有缺點是速度稍慢,需要管理資源 ID 範圍。 它的優點是,連結到多個 MFC 擴展 DLL 的用戶端應用程式可以使用任何 DLL 提供的資源,而無需指定 DLL 實例句柄。 `AfxFindResourceHandle`是用於遍走資源清單以查找給定匹配項的 API。 它獲取資源的名稱和類型,並返回首次找到的資源句柄(或 NULL)。

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>編寫使用 DLL 版本的應用程式

### <a name="application-requirements"></a>應用要求

使用 MFC 分享版本的應用程式必須遵循幾個簡單的規則:

- 它必須具有物件`CWinApp`,並遵循消息泵的標準規則。

- 它必須使用一組必需的編譯器標誌進行編譯(見下文)。

- 它必須與 MFCxx 導入庫連結。 通過設置所需的編譯器標誌,MFC 標頭確定應用程式應在連結時連結到哪個庫。

- 要執行執行檔,MFCxx.DLL 必須位於路徑或 Windows 系統目錄中。

### <a name="building-with-the-development-environment"></a>與開發環境一起建構

如果將內部 makefile 與大多數標準預設值一起使用,則可以輕鬆地更改專案以生成 DLL 版本。

以下步驟假定您具有與 NAFXCWD 連結的正常運行的 MFC 應用程式。LIB(用於調試)和 NAFXCW。LIB(用於零售),您希望將其轉換為使用 MFC 庫的共用版本。 您正在運行 Visual C++ 環境,並且具有內部專案檔。

1. 在「**專案」** 選單上,單擊「**屬性**」。 在 **「項目預設值****」下的「一般**」頁中,將 Microsoft 基礎類設定為在共用 DLL (MFCxx.dll)**中使用 MFC。**

### <a name="building-with-nmake"></a>使用 NMAKE 建造

如果您使用的是 Visual C++的外部 makefile 功能,或者直接使用 NMAKE,則必須編輯 makefile 以支援編譯器和連結器選項

必要編譯器標誌:

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

標準 MFC 標頭需要定義此符號:

- **/MD**應用程式必須使用 C 執行時庫的 DLL 版本

所有其他編譯器標誌都遵循 MFC 預設值(例如,_DEBUG用於調試)。

編輯庫的連結器清單。 更改 NAFXCWD。LIB 到 MFCxxD.LIB 並更改 NAFXCW。LIB 到 MFCxx.LIB。 替換 LIBC。與 MSVCRT 的 LIB。自由。 與任何其他 MFC 庫一樣,將 MFCxxD.LIB 放在任何 C 運行時庫**之前**非常重要。

可以選擇將 **/D_AFXDLL**添加到零售和調試資源編譯器選項(實際使用 **/R**編譯資源的選項)。 這樣,通過共用 MFC DLL 中存在的資源,最終可執行檔變小。

進行這些更改後,需要進行完全重建。

### <a name="building-the-samples"></a>建立範例

大多數 MFC 示例程式都可以從 Visual C++ 或從命令列的共用 NMAKE 相容 MAKEFILE 構建。

要將這些範例的任何一個轉換為 MFCxx.DLL,可以載入 。MAK 檔案進入可視化C++並設置上述項目選項。 如果使用 NMAKE 生成,則可以在 NMAKE 命令列上指定「AFXDLL_1」,並使用共用 MFC 庫生成範例。

MFC 高級概念示例[DLLHUSK](../overview/visual-cpp-samples.md)採用 MFC 的 DLL 版本構建。 此示例不僅說明瞭如何建構與 MFCxx.DLL 連結的應用程式,還說明瞭 MFC DLL 打包選項的其他功能,如本文說明的稍後描述的 MFC 擴展 DLL。

### <a name="packaging-notes"></a>包裝說明

DLL 的零售版本 (MFCxx[U])。DLL) 可自由再分發。 DLL 的調試版本不可自由再分發,應僅在應用程式開發期間使用。

調試 DLL 提供調試資訊。 通過使用 VisualC++調試器,可以追蹤應用程式以及 DLL 的執行。 版本 DLL (MFCxx_U])。DLL) 不包含調試資訊。

如果自定義或重建 DLL,則應將其稱為 MFC SRC 檔 MFCDLL 以外的內容。MAK 描述了產生選項,並包含重新命名 DLL 的邏輯。 重新命名檔案是必要的,因為這些 DLL 可能由許多 MFC 應用程式共用。 讓自定義版本的 MFC DLL 替換安裝在系統上的 MFC DLL 可能會使用共用 MFC DLL 中斷另一個 MFC 應用程式。

不建議重建 MFC DLL。

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>如何實施 MFCxx.DLL

以下部分介紹如何實現 MFC DLL (MFCxx.DLL 和 MFCxxD.DLL)。 如果只想將 MFC DLL 與應用程式一起使用 MFC DLL,則瞭解此處的詳細資訊也並不重要。 此處的詳細資訊對於瞭解如何編寫 MFC 擴展 DLL 並非至關重要,但瞭解此實現可以説明您編寫自己的 DLL。

### <a name="implementation-overview"></a>實施概述

如上所述,MFC DLL 實際上是 MFC 擴展 DLL 的特殊情況。 它具有大量匯出大量類。 我們在 MFC DLL 中還執行一些其他操作,使其比常規 MFC 擴展 DLL 更特別。

### <a name="win32-does-most-of-the-work"></a>Win32 做大部分工作

16 位元版本的 MFC 需要許多特殊技術,包括堆疊段上的每個應用數據、由大約 80x86 程式集代碼創建的特殊段、每個進程異常上下文和其他技術。 Win32 直接支援 DLL 中的每個進程數據,這是您大多數時候想要的。 在大多數情況下,MFCxx.DLL 只是 NAFXCW。以 DLL 打包的 LIB。 如果查看 MFC 原始程式碼,你會發現很少#ifdef_AFXDLL,因為需要進行的特殊情況很少。 特殊案例專門處理 Windows 3.1 上的 Win32(也稱為 Win32)。 Win32s 不支援每進程 DLL 數據,因此 MFC DLL 必須使用線程本地存儲 (TLS) Win32 API 來獲取進程本地數據。

### <a name="impact-on-library-sources-additional-files"></a>對函庫源、其他檔案的影響

**_AFXDLL**版本對普通 MFC 類庫源和標頭的影響相對較小。 有一個特殊的版本檔(AFXV_DLL。H)以及額外的標頭檔(AFXDLL_。H) 包括主 AFXWIN。H 標頭。 AFXDLL_H 標頭`CDynLinkLibrary``_AFXDLL`包括 應用程式和 MFC 擴展 DLL 的類和其他實現詳細資訊。 AFXDLLX。H 標頭用於建構 MFC 擴展 DLL(有關詳細資訊,請參閱上文)。

MFC SRC 中 MFC 庫`_AFXDLL`的常規源在 #ifdef下具有一些附加条件代码。 其他源檔(DLLINIT)。CPP) 包含 MFC 共用版本的額外 DLL 初始化代碼和其他膠水。

為了構建 MFC 的共用版本,提供了其他檔。 (有關如何構建 DLL 的詳細資訊,請參閱下文。

- 兩。DEF 檔案用於匯出用於除錯 (MFCxxD.DEF) 和 DLL 版本 (MFCxx.DEF) 的 MFC DLL 入口點。

- A .RC 檔案 (MFCDLL.RC) 包含所有標準 MFC 資源和 DLL 的 VERSIONINFO 資源。

- A .CLW 檔案 (MFCDLL.CLW) 用於允許使用 ClassWizard 流覽 MFC 類。 注意:此功能對於 MFC 的 DLL 版本並不特別。

### <a name="memory-management"></a>記憶體管理

使用 MFCxx.DLL 的應用程式使用 MSVCRTxx.DLL(共用 C 運行時 DLL)提供的常見記憶體分配器。 應用程式、任何 MFC 擴展 DLL 以及 MFC DLL 本身使用此共用記憶體分配器。 通過使用共用 DLL 進行記憶體分配,MFC DLL 可以分配稍後由應用程式釋放的記憶體,反之亦然。 由於應用程式與 DLL 必須使用相同的分配器,因此不應重寫 C++全域**運算符 new****或刪除**。 相同的規則適用於 C 運行時記憶體分配例程的其餘部分(如**malloc、realloc、free****realloc****free**等 )。

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>__declspec (dllexport) 與 DLL 命名

我們不使用C++編譯器`class`**的__declspec(dllexport)** 功能。 相反,類庫源(MFCxx.DEF 和 MFCxxD.DEF)中包含匯出清單。 僅匯出這些選定的入口點集(函數和數據)。 其他符號(如 MFC 私有實現函數或類)不匯出 所有匯出都由單位完成,沒有駐留名稱或非居民名稱表中的字串名稱。

使用`class`**__declspec(dllexport)** 可能是構建較小 DLL 的可行替代方法,但在 MFC 等大型 DLL 的情況下,默認匯出機制具有效率和容量限制。

這一切意味著我們可以在版本 MFCxx.DLL 中打包大量功能,這些功能只有大約 800 KB,同時不會影響很多執行或載入速度。 如果不使用這種技術,MFCxx.DLL 會大 10 萬。 這也使得可以在的末尾添加其他入口點。DEF 檔案允許簡單的版本控制,同時不影響通過單位匯出的速度和大小效率。 MFC 類庫中的主要版本版本版本將更改庫名稱。 即 MFC30。DLL 是包含 MFC 類庫版本 3.0 的可再分發 DLL。 例如,在假設的 MFC 3.1 中升級此 DLL,DLL 將命名為 MFC31。而是 DLL。 同樣,如果修改 MFC 原始碼以生成 MFC DLL 的自訂版本,請使用其他名稱(最好是名稱中沒有"MFC"的名稱)。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
