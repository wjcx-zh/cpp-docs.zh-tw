---
title: "TN033：MFC 的 DLL 版本 | Microsoft Docs"
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
  - "vc.mfc.dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFXDLL 程式庫"
  - "MFC 的 DLL 版本 [C++]"
  - "DLL [C++], MFC"
  - "MFC DLL [C++], 撰寫擴充 DLL"
  - "TN033"
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN033：MFC 的 DLL 版本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個會描述如何使用 MFC 應用程式和擴充 DLL 的 MFCxx.DLL 或 MFCxxD.DLL \(其中 x 是 MFC 版本號碼\) 共用的動態連結程式庫。  如需標準 DLL 的詳細資訊，請參閱 [使用為 DLL 中的 MFC](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。  
  
 這個技術提示包括 DLL 的三個方面。  最後兩個字元是提供更多進階使用者:  
  
-   [如何建置 MFC 擴充 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)  
  
-   [如何使用 MFC 的 DLL 版本的 MFC 應用程式](#_mfcnotes_writing_an_application_that_uses_the_dll_version)  
  
-   [MFC 共用的動態連結程式庫 \(DLL\) 的實作方式。](#_mfcnotes_how_the_mfc30.dll_is_implemented)  
  
 如果您是使用 MFC 的 DLL 可以搭配非 MFC 應用程式的建置感興趣 \(稱為標準 DLL\) 的話，請參閱 [Technical Note 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。  
  
## MFCxx.DLL 支援的概觀:詞彙和檔案  
 **Regular DLL**:使用某些 MFC 類別，您可以使用標準 DLL 建置獨立 DLL。  跨 App\/DLL 界限的介面是「C」介面，因此，用戶端應用程式不一定要是 MFC 應用程式。  
  
 這是支援的 MFC DLL 支援 1.0 版。  在 [Technical Note 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) 中說明，以及 MFC 進階概念取樣 [DLLScreenCap](../top/visual-cpp-samples.md)。  
  
> [!NOTE]
>  根據 Visual C\+\+ 4.0 版，這個詞彙 **USRDLL** 已經過時和由該規則的 DLL 取代靜態連結至 MFC。  您也可以建置該規則的 DLL 動態連結至 MFC。  
  
 MFC 3.0 \(以上\) 支援的所有新功能的標準 DLL 包含 OLE 和資料庫類別。  
  
 **AFXDLL**:這也稱為 MFC 程式庫的共用版本。  這是在 MFC 加入新 DLL 支援 2.0。  MFC 程式庫在多個 DLL \(接下來將有說明\)，而用戶端應用程式或 DLL 動態連結至所需的 DLL。  跨 application\/DLL 界限的介面是 C\+\+\/MFC 類別介面。  用戶端應用程式必須是 MFC 應用程式。  這個支援所有 MFC 3.0 功能 \(例外狀況:UNICODE 未針對資料庫類別支援\)。  
  
> [!NOTE]
>  根據 Visual C\+\+ 4.0 版，這類型的 DLL 稱為擴充 DLL」。  
  
 這個標記會使用 MFCxx.DLL 參考整個 MFC DLL 集合，包括:  
  
-   偵錯:MFCxxD.DLL \(合併\) 和 MFCSxxD.LIB \(靜態\)。  
  
-   版本:MFCxx.DLL \(合併\) 和 MFCSxx.LIB \(靜態\)。  
  
-   Unicode 偵錯:MFCxxUD.DLL \(合併\) 和 MFCSxxD.LIB \(靜態\)。  
  
-   Unicode 版本:MFCxxU.DLL \(合併\) 和 MFCSxxU.LIB \(靜態\)。  
  
> [!NOTE]
>  MFCSxx \[U\] \[D\] .LIB 程式庫使用 MFC 共用 DLL 一起使用。  這些程式庫必須與應用程式或 DLL 靜態連結所包含的程式碼。  
  
 對應的匯入程式庫的應用程式連結:  
  
-   偵錯:MFCxxD.LIB  
  
-   版本:MFCxx.LIB  
  
-   Unicode 偵錯:MFCxxUD.LIB  
  
-   Unicode 版本:MFCxxU.LIB  
  
 「MFC 擴充 DLL」是 DLL 建置於 MFCxx.DLL \(和 \(或\) 其他 MFC 共用 DLL\)。  這裡 MFC 元件架構啟動。  如果您從 MFC 類別衍生一個有用的類別或建置另一個像 MFC 的工具箱，您在 DLL 可以放置它。  DLL 使用 MFCxx.DLL，與最後一個用戶端應用程式。  這樣可重複使用的分葉類別、可重複使用的基底類別和可重複使用的檢視\/資料類別。  
  
## 的優缺點  
 為何要使用 MFC 的共用版本?  
  
-   使用這個共用程式庫可以產生較小的應用程式 \(使用最對 MFC 程式庫小於 10K\) 的最小應用程式。  
  
-   MFC 的共用版本支援 MFC 擴充 DLL 的標準 DLL。  
  
-   建立使用 MFC 共用程式庫的應用程式會建立靜態連結至 MFC 應用程式快速，因為連結 MFC 不必要的。  這一點尤其適用於在連結器必須壓縮偵錯資訊 \( **DEBUG** 的組建透過連結已經包含偵錯資訊的 DLL，有較少的偵錯資訊在應用程式內壓縮。  
  
 為何應該不使用 MFC 的共用版本:  
  
-   傳輸使用這個共用程式庫的應用程式需要傳輸有程式的 MFCxx.DLL \(和其他\) 程式庫。  MFCxx.DLL 自由是可轉散發像許多 DLL，不過，您仍然必須安裝安裝程式裡安裝 DLL。  此外，您必須傳輸 MSVCRTxx.DLL，包含 C 執行階段程式庫的程式和 MFC DLL 使用。  
  
##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> 如何撰寫 MFC 擴充 DLL  
 MFC 擴充 DLL 是包含類別和函式的 DLL 寫入裝飾 MFC 類別的功能。  MFC 擴充 DLL 來使用共用的 MFC DLL 應用程式使用它，有一些額外的考量:  
  
-   建置程序與建立使用有一些共用 MFC 程式庫其他編譯器和連結器選項的應用程式。  
  
-   MFC 擴充 DLL 沒有 `CWinApp`衍生類別。  
  
-   MFC 擴充 DLL 必須提供特殊的 `DllMain`。  AppWizard 提供您可以修改的 `DllMain` 函式。  
  
-   如果擴充 DLL 的匯出 `CRuntimeClass`、或應用程式資源， MFC 擴充 DLL 通常會提供一個初始化程序建立 **CDynLinkLibrary** 。  **CDynLinkLibrary** 衍生類別，則必須由擴充 DLL，維護每個應用程式資料可能使用。  
  
 這些考量如下的詳細說明。  因為它所說明，您也應該提到 MFC 進階概念 [DLLHUSK](../top/visual-cpp-samples.md) 範例:  
  
-   建立使用共用程式庫的應用程式。\(DLLHUSK.EXE 是動態連結至 MFC 程式庫以及其他 DLL 之 MFC 應用程式  
  
-   建置 MFC 擴充 DLL。\(請注意用於建置擴充 DLL\) 的特殊旗標 \(例如 `_AFXEXT` \)  
  
-   MFC 擴充 DLL 的兩個範例。  顯示一個 MFC 擴充 DLL 的基礎結構以限制匯出 \(TESTDLL1\) 和其他的匯出整個類別介面 \(TESTDLL2\) 的示範。  
  
 用戶端應用程式和任何擴充 DLL 必須使用 MFCxx.DLL 相同版本。  您應該遵循 MFC DLL 的慣例和提供偵錯和您的擴充 DLL 零售 \(\/release\) 版本。  這可讓用戶端程式建置兩個具有適當偵錯及其應用程式零售版本並連結至其偵錯或 DLL 零售版本。  
  
> [!NOTE]
>  由於 C\+\+ 函式名稱改變 \(Name Mangling\) 和匯出問題，從擴充 DLL 的匯出清單可能會不同於不同平台的同一個 DLL 的偵錯和零售版本和 DLL 之間。  零售 MFCxx.DLL 有大約 2000 個匯出的進入點;偵錯 MFCxxD.DLL 有 3000 輸出進入點。  
  
### 如需記憶體管理的快速提示  
 在這個技術提示周圍結尾標題為「記憶體管理， \> 一節，說明 MFCxx.DLL 的實作與 MFC 共用版本的。  您必須知道實作擴充 DLL 的資訊會描述此處。  
  
 MFCxx.DLL 和任何擴充 DLL 載入至用戶端應用程式的位址空間將使用相同的記憶體配置器、資源載入和其他 MFC 「全域狀態，就如同在相同的應用程式。  這是必要的，因為靜態連結至 MFC 的非 MFC DLL 程式庫和標準 DLL 會確實在相反且具有配置在它的記憶體集區外面的每一個 DLL。  
  
 如果擴充 DLL 配置記憶體，則該記憶體可以自由混合其他應用程式配置物件。  此外，如果使用，則共用 MFC 程式庫的應用程式損毀，作業系統的保護會維護其他 MFC 應用程式的共用 DLL 完整性。  
  
 相同的其他」全域 MFC 狀態，例如載入資源的目前可執行檔從，也會在用戶端應用程式和所有 MFC 擴充 DLL 以及 MFCxx.DLL 之間。  
  
### 建置擴充 DLL  
 您可以使用 AppWizard 建立 MFC 擴充 DLL 專案，因此，它會自動產生適當的編譯器和連結器設定。  它也會產生您可以修改的 `DllMain` 函式。  
  
 如果您將現有的專案加入至 MFC 擴充 DLL，使用 MFC 的共用版本，請啟動以建立的應用程式的標準規則，則執行下列動作:  
  
-   對編譯器旗標的加 **\/D\_AFXEXT** 。  在專案屬性對話方塊中，選取 C\/C\+\+ 節點。  然後選取前置處理器分類。  將 `_AFXEXT` 加入至定義巨集欄位，而每個以分號分隔的項目。  
  
-   移除 **\/Gy** 編譯器參數。  在專案屬性對話方塊中，選取 C\/C\+\+ 節點。  然後選取程式碼產生類別。  確定「啟用函式階層連結選項未啟用。  因為連結器不會移除未參考的函式，這可讓您輕鬆地匯出類別。  如果原始專案可用來建立靜態連結至 MFC 的標準 DLL，請變更 **\/MT\[d\]** 編譯器選項到 **\/MD\[d\]**。  
  
-   建構匯出程式庫以 **\/DLL** 選項連接。  這會設定，當您建立新的目標，指定 Win32 動態連結程式庫為目標型別。  
  
### 變更您的標頭檔  
 擴充 DLL 的目標通常是匯出一些通用功能對可使用該功能的一或多個應用程式。  這是因為用來匯出為您的用戶端應用程式可以使用類別和全域函式。  
  
 要這樣做必須確保每 10% 成員函式標記為匯入或匯出屬性。  這需要特殊的宣告: **\_\_declspec\(dllexport\)** 和 **\_\_declspec\(dllimport\)**。  當用戶端應用程式時使用您的類別中，您要將其宣告為 **\_\_declspec\(dllimport\)**。  當擴充 DLL 在建置時，應該宣告為 **\_\_declspec\(dllexport\)**。  此外，必須實際匯出函式，因此，用戶端程式繫結至它們在載入時間。  
  
 若要匯出針對整個類別，請使用 **AFX\_EXT\_CLASS** 在類別定義。  這個巨集是由架構所定義的成員，當 **\_\_declspec\(dllexport\)** 和 **\_AFXDLL**`_AFXEXT` 後，不過，定義為 **\_\_declspec\(dllimport\)** ，當 `_AFXEXT` 沒有定義時。  在建置擴充 DLL 時，`_AFXEXT` 如上所述，只定義。  例如：  
  
```  
class AFX_EXT_CLASS CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
### 不要匯出整個類別  
 有時您可能想要匯出您的類別的必要成員。  例如，如果您正在匯出 `CDialog` 衍生類別，您可能只需要匯出建構函式和 `DoModal` 呼叫。  您可以匯出使用 DLL 的 .DEF 檔案中的這些成員，不過，您可以在相同情況使用 **AFX\_EXT\_CLASS** 在您需要匯出的個別成員。  
  
 例如：  
  
```  
class CExampleDialog : public CDialog  
{  
public:  
   AFX_EXT_CLASS CExampleDialog();  
   AFX_EXT_CLASS int DoModal();  
   // rest of class definition  
   .  
   .  
   .  
};  
```  
  
 這樣做時，可能會發生了問題，因為您不再匯出類別的所有成員。  這個問題就像 MFC 巨集運作的。  有幾個 MFC 的 Helper 巨集實際上會宣告或定義資料成員。  因此，這些資料成員也必須從您的 DLL 匯出。  
  
 例如，建置擴充 DLL 時，`DECLARE_DYNAMIC` 巨集會定義如下：  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
   public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
 啟動靜態 `AFX_DATA`」的行宣告在類別內的靜態物件。  若要正確匯出這個類別和從用戶端 .EXE 存取執行階段資訊，您必須匯出這個靜態物件。  因為靜態物件已經用修飾詞 `AFX_DATA` 宣告，所以您在建置 DLL 時只需要將 `AFX_DATA` 定義成 **\_\_declspec\(dllexport\)**，而在建立用戶端可執行檔時定義為 **\_\_declspec\(dllimport\)**。  
  
 如先前所述， **AFX\_EXT\_CLASS** 這類已經定義。  您必須重新解譯 `AFX_DATA` 與 **AFX\_EXT\_CLASS** 類別中定義的。  
  
 例如：  
  
```  
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
  
 MFC 一定會使用其巨集內定義資料項目的 `AFX_DATA` 符號，因此，這項技術用於所有這類案例中運作。  例如，它會為 `DECLARE_MESSAGE_MAP`中運作。  
  
> [!NOTE]
>  如果您是匯出整個類別而不是類別中選取的成員，則靜態資料成員會自動匯出。  
  
 您可以使用相同的技巧自動匯出使用 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 巨集之類別的 `CArchive` 擷取運算子。  透過托類別宣告匯出封存運算子 \(位於。H 檔案\) 包含下列程式碼中:  
  
```  
#undef AFX_API  
#define AFX_API AFX_EXT_CLASS  
  
<your class declarations here>  
  
#undef AFX_API  
#define AFX_API  
```  
  
### \_AFXEXT 的限制  
 只要您沒有擴充 DLL，多個圖層可以為您的擴充 DLL 使用 \_**AFXEXT** 前置處理器符號。  如果您的擴充 DLL 呼叫或衍生自您自己之擴充 DLL 裡的類別，接著又衍生自 MFC 類別，您必須使用自己的前置處理器符號來避免模稜兩可 \(Ambiguity\) 的情形。  
  
 問題是因為您必須在 Win32 中將任何從 DLL 匯出的資料明確地宣告為 **\_\_declspec\(dllexport\)**，而在從 DLL 匯入則宣告為 **\_\_declspec\(dllimport\)**。  當您定義 `_AFXEXT` 時，MFC 標頭檔會確定 **AFX\_EXT\_CLASS** 已正確地定義。  
  
 當您有多個圖層時，符號 \( **AFX\_EXT\_CLASS** 不足，，因為擴充 DLL 可能匯出新類別以及從另一個擴充 DLL 的其他類別。  為了處理這個問題，請使用特殊的前置處理器符號表示您建置 DLL 對使用 DLL。  例如，請想像兩個擴充 DLL、A.DLL 和 B.DLL。  它們各自在匯出 A.H 和 B.H 的一些類別，分別。  B.DLL 使用 A.DLL 的類別。  標頭檔會看起來會類似下列所示：  
  
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
  
 當 A.DLL 建置時，會用 **\/D A\_IMPL** 建置，而且，當 B.DLL 建置時，會用 **\/D B\_IMPL**建置。  每一個 DLL 使用不同的符號， CExampleB 匯出，並 CExampleA 匯出，而建置 B.DLL 時。  CExampleA 匯出，在建置 A.DLL 而且匯出，而使用由 B.DLL \(或其他的一些用戶端\)。  
  
 當使用固定 **AFX\_EXT\_CLASS** 和 `_AFXEXT` 前置處理器符號時，此種圖層無法完成。  表示建立其 OLE、資料庫和網路範圍 DLL 時，所描述的技巧上面有些解決問題不同於機制 MFC 用途。  
  
### 不要匯出整個類別  
 同樣地，，所以匯出整個類別，您必須採取特殊處理。  您必須確定 MFC 巨集建立必要的資料項目正確匯出。  您可以重新定義至特定類別之巨集的 **AFX\_DATA** 完成。  這個工作應該在每次您沒有匯出整個類別時執行。  
  
 例如：  
  
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
   //class definition   
   .  
   .  
   .  
};  
  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### DllMain  
 以下是您在您的擴充 DLL 的主要原始程式檔應放置的正確程式碼。  在標準包括後，它應該是。  請注意，當您使用 AppWizard 建立擴充 DLL 的起始檔案 \(Starter File\)，它會提供您的 `DllMain` 。  
  
```  
#include "afxdllx.h"  
  
static AFX_EXTENSION_MODULE extensionDLL;  
  
extern "C" int APIENTRY   
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)  
{  
   if (dwReason == DLL_PROCESS_ATTACH)  
   {  
      // Extension DLL one-time initialization   
      if (!AfxInitExtensionModule(  
             extensionDLL, hInstance))  
         return 0;  
  
      // TODO: perform other initialization tasks here  
   }  
   else if (dwReason == DLL_PROCESS_DETACH)  
   {  
      // Extension DLL per-process termination  
      AfxTermExtensionModule(extensionDLL);  
  
          // TODO: perform other cleanup tasks here  
   }  
   return 1;   // ok  
}  
```  
  
 對 `AfxInitExtensionModule` 的呼叫擷取模組執行階段類別 \(`CRuntimeClass` 結構\) 以及它的 Object Factory \(`COleObjectFactory` 物件\) 之後使用，當 **CDynLinkLibrary** 物件建立時。  對 `AfxTermExtensionModule` 的 \(選擇性\) 呼叫提供 MFC 對清除擴充 DLL 時，每個處理序從擴充 DLL 中斷連結 \(發生，當處理序結束時，或者，當卸載 DLL 由於 **FreeLibrary** 呼叫時\)。  因為大部分擴充 DLL 沒有動態載入 \(通常，會透過其匯入程式庫連結\)，對 `AfxTermExtensionModule` 的呼叫通常不是必要的。  
  
 如果您的應用程式以動態方式載入並釋放擴充 DLL，請確定呼叫 `AfxTermExtensionModule` 如上所述。  因此請務必使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` \(而不是 Win32 函式 **LoadLibrary** 和 **FreeLibrary**\)，如果您的應用程式使用多執行緒，或者動態載入擴充 DLL。  使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 是否已執行的啟動和關閉程式碼，在擴充 DLL 載入和卸載時不會損毀全域 MFC 狀態。  
  
 標頭檔 AFXDLLX.H 包含在擴充功能之結構的特殊定義 DLL，例如這個定義用於 `AFX_EXTENSION_MODULE` 和 **CDynLinkLibrary**。  
  
 必須宣告全域 *extensionDLL* 如下所示。  此時，不同於 MFC 16 位元版本中，您可以配置記憶體和呼叫 MFC 函式，，因為 MFCxx.DLL 完全初始化，以便在呼叫 `DllMain` 時。  
  
### 共用資源和類別  
 只有簡單的 MFC 擴充 DLL 必須匯出至用戶端應用程式與 Nothing 的一些低頻寬函式等等。  更多使用者介面密集的 DLL 可能想要匯出資源和 C\+\+ 類別加入至用戶端應用程式。  
  
 匯出資源是經由資源清單來完成。  在每個應用程式的唯一方式是 **CDynLinkLibrary** 物件的連結串列。  在尋找資源時，載入資源的大部分標準 MFC 實作先仔細留意目前資源模組 \(`AfxGetResourceHandle`\)，而且，如果找不到查核行程 **CDynLinkLibrary** 清單物件嘗試載入要求的資源。  
  
 C\+\+ 物件的動態建立給定的 C \+\+. 類別名稱是類似的。  MFC 物件還原序列化機制需要註冊的所有 `CRuntimeClass` 物件，以便將動態建立以儲存了什麼的所需型別的 C\+\+ 物件重建前。  
  
 如果您在擴充 DLL 的用戶端應用程式使用的是 `DECLARE_SERIAL`類別，則您必須匯出您的類別為可見的用戶端應用程式。  這個由查核來完成 **CDynLinkLibrary** 清單。  
  
 在 MFC 進階概念的情況下請取樣 [DLLHUSK](../top/visual-cpp-samples.md)，清單看起來會像這樣:  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
               |                      |  
          TESTDLL2.DLL           TESTDLL2.DLL  
               |                      |  
          TESTDLL1.DLL           TESTDLL1.DLL  
               |                      |  
               |                      |  
            MFC90D.DLL            MFC90.DLL  
```  
  
 MFCxx.DLL 通常最後在資源和類別清單。  MFCxx.DLL 包括所有標準 MFC 資源，包括所有標準命令 ID 的提示字串。  將它放置在清單的尾端讓 DLL 和用戶端應用程式沒有標準 MFC 資源的自己的複本，，而是依賴 MFCxx.DLL 的共用資源。  
  
 合併所有 DLL 資源和類別名稱加入至用戶端應用程式的命名空間中有缺點則必須小心哪些 ID 或名稱您選取。  當然您也可以不匯出您的資源或一 **CDynLinkLibrary** 物件停用這項功能對用戶端應用程式。  [DLLHUSK](../top/visual-cpp-samples.md) 範例會使用多個標頭檔來管理共用資源命名空間。  為使用共用資源檔的詳細技巧參閱 [Technical Note 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) 。  
  
### 初始化 DLL  
 如先前所述，您通常要建立 **CDynLinkLibrary** 物件以便匯出您的資源和類別為用戶端應用程式。  您將需要提供輸出進入點初始化 DLL。  至少，這是任何不使用引數並傳回空白的常式，不過，它可以是您想要的任何。  
  
 若要使用您的 DLL 的每一個用戶端應用程式必須呼叫這個初始化程序，因此，如果您使用這種方法。  您也可以指派至 `DllMain` 的這個 **CDynLinkLibrary** 物件在呼叫 `AfxInitExtensionModule`之後。  
  
 初始化程序必須在目前應用程式記憶體段落的 **CDynLinkLibrary** 物件，連接由您的擴充 DLL 資訊決定。  這可以與下列項目:  
  
```  
extern "C" extern void WINAPI InitXxxDLL()  
{  
   new CDynLinkLibrary(extensionDLL);  
}  
```  
  
 定期名稱，在此範例中的 *InitXxxDLL* ，可以是您想要的任何。  它不需要是，則為 `extern "C"`，但是這樣做可讓輸出清單更容易維護。  
  
> [!NOTE]
>  如果您使用您的標準 DLL 的擴充 DLL，您必須匯出這個初始化函式。  必須在使用任何擴充 DLL 類別或資源前的標準 DLL 呼叫此函式。  
  
### 匯出項目  
 最簡單的方式匯出您的類別會使用 **\_\_declspec\(dllimport\)** 和 **\_\_declspec\(dllexport\)** 要匯出的每個類別和全域函式。  這項命名每個進入點使它很容易，不過，效率的 \(接下來將有說明\)，讓您更能控制哪些匯出的函式，而且您無法依序數匯出函式。  TESTDLL1 和 TESTDLL2 使用這個方法會匯出其項目。  
  
 有效的方法 \(和 MFCxx.DLL 的方法\) 會以手動方式匯出每個項目都是藉由命名每個項目在 .DEF 檔。  因為我們匯出我們的 DLL \(即不是項目\) 的選擇性的匯出，我們必須決定特定介面希望匯出。  因為您必須指定 mangled 名稱給連結器以輸入的形式在 .DEF 檔，這是相當困難。  除非您真的需要有其，符號連結不會匯出任何 C\+\+ 類別。  
  
 如果您嘗試匯出 C\+\+ 與 .DEF 的類別檔案之前，您可能想要開發工具自動產生這個清單。  使用兩個階段連結程序，這個交易。  一次連接您的 DLL 沒有匯出，並可以讓連結器產生 .MAP 檔案。  .MAP 檔案可用來產生應匯出函式的清單，因此，只需要重新整理，它可以用來產生您的 .DEF 檔的匯出項目。  MFCxx.DLL 和 OLE 的輸出清單和資料庫擴充 DLL，千位在數目，產生了與此處理序 \(雖然它並不完全自動並不需要隨時調整陣列的傳遞\)。  
  
### CWinApp 至 CDynLinkLibrary  
 MFC 擴充 DLL 沒有 `CWinApp`\-它的衍生物件;它必須與 `CWinApp`\-用戶端應用程式的衍生物件一起使用。  這表示用戶端應用程式有自己的主要訊息幫浦，閒置迴圈等等。  
  
 如果您的 MFC 擴充 DLL 必須維護額外資料為每個應用程式，您可以從 **CDynLinkLibrary** 衍生新類別，並建置在 InitXxxDLL 常式說明得最上方。  該 DLL 會在執行時檢查 **CDynLinkLibrary** 物件目前的應用程式清單，找出特殊擴充 DLL 的物件。  
  
### 使用在 DLL 中實作的資源  
 如先前所述，預設資源載入會引導尋找具有所要求資源的第一個 EXE 或 DLL 的 **CDynLinkLibrary** 物件清單。  所有的 MFC 應用程式以及所有內部程式碼使用 `AfxFindResourceHandle` 中找出任何資源的資源清單，，不論它可能位於。  
  
 如果您想要從特定層級只載入資源，請使用 API `AfxGetResourceHandle` 和 `AfxSetResourceHandle` 儲存舊的控制代碼和設定新控制代碼。  請確定在傳回用戶端應用程式之前要還原舊的資源控制代碼。  這個範例 TESTDLL2 為明確載入功能表使用這種方法。  
  
 瀏覽清單時會出現速度略微緩慢和需要管理資源 ID 範圍等缺點。  優點是連結至數個擴充 DLL 的用戶端應用程式可以使用任何 DLL 提供的資源，而不需要指定 DLL 執行個體控制代碼 \(Instance Handle\)。  `AfxFindResourceHandle` 是 API，用來逐一查看資源清單以尋找指定的符合項目。  這個 API 會使用到資源的名稱、類型，並傳回第一次發現時 \(或 NULL\) 的資源控制代碼。  
  
##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> 撰寫使用 DLL 版本的應用程式  
  
### 應用程式需求。  
 使用 MFC 的共用版本的應用程式必須遵守一些簡單規則:  
  
-   它必須是 `CWinApp` 物件，並遵循這個標準訊息的規則的範例。  
  
-   必須編譯它與一組必要的編譯器旗標 \(參看下方\)。  
  
-   它必須與 MFCxx 匯入程式庫連結。  藉由設定必要的編譯器旗標， MFC 標頭檔會決定在程式庫應用程式應該要連結的連結時間。  
  
-   若要執行可執行檔， MFCxx.DLL 必須在路徑或在 Windows 系統目錄。  
  
### 與開發環境中建置  
 如果您使用與大部分的內部 Makefile 標準預設值，您可以輕鬆地變更專案建立 DLL 版本。  
  
 下列步驟假設您有 NAFXCWD.LIB 連接的正確運作的 MFC 應用程式 \(偵錯\)，並 NAFXCW.LIB \(為 Retail\) 和您要將它轉換為使用 MFC 程式庫的共用版本。  執行 Visual C\+\+ 環境並具有內部專案檔。  
  
1.  在 **Projects** 功能表上，按一下 \[**屬性**\]。  在 **Project Defaults**下的 **General** 頁面，設定 Microsoft Foundation Classes 對 **Use MFC in a Shared DLL** \(MFCxx \(d\) .dll\)。  
  
### 使用 NMAKE 建置。  
 如果您使用 Visual C\+\+ 的外部 Makefile 功能或直接使用 NMAKE，您必須編輯 Makefile 支援編譯器和連結器選項  
  
 必要的編譯器旗標:  
  
 **\/D\_AFXDLL \/MD**  
 **\/D\_AFXDLL**  
  
 標準 MFC 標頭需要這個符號定義:  
  
 **\/MD**  
 應用程式必須使用 C 執行階段程式庫的 DLL 版本。  
  
 其他編譯器旗標遵循 MFC 預設 \(例如 \_DEBUG，為偵錯\)。  
  
 編輯程式庫連結器清單。  變更 NAFXCWD.LIB 到 MFCxxD.LIB 並變更 NAFXCW.LIB 到 MFCxx.LIB。  用 MSVCRT.LIB 取代 LIBC.LIB。  與其他 MFC 程式庫是重要的 MFCxxD.LIB 是定位 **before** 任何 C 執行階段程式庫。  
  
 選擇性地將 **\/D\_AFXDLL** 加入零售和偵錯資源編譯器選項 \(實際編譯 **\/R**的資源\) 的值。  這是透過共用存在於 MFC DLL 的資源將最後一個可執行檔更小。  
  
 完整重建，在這些變更後，需要。  
  
### 建置範例  
 大部分 MFC 範例程式可以建立從 Visual C\+\+ 或從命令列的共用 NMAKE 相容 MAKEFILE。  
  
 若要將這些範例中的任一個使用 MFCxx.DLL，可以載入 .MAK 檔簽入 Visual C\+\+ 和上述設定專案選項。  如果您使用 NMAKE 建置，您在 NMAKE 命令列上指定「AFXDLL\=1」使用共用 MFC 程式庫，因此，這會建置此範例。  
  
 MFC 進階概念範例 [DLLHUSK](../top/visual-cpp-samples.md) 的 MFC DLL 版本所建置。  這個範例同時說明如何建立與 MFCxx.DLL 連接的應用程式，不過，它也會說明 MFC DLL 封裝選項的其他功能 \(例如 MFC 擴充此技術提示稍後說明的 DLL。  
  
### 封裝注意事項。  
 DLL \(MFCxx \[U\] .DLL\) 的零售版本可以自由重新散佈。  在應用程式的開發過程中， DLL 的偵錯版本不可以自由重新散佈，應該只使用。  
  
 偵錯 DLL 提供的偵錯資訊。  使用 Visual C\+\+ 偵錯工具，您可以追蹤您的應用程式和 DLL 的執行。  版本 DLL \(MFCxx \[U\] .dll\) 不包含偵錯資訊。  
  
 如果您自訂或重建 DLL，則您應該呼叫它們不屬於「MFCxx」以外的 MFC SRC 檔案 MFCDLL.MAK 描述建置選項並包含指定的 DLL 重新命名邏輯。  因為這些 DLL 可能由許多 MFC 應用程式，共用重新命名檔案是必要的。  使用共用 MFC DLL，您的 MFC DLL 的自訂版本取代在系統上安裝的那些可以中斷其他 MFC 應用程式。  
  
 MFC DLL 不建議重建。  
  
##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> MFCxx.DLL 實作方式。  
 下列章節說明 MFC DLL \(MFCxx.DLL 或 MFCxxD.DLL\) 方式實作。  了解在這裡詳細資料也不是，如果您要做的是用於應用程式的 MFC DLL。  在這裡詳細了解如何不重要的 MFC 擴充 DLL，不過，了解這個實作可協助您撰寫自己的 DLL。  
  
### 實作一般。  
 MFC DLL 如上所述實際上是 MFC 擴充 DLL 的特殊案例。  它有大量的類別只能有一個非常大量的匯出。  具有我們在 MFC DLL 來進行規則擴充 DLL 更特殊的陣列的其他動作。  
  
### Win32 執行大部分工作  
 MFC 16 位元版本需要一些特殊技巧包括在某一 80x86 組件程式碼建立的堆疊區段、特殊區段，每個處理序例外狀況內容和其他技術在每個應用程式資料。  Win32 直接支援 DLL 的處理序專屬資料，就是您想要在大部分的情況。  在大部分的情況下 MFCxx.DLL 在 DLL 包裝的 NAFXCW.LIB。  如果您看到 MFC 原始程式碼，您會發現極少 \#ifdef \_AFXDLL，，因為有非常需要以較少的特殊案例。  在其中的特殊情況特別涉及在 Windows 3.1 的 Win32 \(也稱為 Win32\)。  Win32 不直接支援每個處理序 DLL 資料，因此 MFC DLL 必須使用執行緒區域儲存區 \(Thread Local Storage \(TLS\) Win32 API 衍生管理本機資料。  
  
### 對程式庫來源，其他檔案的影響  
 **\_AFXDLL** 版本的影響一般 MFC 類別庫來源和標題是較小。  具有較高的版本檔案 \(AFXV\_DLL.H\) 以及其他標頭檔 \(AFXDLL\_.H\) 包含由主要 AFXWIN.H 標頭。  AFXDLL\_.H 標頭包含類別 **CDynLinkLibrary** 和 **\_AFXDLL** 應用程式和 MFC 擴充 DLL 其他實作詳細資料。  AFXDLLX.H 標題為建立 MFC 擴充 DLL 提供 \(請參閱上述的詳細資料\)。  
  
 對 MFC 程式庫的規則來源 MFC 的 SRC 有一些額外的條件式程式碼在 **\_AFXDLL** \#ifdef 下。  另一個原始程式檔 \(DLLINIT.CPP\) 包含其他 DLL 初始化程式碼和其他黏附 MFC 共用版本的。  
  
 若要建立 MFC 的共用版本，提供額外的檔案。\(請參閱下面如需的詳細資料建置 DLL\)。  
  
-   兩個 .DEF 檔為匯出 MFC DLL 進入點用於偵錯 \(MFCxxD.DEF\) 並釋放 \(MFCxx.DEF\) DLL 的版本。  
  
-   .RC 檔 \(MFCDLL.RC\) 包含所有標準 MFC 資源與 VERSIONINFO 資源 DLL 的。  
  
-   使用 ClassWizard，提供 .CLW 檔案 \(MFCDLL.CLW\) 允許瀏覽 MFC 類別。  注意:這項功能對 MFC DLL 版本不是特定的。  
  
### 記憶體管理  
 使用 MFCxx.DLL 的應用程式使用 MSVCRTxx.DLL 提供的公用記憶體配置器，共用的 C 執行階段 DLL。  應用程式中，所有擴充 DLL 和確定為 MFC DLL 使用這個共用記憶體配置器。  使用記憶體配置的共用 DLL， MFC DLL 可以配置由應用程式之後釋放反之亦然的記憶體。  由於應用程式和 DLL 必須使用相同的配置器，您不應該覆寫 C\+\+ 全域 `operator new` 或 `operator delete`。  同樣的規則也適用於 C 執行階段記憶體配置常式的其餘部分 \(例如 `malloc`、 `realloc`， **free**和其他\)。  
  
### 序數和類別 declspec\(dllexport\) 和 DLL 命名  
 不使用 C\+\+ 編譯器的 `class` **\_\_declspec\(dllexport\)** 功能。  相反地，匯出清單包含類別庫來源 \(MFCxx.DEF 和 MFCxxD.DEF\)。  只有這些選取一組進入點 \(函式和資料\) 是輸出。  其他符號，例如 MFC 私用實作函式或類別，在常駐或非根據名稱表格中沒有匯出所有匯出序數完成沒有字串名稱。  
  
 使用 `class` **\_\_declspec\(dllexport\)** 可能是建置的較小的 DLL 的一個可行的選取，在像 MFC DLL，大的情況下，但是，匯出機制的預設具有效率和大小限制。  
  
 這個的哪些所有方法是我們可以包裝在僅大約 800 KB，而不會危及執行或載入速度的版本 MFCxx.DLL 的許多功能。  MFCxx.DLL 將較大 100K 這個技術未使用。  這也可以讓您將其他進入點在 .DEF 關閉檔案時允許簡單版本，而不會危及速度和大小效率匯出序數。  主要版本修改在 MFC 類別庫中將程式庫名稱。  也就是說 MFC30.DLL 是包含 MFC 3.0 版類別庫的可轉散發 DLL。  升級這個 DLL 在假設 MFC 3.1， DLL 名為 MFC31.DLL。  同樣地，因此，如果您修改 MFC 原始程式碼會產生 MFC DLL 的自訂版本，請使用不同的名稱 \(和最好是一個沒有「MFC」在名稱\)。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)