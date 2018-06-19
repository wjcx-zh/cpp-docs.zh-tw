---
title: 'TN033: MFC 的 DLL 版本 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dll
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a247ffc36b3e0eb3e52c6f04949c693597d73064
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385238"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033：MFC 的 DLL 版本
此提示描述如何使用 MFCxx.DLL 和 mfcxxd.dll （其中 x 是 MFC 版本號碼） 指共用 MFC 應用程式與 MFC 擴充 Dll 的動態連結程式庫。 如需 MFC 的標準 Dll 的詳細資訊，請參閱[將 MFC 當成 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。  
  
 這個技術提示涵蓋三個層面的 Dll。 最後兩個適用於更進階使用者：  
  
- [您如何建置 MFC 擴充 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)  
  
- [您如何建置使用 MFC 的 DLL 版本的 MFC 應用程式](#_mfcnotes_writing_an_application_that_uses_the_dll_version)  
  
- [MFC 共用動態連結程式庫的方式實作](#_mfcnotes_how_the_mfc30.dll_is_implemented)  
  
 如果您想要建置使用可搭配非 MFC 應用程式 （稱為標準的 MFC DLL） 的 MFC DLL，請參閱[技術提示 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。  
  
## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>MFCxx.DLL 支援的概觀： 術語和檔案  
 **MFC 的標準 DLL**： 您可以使用標準的 MFC DLL 來建立獨立的 DLL 使用 MFC 類別的一部分。 應用程式或 DLL 界限之間的介面，"C"介面，以及用戶端應用程式沒有 MFC 應用程式。  
  
 這是支援在 MFC 1.0 中的 DLL 支援的版本。 中描述[技術提示 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)和 MFC 進階概念範例[DLLScreenCap](../visual-cpp-samples.md)。  
  
> [!NOTE]
>  從 Visual c + + 4.0 版，開始一詞**USRDLL**已經過時，已靜態連結至 MFC 之標準 MFC DLL 被取代。 您也可能會建置一般 MFC 動態連結至 MFC 的 DLL。  
  
 MFC 3.0 （和更新版本） 支援 MFC 的標準 Dll 包括 OLE 和資料庫類別的新功能。  
  
 **AFXDLL**： 這也稱為共用版本的 MFC 程式庫。 這是新的 DLL 支援加入 MFC 2.0 中。 在 MFC 程式庫本身處於數目 Dll （如下所述），用戶端應用程式或 DLL 動態連結它所需的 Dll。 應用程式/DLL 界限之間的介面是 C + + MFC 類別介面。 用戶端應用程式必須是 MFC 應用程式。 這可支援所有的 MFC 3.0 功能 (例外狀況： 資料庫類別不支援 UNICODE)。  
  
> [!NOTE]
>  自 Visual c + + 4.0 版，這種類型的 DLL 被指 「 擴充 DLL。 」  
  
 這個附註將會使用 MFCxx.DLL 來參考的整個 MFC DLL 集合，其中包括：  
  
-   偵錯： Mfcxxd.dll 指 （結合） 和 MFCSxxD.LIB （靜態）。  
  
-   發行： MFCxx.DLL （結合） 和 MFCSxx.LIB （靜態）。  
  
-   Unicode 偵錯： MFCxxUD.DLL （結合） 和 MFCSxxD.LIB （靜態）。  
  
-   Unicode 版本： MFCxxU.DLL （結合） 和 MFCSxxU.LIB （靜態）。  
  
> [!NOTE]
>  MFCSxx [U] [D]。LIB 文件庫中使用與 MFC 一起共用的 Dll。 這些程式庫包含必須以靜態方式連結至 DLL 的應用程式的程式碼。  
  
 連結至對應的應用程式匯入程式庫：  
  
-   偵錯： MFCxxD.LIB  
  
-   發行： MFCxx.LIB  
  
-   Unicode Debug: MFCxxUD.LIB  
  
-   Unicode 版本： MFCxxU.LIB  
  
 「 MFC 擴充 DLL"是建置在 MFCxx.DLL DLL （和/或其他 MFC 共用 Dll）。 這裡 MFC 元件架構會介入。 如果您有用的類別從 MFC 類別衍生，或建立另一個類似 MFC 的工具組，您可以將它放在 DLL 中。 DLL 會使用 MFCxx.DLL，最終的用戶端應用程式一樣。 如此可重複使用的分葉類別、 可重複使用的基底類別，以及可重複使用的檢視/文件類別。  
  
## <a name="pros-and-cons"></a>優缺點  
 為何應使用 MFC 的共用的版本  
  
-   使用共用的程式庫可能會導致較小的應用程式 （使用大部分的 MFC 程式庫的最小應用程式是不超過 10k）。  
  
-   共用的版本的 MFC 支援 MFC 擴充 Dll 和 MFC 的標準 Dll。  
  
-   建立使用共用的 MFC 程式庫的應用程式的速度比建置以靜態方式連結的 MFC 應用程式，因為它不需要連結至 MFC 本身。 特別是在**偵錯**連結器必須在其中壓縮的偵錯資訊的組建，連結的 DLL，已包含偵錯資訊，偵錯資訊變少了壓縮應用程式中。  
  
 為什麼應該不使用 MFC 的共用的版本：  
  
-   傳送使用共用的程式庫的應用程式需要您在出貨 MFCxx.DLL （以及其他） 與您的程式庫。 MFCxx.DLL 可以自由轉像許多 Dll，但您仍然必須安裝此 DLL 安裝程式中。 此外，您必須提供 MSVCRTxx.DLL，其中包含您的程式和 MFC Dll 本身都能使用的 C 執行階段程式庫。  
  
##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> 如何撰寫 MFC 擴充 DLL  
 MFC 擴充 DLL 是包含類別和函式，最好的 MFC 類別的功能撰寫的 DLL。 MFC 擴充 DLL 使用共用的 MFC Dll 相同的方式，應用程式所使用的是，有幾個其他考量：  
  
-   若要建置的應用程式使用共用的 MFC 程式庫與一些其他編譯器和連結器選項相似的建置程序。  
  
-   MFC 擴充 DLL 並沒有`CWinApp`-衍生的類別。  
  
-   MFC 擴充 DLL 必須提供特殊`DllMain`。 AppWizard 提供`DllMain`函式，您可以進行修改。  
  
-   MFC 擴充 DLL 通常會提供初始化常式，以建立**CDynLinkLibrary**如果 MFC 擴充 DLL 想要匯出`CRuntimeClass`es 或應用程式的資源。 在衍生的類別的**CDynLinkLibrary**可能會使用由 MFC 擴充 DLL 必須維護每個應用程式資料。  
  
 以下更詳細說明這些考量。 您也應該參閱 MFC 進階概念範例[DLLHUSK](../visual-cpp-samples.md)因為它會說明：  
  
-   建立使用共用的程式庫的應用程式。 (DLLHUSK。EXE 是 MFC 應用程式動態連結至 MFC 程式庫以及其他 Dll）。  
  
-   建置 MFC 擴充 DLL。 (請注意的特殊旗標時，例如`_AFXEXT`，用於建立 MFC 擴充 DLL)  
  
-   MFC 擴充 Dll 的兩個範例。 其中一個顯示 MFC 擴充 DLL 使用有限的匯出 (TESTDLL1) 和其他顯示匯出整個類別介面 (TESTDLL2) 的基本結構。  
  
 用戶端應用程式和任何 MFC 擴充 Dll 必須使用相同版本的 MFCxx.DLL。 您應該遵循的慣例 MFC DLL，並提供偵錯和零售 (/release) 您的 MFC 擴充 DLL 的版本。 這可讓用戶端程式的建置的應用程式的偵錯和零售版本，並將其連結與適當的偵錯或零售版本的所有 Dll。  
  
> [!NOTE]
>  因為 c + + 名稱修飾 （name-mangling），和匯出問題，請從 MFC 擴充 DLL 的 [匯出] 清單可能相同 DLL 的偵錯和零售版本和 Dll 之間的不同平台不同。 零售 MFCxx.DLL 有大約 2000年匯出進入點。偵錯 mfcxxd.dll 指大約 3000 已匯出的進入點。  
  
### <a name="quick-note-on-memory-management"></a>記憶體管理上的快速提示  
 「 記憶體管理，」 這個技術提示結尾附近一節描述 MFCxx.DLL 與 MFC 的共用版本的實作。 您需要知道實作只 MFC 擴充功能 DLL 此處所述的資訊。  
  
 MFCxx.DLL 和所有 MFC 擴充 Dll 載入到用戶端應用程式的位址空間會使用相同的記憶體配置器、 載入資源和其他 MFC 的 「 全域 」 狀態如同它們是相同的應用程式中。 因為非 MFC DLL 程式庫和以靜態方式連結至 MFC 的標準 MFC Dll 則完全相反，而且有它自己的記憶體集區超出每個 DLL 配置，這十分重要。  
  
 如果 MFC 擴充 DLL 配置記憶體，然後該記憶體可以自由地混合與其他應用程式配置的物件。 此外，如果使用共用的 MFC 程式庫的應用程式當機，保護的作業系統會維護其他任何 MFC 應用程式共用 DLL 的完整性。  
  
 同樣地其他 「 全域 」 的 MFC 狀態，例如目前的可執行檔載入資源，也會用戶端應用程式和所有 MFC 擴充 Dll，以及 MFCxx.DLL 本身之間共用。  
  
### <a name="building-an-mfc-extension-dll"></a>建置 MFC 擴充 DLL  
 您可以使用 AppWizard 建立 MFC 擴充 DLL 專案，並會自動產生適當的編譯器和連結器設定。 所以也會產生`DllMain`函式，您可以進行修改。  
  
 如果您要將現有的專案轉換成 MFC 擴充 DLL，開始建立使用共用的版本的 MFC 應用程式的標準規則，然後執行下列動作：  
  
-   新增 **/D_AFXEXT**編譯器旗標。 在 [專案屬性] 對話方塊中，選取 [C/c + +] 節點。 然後，選取前置處理器的類別。 新增`_AFXEXT`到定義的巨集 欄位中，每個項目以分號分隔。  
  
-   移除 **/Gy**編譯器參數。 在 [專案屬性] 對話方塊中，選取 [C/c + +] 節點。 然後，選取程式碼產生類別。 請確定未啟用 「 啟用函式層級連結 」 的選項。 這會讓匯出的類別，因為連結器將不會移除未參考函式更加簡單。 如果原始的專案用來建置一般 MFC DLL 靜態連結至 MFC，變更 **/MT [d]** 編譯器選項以 **/MD [d]**。  
  
-   建立與匯出程式庫 **/DLL**連結選項。 這會設定當您建立新的目標，指定做為目標類型的 Win32 動態連結程式庫。  
  
### <a name="changing-your-header-files"></a>變更標頭檔  
 MFC 擴充 DLL 的目標通常是匯出一或多個可以使用該功能的應用程式的一些常見的功能。 這可簡化為匯出的類別和全域函式可供用戶端應用程式。  
  
 若要這樣做，您必須確定每個成員函式會標記為匯入或匯出適當。 這需要特殊的宣告： **__declspec （dllexport)** 和 **__declspec （dllimport)**。 當用戶端應用程式使用您的類別時，要將它們宣告為 **__declspec （dllimport)**。 建立 MFC 擴充 DLL 本身時，它們應該宣告為 **__declspec （dllexport)**。 此外，函式必須實際匯出，以便用戶端程式繫結至其在載入時間。  
  
 若要匯出整個類別，請使用**AFX_EXT_CLASS**類別定義中。 定義此巨集做為架構 **__declspec （dllexport)** 時 **_AFXDLL**和`_AFXEXT`定義，但定義為 **__declspec （dllimport)** 時`_AFXEXT`未定義。 `_AFXEXT` 建置您的 MFC 擴充 DLL 時，如上面所述，是只會定義。 例如:   
  
```  
class AFX_EXT_CLASS CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
### <a name="not-exporting-the-entire-class"></a>不會匯出整個類別  
 有時您可能想要匯出只需要的個別成員類別。 例如，如果您要匯出`CDialog`-衍生的類別，您可能只需要將匯出的建構函式和`DoModal`呼叫。 您可以匯出使用 DLL 的這些成員。DEF 檔案，但您也可以使用**AFX_EXT_CLASS**的相同方式進行您需要匯出的個別成員上。  
  
 例如:   
  
```  
class CExampleDialog : public CDialog  
{  
public:  
    AFX_EXT_CLASS CExampleDialog();
AFX_EXT_CLASS int DoModal();
*// rest of class definition  
 .  
 .  
 .  
};  
```  
  
 當您這樣做時，您可能會遇到其他問題因為您不再想要匯出類別的所有成員。 問題的方式是 MFC 巨集工作。 有幾個 MFC 的協助程式巨集實際宣告或定義的資料成員。 因此，這些資料成員也必須從您的 DLL 匯出。  
  
 例如，`DECLARE_DYNAMIC`建置 MFC 擴充 DLL 時，如下所示定義巨集：  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
    static CRuntimeClass* PASCAL _GetBaseClass();

\  
    public: \  
    static AFX_DATA CRuntimeClass class##class_name; \  
    virtual CRuntimeClass* GetRuntimeClass() const;

\  
```  
  
 開始行 「 靜態`AFX_DATA`"會宣告您的類別內的靜態物件。 若要正確匯出這個類別，並從用戶端存取執行階段資訊。EXE，您需要匯出這個靜態物件。 因為以修飾詞宣告靜態物件`AFX_DATA`，您只需要定義`AFX_DATA`是 **__declspec （dllexport)** 建置 DLL 時，它定義為 **__declspec（dllimport)** 建置您的用戶端可執行檔時。  
  
 如上所述， **AFX_EXT_CLASS**已經在這種方式定義。 您只需要重新定義`AFX_DATA`是相同**AFX_EXT_CLASS**周圍類別定義。  
  
 例如:   
  
```  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
class CExampleView : public CView  
{  
    DECLARE_DYNAMIC() *// ... class definition ...  
};  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
 MFC 一定會使用`AFX_DATA`符號定義在其巨集，因此這項技術可用於所有這類案例中的資料項目上。 例如，它就能用於`DECLARE_MESSAGE_MAP`。  
  
> [!NOTE]
>  如果您要匯出整個類別，而不是所選的類別的成員，靜態資料成員會自動匯出。  
  
 您可以使用相同的技巧，自動匯出`CArchive`引出運算子的類別使用`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`巨集。 匯出封存運算子的類別宣告方括號 (位於。H 檔案） 為下列程式碼：  
  
```  
#undef AFX_API  
#define AFX_API AFX_EXT_CLASS  
 
<your class declarations here>  
 
#undef AFX_API  
#define AFX_API  
```  
  
### <a name="limitations-of-afxext"></a>_AFXEXT 的限制  
 您可以使用 _**AFXEXT**您 MFC 擴充 Dll 只要您不需要多個圖層的 MFC 擴充 Dll 的前置處理器符號。 如果您有 MFC 擴充 Dll 呼叫，或衍生自類別，在您自己的 MFC 擴充 Dll，然後從 MFC 類別衍生，您必須使用您自己的前置處理器符號，以避免模稜兩可。  
  
 問題是，在 Win32 中，您必須明確宣告為任何資料 **__declspec （dllexport)** 是否要從 DLL 匯出和 **__declspec （dllimport)** 是否要從 DLL 匯入。 當您定義`_AFXEXT`，MFC 標頭，確定**AFX_EXT_CLASS**定義正確。  
  
 當您有多個圖層，一個符號例如**AFX_EXT_CLASS**不足夠，因為 MFC 擴充 DLL 可能會匯出新的類別，以及從另一個 MFC 擴充 DLL 匯入其他類別。 若要處理這個問題，使用特殊的前置處理器符號，指出您要建置 DLL 本身而非使用 DLL。 例如，假設有兩個 MFC 擴充 Dll、 A.DLL 和 B.DLL。 每個分別匯出 A.H 和 B.H 中的某些類別。 B.DLL 會使用 A.DLL 類別。 標頭檔看起來可能像這樣：  
  
```  
/* A.H */  
#ifdef A_IMPL  
 #define CLASS_DECL_A   __declspec(dllexport)  
#else  
 #define CLASS_DECL_A   __declspec(dllimport)  
#endif  
 
class CLASS_DECL_A CExampleA : public CObject  
{ ... class definition ... };  
 
/* B.H */  
#ifdef B_IMPL  
 #define CLASS_DECL_B   __declspec(dllexport)  
#else  
 #define CLASS_DECL_B   __declspec(dllimport)  
#endif  
 
class CLASS_DECL_B CExampleB : public CExampleA  
{ ... class definition .. };  
```  
  
 A.DLL 建置時，它內建與 **/D A_IMPL**而且 B.DLL 建置時，它會根據 **/D B_IMPL**。 每一個 dll 中使用不同的符號，匯出 CExampleB 和 CExampleA 建置 B.DLL 時匯入。 CExampleA，建置 A.DLL 時匯出並匯入由 B.DLL （或其他用戶端） 時。  
  
 使用內建時，無法執行這種類型的分層**AFX_EXT_CLASS**和`_AFXEXT`前置處理器符號。 上述的技巧來解決這個問題，方式沒有不同的是建置其 OLE、 資料庫和網路 MFC 擴充 Dll 時，會使用 MFC 的機制。  
  
### <a name="not-exporting-the-entire-class"></a>不會匯出整個類別  
 同樣地，您必須採取特別注意，當您不想要匯出整個類別。 您必須確定建立的 MFC 巨集的必要資料項目都正確匯出。 作法是藉由重新定義**AFX_DATA**特定類別的巨集。 這應該在完成任何您不想要匯出整個類別的時間。  
  
 例如:   
  
```  
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
*//class definition   
 .  
 .  
 .  
};  
 
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### <a name="dllmain"></a>DllMain  
 以下是您應該將您的 MFC 擴充 DLL 的主要原始程式檔的實際程式碼。 它應該來自之後包含標準。 請注意，當您使用 AppWizard 建立的 MFC 擴充 DLL 的初學者檔案時，它會提供`DllMain`您。  
  
```  
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
  
 呼叫`AfxInitExtensionModule`擷取模組執行階段類別 (`CRuntimeClass`結構) 以及其物件處理站 (`COleObjectFactory`物件) 使用更新版本時**CDynLinkLibrary**建立物件。 （選擇性） 呼叫`AfxTermExtensionModule`可讓 MFC 清理 MFC 擴充 DLL 每個處理序中斷連結時 (也就是當處理序結束，或可能是卸載 DLL， **FreeLibrary**呼叫) 從 MFC 擴充 DLL. 因為大部分的 MFC 擴充 Dll 不會以動態方式載入 （通常，這些連結透過其匯入程式庫），呼叫`AfxTermExtensionModule`通常並不需要。  
  
 如果您的應用程式載入，而且會動態釋放 MFC 擴充 Dll，請務必呼叫`AfxTermExtensionModule`如上所示。 也請務必使用`AfxLoadLibrary`和`AfxFreeLibrary`(而不是 Win32 函式**LoadLibrary**和**FreeLibrary**) 如果您的應用程式使用多個執行緒，或者它會以動態方式載入 MFC擴充 DLL。 使用`AfxLoadLibrary`和`AfxFreeLibrary`確保執行時載入及卸載 MFC 擴充 DLL 的啟動和關閉程式碼而損毀全域 MFC 狀態。  
  
 標頭檔 AFXDLLX。H 包含特殊 MFC 擴充 Dll，例如的定義中使用的結構定義`AFX_EXTENSION_MODULE`和**CDynLinkLibrary**。  
  
 全域*extensionDLL*必須宣告所示。 與不同的是 MFC 的 16 位元版本，您可以配置的記憶體，並在此期間，呼叫 MFC 函式，因為 MFCxx.DLL 完全初始化的時間您`DllMain`呼叫。  
  
### <a name="sharing-resources-and-classes"></a>共用資源和類別  
 簡單的 MFC 擴充 Dll 只需要將幾個低頻寬函式匯出至用戶端應用程式而無其他。 多個使用者介面大量 Dll 可能想要將資源和 c + + 類別匯出至用戶端應用程式。  
  
 匯出資源是透過資源的清單。 每個應用程式是單向連結的清單**CDynLinkLibrary**物件。 大部分的載入資源的標準 MFC 實作資源時，尋找在目前的資源模組的第一個 (`AfxGetResourceHandle`) 如果不找到查核行程的清單**CDynLinkLibrary**嘗試載入的物件要求的資源。  
  
 相似的動態建立的 c + + 物件指定 c + + 類別名稱。 MFC 物件還原序列化機制需要將所有`CRuntimeClass`登錄，讓它可以藉由動態建立 c + + 物件的所需的類型，根據項目先前已儲存重新建構的物件。  
  
 如果您想要使用您的 MFC 擴充 DLL 中的類別，用戶端應用程式`DECLARE_SERIAL`，則您必須匯出為用戶端應用程式可以看到您的類別。 這也藉由查核完成**CDynLinkLibrary**清單。  
  
 在 MFC 進階概念範例的情況下[DLLHUSK](../visual-cpp-samples.md)，清單看起來像這樣：  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
 |      |  
    TESTDLL2.DLL TESTDLL2.DLL  
 |      |  
    TESTDLL1.DLL TESTDLL1.DLL  
 |      |  
 |      |  
    MFC90D.DLL MFC90.DLL  
```  
  
 MFCxx.DLL 是根據資源和類別清單通常是最後一個項目。 MFCxx.DLL 包括所有標準 MFC 資源，包括所有標準命令 Id 的提示字串。 Dll 和用戶端應用程式本身不需要將它放在清單結尾可讓他們自己的標準 MFC 資源，但若要依賴 MFCxx.DLL 中共用的資源而的複本。  
  
 合併至用戶端應用程式的命名空間的資源和所有 dll 的類別名稱都有缺點是，您應特別小心，哪些識別碼或名稱。 您可以當然停用這項功能不會匯出任何您的資源或**CDynLinkLibrary**用戶端應用程式的物件。 [DLLHUSK](../visual-cpp-samples.md)範例使用多個標頭檔來管理共用的資源命名空間。 請參閱[技術附註 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)如需使用共用的資源檔的秘訣。  
  
### <a name="initializing-the-dll"></a>初始化 DLL  
 如上面所述，您通常會想要建立**CDynLinkLibrary**才能匯出您的資源和類別，用戶端應用程式的物件。 您必須提供初始化的 DLL 匯出的進入點。 使用最低限度，這是在 void 常式不接受引數並傳回任何內容，但它可以是任何您喜歡的項目。  
  
 每個想要使用您的 DLL 的用戶端應用程式必須呼叫這個初始化常式，如果您使用這個方法。 您也可能會配置此**CDynLinkLibrary**物件存放至您`DllMain`之後呼叫`AfxInitExtensionModule`。  
  
 初始化常式必須建立**CDynLinkLibrary**物件在目前應用程式的堆積中，連線到您的 MFC 擴充 DLL 的資訊。 這可以使用下列：  
  
```  
extern "C" extern void WINAPI InitXxxDLL()  
{  
    new CDynLinkLibrary(extensionDLL);

}  
```  
  
 常式的名稱， *InitXxxDLL*在此範例中，可以是您想要的任何項目。 不需要`extern "C"`，但是，這樣可讓您更輕鬆地維護的 [匯出] 清單。  
  
> [!NOTE]
>  如果您使用您從一般 MFC DLL 的 MFC 擴充 DLL，您必須匯出初始化函式。 使用任何 MFC 擴充 DLL 的類別或資源之前，必須與一般 MFC 的 DLL 呼叫此函數。  
  
### <a name="exporting-entries"></a>匯出的項目  
 若要匯出您的類別的簡單方式是使用 **__declspec （dllimport)** 和 **__declspec （dllexport)** 上每個類別和您想要匯出的全域函式。 這可讓您更輕鬆，但效率比命名 （如下所述） 的每個進入點，因為您可以控制哪些函式會匯出較少，而且您無法依序數匯出的函式。 TESTDLL1 和 TESTDLL2 使用這個方法，若要匯出其項目。  
  
 更有效率的方法 （和 MFCxx.DLL 所使用的方法） 不會匯出每個項目以手動方式來命名每個項目。DEF 檔案。 我們正在匯出選擇性匯出從我們的 DLL （也就是不所有項目），因為我們必須決定哪些我們想要匯出的特定介面。 這是很困難，因為您必須指定損害的名稱給連結器中的項目表單中。DEF 檔案。 不要匯出任何 c + + 類別，除非您真的需要的符號連結。  
  
 如果您嘗試匯出 c + + 類別使用。DEF 檔案之前，您可能想要開發工具，以自動產生這份清單。 這可以使用兩階段連結程序。 連結您的 DLL，一次使用任何匯出，並讓連結器產生。對應檔。 。對應檔案可以用來產生要匯出的函式的清單，因此有一些重新排列，它可以用來產生匯出項目您。DEF 檔案。 MFCxx.DLL 和 OLE 和幾千在數目、 資料庫 MFC 擴充 Dll 的匯出清單產生程序 （雖然它不是完全自動的而且需要某些手動微調每隔一段）。  
  
### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs。CDynLinkLibrary  
 MFC 擴充 DLL 並沒有`CWinApp`-衍生自己的物件; 而是必須與中一起`CWinApp`-衍生的用戶端應用程式的物件。 這表示用戶端應用程式擁有主要訊息幫浦，閒置迴圈，依此類推。  
  
 如果您的 MFC 擴充 DLL 需要維護額外的資料，每個應用程式，您可以衍生新的類別，從**CDynLinkLibrary**並建立常式上述 InitXxxDLL 中。 DLL 執行時，可以檢查目前的應用程式清單**CDynLinkLibrary**来找到該特定 MFC 擴充 DLL 的物件。  
  
### <a name="using-resources-in-your-dll-implementation"></a>您的 DLL 實作中使用的資源  
 預設資源負載如上面所述，將逐步引導的清單**CDynLinkLibrary**尋找第一個 EXE 或 DLL，具有要求之資源的物件。 所有的 MFC 應用程式開發介面，以及內部的程式碼會使用所有`AfxFindResourceHandle`查核資源清單來尋找無論可能存在其中的任何資源。  
  
 如果您想要只從特定位置中載入資源，使用 Api`AfxGetResourceHandle`和`AfxSetResourceHandle`儲存舊的控制代碼，並將新的控制代碼。 請務必還原舊的資源控制代碼傳回至用戶端應用程式之前。 TESTDLL2 這個範例會使用這種方法，明確載入功能表。  
  
 查核清單有缺點，它會稍微慢一點，而且必須管理資源 ID 範圍。 它的優點是連結到數個 MFC 擴充 Dll 的用戶端應用程式可以使用任何提供 DLL 的資源，而不需要指定 DLL 的執行個體控制代碼。 `AfxFindResourceHandle` API 用查核資源清單來查詢給定的相符項目。 它會使用名稱和資源類型，並傳回其第一次找到的資源控制代碼 （或 NULL）。  
  
##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> 撰寫的應用程式使用的 DLL 版本  
  
### <a name="application-requirements"></a>應用程式的需求  
 使用 MFC 的共用的版本的應用程式必須遵循一些簡單的規則：  
  
-   它必須有`CWinApp`物件，並依照訊息幫浦的標準規則。  
  
-   它必須使用一組必要的編譯器旗標 （請參閱下文） 進行編譯。  
  
-   它必須與 MFCxx 匯入程式庫連結。 藉由設定必要的編譯器旗標，MFC 標頭在連結階段決定哪些應用程式應該連結的程式庫。  
  
-   若要執行可執行檔，MFCxx.DLL 必須在路徑上或在 Windows 系統目錄中。  
  
### <a name="building-with-the-development-environment"></a>建立與開發環境  
 如果您使用內部 makefile 與大部分的標準預設值，您可以輕鬆地變更要建置的 DLL 版本的專案。  
  
 下列步驟假設您有與 NAFXCWD 連結正常運作的 MFC 應用程式。LIB （適用於偵錯） 和 NAFXCW。LIB （適用於零售），而且您想要將它轉換成使用共用的版本的 MFC 程式庫。 您正在執行的 Visual c + + 環境，而且有內部的專案檔。  
  
1.  在**專案**功能表上，按一下 **屬性**。 在**一般**頁面**專案預設值**，若要設定 Microsoft Foundation Classes**使用 MFC 的共用 dll** (MFCxx(d).dll)。  
  
### <a name="building-with-nmake"></a>使用 NMAKE 建置  
 如果您使用外部 makefile 功能的 Visual c + + 中，或直接使用 NMAKE，您必須編輯您的 makefile，來支援編譯器和連結器選項  
  
 必要的編譯器旗標：  
  
 **/ D_AFXDLL /MD**  
 **/ D_AFXDLL**  
  
 標準 MFC 標頭需要定義這個符號：  
  
 **/MD**  
 應用程式必須使用 C 執行階段程式庫的 DLL 版本  
  
 所有其他的編譯器旗標會遵循 MFC 預設值 (例如，針對偵錯 _DEBUG)。  
  
 編輯程式庫的連結器清單。 變更 NAFXCWD。以 MFCxxD.LIB LIB，並將變更 NAFXCW。MFCxx.LIB LIB。 取代 LIBC。LIB MSVCRT 與。LIB。 與其他 MFC 程式庫，所以重要位於 MFCxxD.LIB**之前**任何 C 執行階段程式庫。  
  
 選擇性地加入 **/D_AFXDLL**為您的零售和偵錯資源編譯器選項 (實際上會編譯與資源的一個 **/R**)。 這可讓您最終可執行檔小共用 MFC Dll 中的資源。  
  
 進行這些變更之後，需要完整重建。  
  
### <a name="building-the-samples"></a>建置範例  
 您可以建立大部分的 MFC 範例程式，從 Visual c + + 或共用的相容 NMAKE MAKEFILE，從命令列。  
  
 若要轉換的這些範例使用 MFCxx.DLL 任何，您可以載入。MAK 讓 Visual c + + 檔案，並設定專案選項，如上面所述。 如果您使用 NMAKE 組建，您可以指定"AFXDLL = 1"上 NMAKE 命令列，並且會建立使用共用的 MFC 程式庫範例。  
  
 MFC 進階概念範例[DLLHUSK](../visual-cpp-samples.md)使用 MFC 的 DLL 版本所建置。 此範例不只會說明如何建置與 MFCxx.DLL，連結的應用程式，但它也說明 MFC DLL 封裝選項，例如 MFC 擴充 Dll，這個技術提示後文所述的其他功能。  
  
### <a name="packaging-notes"></a>封裝資訊  
 零售版本的 Dll (MFCxx [U]。DLL) 是免費轉散發。 不能自由轉散發 Dll 的偵錯版本，並應該只在您的應用程式開發期間使用。  
  
 提供偵錯 Dll 的偵錯資訊。 藉由使用 Visual c + + 偵錯工具，您可以追蹤執行的應用程式，以及 DLL。 釋放 Dll (MFCxx [U]。DLL) 並包含偵錯資訊。  
  
 如果您自訂或重建 Dll，然後您應該呼叫這些項目 」 MFCxx"MFC SRC 檔 MFCDLL 以外。MAK 說明組建選項，並包含重新命名 DLL 的邏輯。 重新命名檔案是有必要，，因為這些 Dll 可能由許多 MFC 應用程式共用。 讓您自訂的 MFC Dll 取代版本安裝在系統上可能會中斷另一個使用共用的 MFC Dll 的 MFC 應用程式。  
  
 建議您不要重建 MFC Dll。  
  
##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> 如何實作 MFCxx.DLL  
 下列章節描述如何實作 MFC DLL （MFCxx.DLL 和 mfcxxd.dll 指）。 了解的詳細資料也不很重要，如果您想要是使用您的應用程式的 MFC DLL。 詳細資料不是必要的以了解如何撰寫 MFC 擴充 DLL，但是了解這項實作可協助您撰寫您自己的 DLL。  
  
### <a name="implementation-overview"></a>實作概觀  
 MFC DLL 實際上是 MFC 擴充 DLL 的特殊案例，如上面所述。 它有非常大量的類別是大量匯出。 有幾個其他件事，我們在 MFC DLL，可讓您更特殊比一般 MFC 擴充 DLL。  
  
### <a name="win32-does-most-of-the-work"></a>Win32 會執行大部分的工作  
 MFC 的 16 位元版本需要一些特殊的技術，包括每個應用程式資料上的堆疊區段中，某些 80x86 組譯程式碼、 處理序專屬例外狀況內容和其他技術所建立的特殊區段。 Win32 直接支援同處理序資料在 DLL 中，這是您想在大多數情況。 在大部分情況 MFCxx.DLL 是只 NAFXCW。封裝在 DLL 中的 LIB。 如果您看一下 MFC 原始程式碼，您會發現很少 #ifdef _AFXDLL，因為有很少需要進行的特殊情況。 會有特別處理 （亦稱為 win32） Windows 3.1 上 Win32 特殊案例。 Win32 並不支援同處理序 DLL 的資料，因此 MFC DLL 必須使用執行緒區域儲存區 (TLS) 來取得處理程序的本機資料的 Win32 Api 直接。  
  
### <a name="impact-on-library-sources-additional-files"></a>對程式庫來源、 其他檔案的影響  
 所造成的影響 **_AFXDLL**上標準的 MFC 類別程式庫來源和標頭版本是相當小。 沒有特殊版檔案 (AFXV_DLL。H），以及額外的標頭檔 (AFXDLL_。H） 包含主要 AFXWIN。H 標頭。 AFXDLL_。H 標頭包含**CDynLinkLibrary**類別和其他實作詳細資料，這兩者的 **_AFXDLL**應用程式和 MFC 擴充 Dll。 AFXDLLX。用於建立 MFC 擴充 Dll （如需詳細資訊請參閱以上） 提供 H 標頭。  
  
 MFC 程式庫在 MFC SRC 規則來源有一些額外的條件式程式碼底下 **_AFXDLL** #ifdef。 其他的原始程式檔 (DLLINIT。CPP) 包含額外的初始化程式碼和其他黏附共用版本的 MFC。  
  
 若要建立 MFC 共用的版本，請提供其他檔案。 （請參閱下列如何建置 DLL 的詳細資料。）  
  
-   兩個。DEF 檔案可用來匯出偵錯 (MFCxxD.DEF) 的 MFC DLL 進入點，然後放開 (MFCxx.DEF) 版本的 DLL。  
  
-   。RC 檔 (MFCDLL。RC) 會包含所有標準 MFC 資源和 VERSIONINFO 資源 dll。  
  
-   A。CLW 檔案 (MFCDLL。CLW) 被提供使用 ClassWizard 允許瀏覽 MFC 類別。 注意： 這項功能不是特定 MFC 的 DLL 版本。  
  
### <a name="memory-management"></a>記憶體管理  
 使用 MFCxx.DLL 的應用程式會使用一般的記憶體配置器 MSVCRTxx.DLL，共用的 C 執行階段 DLL 所提供。 應用程式、 任何 MFC 擴充 Dll，以及 MFC Dll 本身會使用此共用的記憶體配置器。 使用的記憶體配置共用的 DLL，MFC Dll 可以配置應用程式，反之亦然，稍後會釋放的記憶體。 因為應用程式和 DLL 必須使用相同的配置器，您不應覆寫通用的 c + +`operator new`或`operator delete`。 相同的規則會套用到其餘的 C 執行階段記憶體配置常式 (例如`malloc`， `realloc`，**可用**，等等)。  
  
### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>序數和類別 __declspec （dllexport） 和 DLL 命名  
 我們不會將`class` **__declspec （dllexport)** c + + 編譯器的功能。 相反地，匯出清單會包含 （MFCxx.DEF 和 MFCxxD.DEF） 的類別程式庫來源。 匯出只這些選取的一組 （函式和資料） 的進入點。 其他符號，例如 MFC 私用實作函式或類別，不會匯出序數沒有內建或非內建名稱表格中的字串名稱來完成所有的匯出。  
  
 使用`class` **__declspec （dllexport)** 可能是可行的替代方案來建立較小的 Dll，但若為大型的 DLL，像是匯出機制的預設值，MFC 具有效率和容量限制。  
  
 意思就是所有為何，我們可以將封裝大量 MFCxx.DLL 才約 800 KB，而不危害多執行或載入速度的版本中的功能。 MFCxx.DLL 已經 100k 較大這項技術尚未使用。 這也可讓以新增其他的進入點的結尾。允許簡單的版本控制，而不會危害速度和大小的效率依序數匯出.DEF 檔案。 MFC 類別庫中的主要版本修訂將會變更程式庫名稱。 也就是說，MFC30。DLL 是包含 MFC 類別程式庫 3.0 版可轉散發 DLL。 此 dll，升級說，假設 MFC 3.1 中，DLL 會名為 MFC31。DLL 改為。 同樣地，如果您修改 MFC 原始程式碼來產生自訂版本的 MFC DLL，請使用不同的名稱 （，最好是一個不是以名稱中的 「 MFC"）。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

