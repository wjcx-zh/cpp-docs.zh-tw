---
title: "做法：在通用 Windows 平台應用程式中使用現有的 C++ 程式碼 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6d022edae8e63a5a6b8ec98ea67fceb4750b173
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>做法：在通用 Windows 平台應用程式中使用現有的 C++ 程式碼
在 UWP 環境中執行傳統型程式的最簡單方式，可能是使用傳統型橋接器技術。 其中包括 Desktop App Converter，這會將現有應用程式封裝為 UWP 應用程式，而不需要變更程式碼。 如需詳細資訊，請參閱 [Bring your desktop app to the Universal Windows Platform (UWP) with the Desktop Bridge](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) (使用傳統型橋接器將您的傳統型應用程式移轉至通用 Windows 平台 (UWP))。

本主題的其餘部分討論如何將 C++ 程式庫 (DLL 和靜態程式庫) 移植到通用 Windows 平台 (UWP)。 您可能想要執行這項作業，讓您的核心 C++ 邏輯可以與多個 UWP 應用程式搭配使用。 
  
 UWP 應用程式會在受保護的環境中執行，因此不允許執行許多可能會危害平台安全性的 Win32、COM 及 CRT API 呼叫。 如果使用 /ZW 選項，編譯器能夠偵測這類呼叫，還能產生錯誤。 您可以在應用程式上使用應用程式認證套件，來偵測呼叫禁止使用之 API 的程式碼。 請參閱[使用 Windows 應用程式認證套件](https://msdn.microsoft.com/library/windows/apps/hh694081.aspx)。  
  
 如果程式庫有可用的原始程式碼，您也許能夠排除禁止的 API 呼叫。 如需包含允許或禁止之 API 清單的詳細資訊，請參閱[適用於 Windows 執行階段應用程式與 Windows 通用平台 (UWP) 應用程式的 Win32 與 COM](https://msdn.microsoft.com/library/windows/apps/br205762.aspx) 和[不支援使用 /ZW 的 CRT 函式](https://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。 一些其他替代方案，請參閱 [Windows 執行階段應用程式和通用 Windows 平台 (UWP) 應用程式中 Windows API 的替代方法](https://msdn.microsoft.com/library/windows/apps/hh464945.aspx)。  
  
 如果您只是嘗試將通用的 Windows 專案的參考加入傳統桌面程式庫，您會收到指出程式庫並不相容的錯誤訊息。 如果是靜態程式庫，您只要像傳統的 Win32 應用程式中一樣，將程式庫 (.lib 檔案) 加入您的連結器輸入，就可以連結程式庫。 其中只有二進位檔可用的程式庫，這是唯一的選項。 靜態程式庫可連結至應用程式可執行檔，但您必須將 UWP 應用程式中使用的 Win32 DLL 納入專案中並標示為內容以封裝為應用程式。 若要在通用 Windows 平台應用程式中載入 Win32 DLL，您還必須呼叫 [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159.aspx)，而不是 LoadLibrary 或 LoadLibraryEx。  
  
 如果您有 DLL 或靜態程式庫的原始程式碼，您可以使用 /ZW 重新編譯為 UWP 專案。 如果您這麼做，可以使用 [方案總管] 加入參考，然後在 C++ UWP 應用程式中使用。 若為 DLL，請您使用匯出程式庫來連結。  
  
 若要向其他語言的呼叫者公開功能，您可以將程式庫轉換成 Windows 執行階段元件。 Windows 執行階段元件不同於一般的 DLL，因為它們以 .winmd 檔案的形式包含的中繼資料，會以 .NET 與 JavaScript 客戶所需的方式描述內容。 若要向其他語言公開 API 項目，您可以加入 C++/CX 建構 (例如 ref 類別) 並設定為公用，或使用 [Windows 執行階段 C++ 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。  在 Windows 10 和更新版本中，您可以使用 [C++/WinRT library](https://github.com/microsoft/cppwinrt) (C++/WinRT 程式庫)，而非 C++/CX。 
  
 前述討論不適用於必須以不同方式處理的 COM 元件。 如果您在 EXE 或 DLL 中有 COM 伺服器，則可以在通用 Windows 專案中使用它，只要將它封裝為[免註冊的 COM 元件](https://msdn.microsoft.com/library/dd408052.aspx)，並當成內容檔案新增至專案，然後使用 [CoCreateInstanceFromApp](https://msdn.microsoft.com/library/windows/apps/hh404137.aspx) 加以具現化即可。 請參閱 [Using Free-COM DLL in Windows Store C++ Project](http://blogs.msdn.com/b/win8devsupport/archive/2013/05/20/using-free-com-dll-in-windows-store-c-project.aspx) (在 Windows 市集 C++ 專案中使用免費 COM DLL)。  
  
 如果您有想要移植到通用 Windows 平台的現有 COM 程式庫，則可以使用 [Windows 執行階段 C++ 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md) 將它轉換成 Windows 執行階段元件。 WRL 不支援所有的 ATL 與 OLE 功能，因此這類移植是否可行，取決於 COM 程式碼有多麼依存於您的元件所需的那些 COM、ATL 及 OLE 功能。  
  
 您有許多不同的方式可以在通用 Windows 平台專案中使用現有 C++ 程式碼。 某些方式不需要在啟用 (也就是使用 /ZW 選項) 元件擴充功能 (C++/CX) 的情況下重新編譯程式碼，但某些則需要，因此如果您需要保留標準 C++ 的程式碼，或為一些程式碼保留傳統的 Win32 編譯環境，就可以這樣做，搭配使用適當的架構選項。 例如，包含通用 Windows 平台 UI 與型別且要向 C#、Visual Basic 及 JavaScript 呼叫端公開的所有程式碼，都應該放在 Windows 應用程式專案與 Windows 執行階段元件專案中。 只需要在 C++ (包括 C++/CX) 程式碼中使用的程式碼，可以放在使用 /WX 選項編譯的專案或標準 C++ 專案中。 將程式碼連結為靜態程式庫，或和應用程式一起封裝為內容，然後只有在它不會使用禁止 API 時才以 DLL 載入，就可以使用僅限二進位的程式碼。  
  
 不論您選擇哪一種開發案例，都應該注意可在程式碼中使用的許多巨集，如此才能根據傳統桌面 Win32 與通用 Windows 平台有條件地編譯程式碼。  
  
```cpp  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
```  
  
 這些陳述式分別適用於 Windows 市集應用程式、Windows Phone 市集應用程式、兩者都適用或兩者均不適用 (僅傳統 Win32 桌面)。 這些巨集只能在 Windows SDK 8.1 和更新版本中使用，因此如果您的程式碼需要使用舊版 Windows SDK 編譯或用於 Windows 以外的其他平台，那麼您也應該考慮無一定義的情況。  
  
 本主題包含下列程序：  
  
1.  [在通用 Windows 平台應用程式中使用 Win32 DLL](#BK_Win32DLL)  
  
2.  [在 UWP 應用程式中使用原生 C++ 靜態程式庫](#BK_StaticLib)  
  
3.  [將 C++ 程式庫移植到 Windows 執行階段元件](#BK_WinRTComponent)  
  
##  <a name="BK_Win32DLL"></a> 在通用 Windows 平台應用程式中使用 Win32 DLL  
 為使安全性和可靠性更佳，通用 Windows 應用程式會在受限制的執行階段環境中執行，因此您不能像在傳統 Windows 桌面應用程式那樣使用任何的原生 DLL。 如果您有 DLL 的原始程式碼，就可以移植程式碼，使其在 UWP 上執行。 首先可變更幾個專案設定和專案檔案中繼資料，將該專案識別為 UWP 專案。 您需要使用 /ZW 選項啟用 C++/CX 來編譯程式庫。 由於與該環境相關聯的控制項更加嚴格，因此 UWP 應用程式中不允許特定 API 呼叫。 請參閱[適用於 Windows 執行階段應用程式和通用 Windows 平台 (UWP) 應用程式的 Win32 和 COM](https://msdn.microsoft.com/library/windows/apps/br205757.aspx)。  
  
 下列程序適用於您具有使用 __declspec (dllexport) 公開函式的原生 DLL 案例。  
  
#### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>移植原生 DLL 到 UWP 而不需建立新專案  
  
1.  如果您有使用 __declspec (dllexport) 匯出函式的原生 DLL，您可以藉由重新編譯 DLL 為 UWP 專案，從 UWP 應用程式中呼叫這些函式。 例如，假設我們有會匯出幾個類別和方法的 DLL，且其具有類似下列標頭檔的程式碼：  
  
    ```  
    // giraffe.h  
    #pragma once  
  
    #ifdef _DLL  
    #define GIRAFFE_API __declspec(dllexport)  
    #else  
    #define GIRAFFE_API   
    #endif  
  
    GIRAFFE_API int giraffeFunction();  
  
    class Giraffe  
    {  
        int id;  
            Giraffe(int id_in);  
        friend class GiraffeFactory;  
  
    public:  
        GIRAFFE_API int GetID();  
    };  
  
    class GiraffeFactory  
    {  
        static int nextID;  
    
    public:  
        GIRAFFE_API GiraffeFactory();  
        GIRAFFE_API static int GetNextID();  
        GIRAFFE_API static Giraffe* Create();  
   };  
    ```  
  
     以及下列程式碼：  
  
    ```  
    // giraffe.cpp  
    #include "stdafx.h"  
    #include "giraffe.h"  
  
    Giraffe::Giraffe(int id_in) : id(id_in)  
    {  
    }  
  
    int Giraffe::GetID()  
    {  
      return id;  
    }  
  
    int GiraffeFactory::nextID = 0;  
  
    GiraffeFactory::GiraffeFactory()  
    {  
        nextID = 0;  
    }  
  
    int GiraffeFactory::GetNextID()  
    {  
        return nextID;  
    }  
  
    Giraffe* GiraffeFactory::Create()  
    {  
        return new Giraffe(nextID++);  
    }  
  
    int giraffeFunction();  
    ```  
  
     此專案 (stdafx.h、dllmain.cpp) 中所有其他項目都屬於標準 Win32 專案範本。 如果您想要跟著做，但進行這些步驟時還不想要使用您自己的 DLL，則請嘗試建立 Win32 專案，在 [專案精靈] 中選取 DLL，然後加入標頭檔 giraffe.h 和程式碼檔案 giraffe.cpp，並將這個步驟中的程式碼內容複製到適當的檔案中。  
  
     定義 _DLL 時 (亦即，將專案建立為 DLL 時)，程式碼定義的巨集 GIRAFFE_API 會解析成 __declspec(dllexport) 。  
  
2.  請開啟此 DLL 專案的 [專案屬性]，並將組態設定為 [所有組態]。  
  
3.  在 [專案屬性] 中，於 [C/C++] 的 [一般] 索引標籤中，將 [使用 Windows 執行階段延伸模組] 設定為 [是 (/ZW)]。 這樣可以啟用元件擴充功能 (C++/CX)。  
  
4.  在方案總管中，選取此專案節點，並開啟捷徑功能表，然後選擇 [卸載專案]。 接著，在卸載的專案節點上開啟捷徑功能表，然後選擇要編輯的專案檔。 找出 WindowsTargetPlatformVersion 項目，並以下列項目取代。  
  
    ```xml  
    <AppContainerApplication>true</AppContainerApplication>  
    <ApplicationType>Windows Store</ApplicationType>  
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>  
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>  
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
    ```  
  
     關閉此 .vcxproj 檔案，並再次開啟捷徑功能表，然後選擇 [重新載入專案]。  
  
     [方案總管] 現在會將此專案識別為通用 Windows 專案。  
  
5.  請確定先行編譯標頭檔的名稱正確。 在 [先行編譯標頭] 區段中，將先行編譯標頭檔從 pch.h 變更為 stdafx.h。 如果您不這麼做，您就會看到下列錯誤。  
  
    ```Output  
    error C2857: '#include' statement specified with the /Ycpch.h command-line option was not found in the source file  
    ```  
  
     問題在於通用 Windows 專案針對先行編譯標頭檔使用不同的命名慣例。  
  
6.  建置專案。 您可能會收到一些有關命令列選項不相容的錯誤。 例如，較常使用的選項 [啟用最少重建 (/Gm)] 在許多 C++ 專案中是預設設定，但和 /ZW 不相容。  
  
     如果您針對通用 Windows 平台編譯，便無法使用某些函式。 您會看到任何相關問題的編譯器錯誤。 請解決這些問題，直到組建沒有錯誤為止。  
  
7.  若要在 UWP 應用程式中以相同的方案使用 DLL，請開啟 UWP 專案節點的捷徑功能表，然後依序選擇 [新增]、[參考]。  
  
     在 [專案]、[方案] 下選取此 DLL 專案旁邊的核取方塊，然後選擇 [確定] 按鈕。  
  
8.  在 UWP 應用程式的 pch.h 檔案中包含程式庫的標頭檔。  
  
    ```  
    #include "..\MyNativeDLL\giraffe.h"  
    ```  
  
9. 如往常般在 UWP 專案中新增程式碼，以叫用函式並從 DLL 中建立型別。  
  
    ```  
    MainPage::MainPage()  
    {  
        InitializeComponent();  
        GiraffeFactory gf;  
        Giraffe* g = gf.Create();  
        int id = g->GetID();  
    }  
  
    ```  
  
##  <a name="BK_StaticLib"></a> 在 UWP 應用程式中使用原生 C++ 靜態程式庫  
 您可以在 UWP 專案中使用原生 C++ 靜態程式庫，但是要注意一些限制。 請先閱讀這個關於使用 C++/CX 之靜態程式庫的[主題](https://msdn.microsoft.com/library/hh771041.aspx)。 您可以從 UWP 應用程式存取靜態程式庫中的原生程式碼，但不是建議您在這類靜態程式庫中建立公用 ref 型別。 如果您以 /ZW 選項編譯靜態程式庫時，會警告管理員 (實際上偽裝為連結器)：  
  
```  
LNK4264: archiving object file compiled with /ZW into a static library; note that when authoring Windows Runtime types it is not recommended to link with a static library that contains Windows Runtime metadata  
```  
  
 不過，您不需要使用 /ZW 重新編譯，就可以在 UWP 中使用靜態程式庫。 您將無法宣告任何 ref 型別，或使用 C++/CX 建構，但如果您只是想要使用機器碼的程式庫，可以依照下列步驟執行。  
  
#### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>若要在 UWP 專案中使用原生 C++ 靜態程式庫  
  
1.  在 UWP 專案的專案屬性中，於 [連結器] 區段的 [輸入] 屬性中，加入程式庫的路徑。 例如，針對專案中會將其輸出放在 <方案資料夾>\Debug\MyNativeLibrary\MyNativeLibrary.lib 的程式庫，新增相對路徑 `Debug\MyNativeLibrary\MyNativeLibrary.lib`。  
  
2.  新增 include 陳述式，以參考 UWP 專案中的 pch.h 標頭檔，然後開始將使用該程式庫的程式碼加入。  
  
    ```  
    #include "..\MyNativeLibrary\giraffe.h"  
    ```  
  
     請不要在方案總管的 [參考] 節點中新增參考。 此機制僅適用於 Windows 執行階段元件。  
  
##  <a name="BK_WinRTComponent"></a> 將 C++ 程式庫移植到 Windows 執行階段元件  
 如果您想要從 UWP 應用程式中使用靜態程式庫中的原生 API，而且有原生程式庫的原始程式碼，您就可以將程式碼移植到 Windows 執行階段元件。 它將不再是靜態程式庫，而是 DLL。 您可以在任何 C++ UWP 應用程式中使用，但與靜態程式庫不同的是，您可以加入 ref 型別與用戶端可在任何 UWP 應用程式程式碼中使用的其他 C++/CX 建構，不論語言為何。 因此，您可以從 C#、Visual Basic 或 JavaScript 存取這些型別。  基本程序是建立 Windows 執行階段元件專案，將靜態程式庫的程式碼複製到其中，然後解決將程式碼從標準的 C++ 編譯移至 /ZW 編譯時引發的任何錯誤。  
  
#### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>若要將 C++ 程式庫移植到 Windows 執行階段元件  
  
1.  建立 Windows 執行階段元件專案。  
  
2.  關閉專案。  
  
3.  在 [Windows 檔案總管] 中，找到該專案。 根據預設，Visual Studio 會使用 [文件] 資料夾中的 [Visual Studio 2017\Projects] 資料夾。 找出當中包含您想要移植之程式碼的 C++ 程式庫專案。 複製 C++ 程式庫專案中的原始程式檔 (標頭檔、程式碼檔案及任何其他資源，包括子目錄在內)，然後貼至專案資料夾中，務必要保留相同的資料夾結構。  
  
4.  重新開啟 Windows 執行階段元件專案，並開啟方案總管中專案節點的捷徑功能表，然後選擇 [新增]、[現有項目]。  
  
5.  從原始專案中選取要新增的所有檔案，然後選擇 [確定]。 必要時，對子資料夾重複上述步驟。  
  
6.  您現在已有重複的節點。 如果您有多個先行編譯標頭檔 (例如 stdafx.h 與 pch.h)，請選擇一個加以保留。 將任何必要的程式碼 (例如 include 陳述式) 複製到您要保留的檔案中。 然後將另一個刪除，並在專案屬性的 [先行編譯標頭檔] 下，確定標頭檔的名稱正確無誤。  
  
     如果您已變更要做為先行編譯標頭使用的檔案，請確定每個檔案的先行編譯標頭檔選項都正確無誤。 依次選擇每個 .cpp 檔案，開啟其屬性視窗，然後確定全部都設定為 [使用 (/Yu)]，當中只有想要的先行編譯標頭檔設定為 [建立 (/Yc)]。  
  
7.  建置專案，並解決任何錯誤。 這些錯誤可能是使用 /ZW 選項造成，或由新版 Windows SDK 造成，或者可能在反映依存性 (例如程式庫所依存的標頭檔)，或新舊專案之間的專案設定差異。  
  
8.  將公用 ref 型別加入您的專案，或將一般型別轉換為 ref 型別，以將進入點公開為您想要從 UWP 應用程式呼叫的功能。  
  
9. 藉由從 UWP 應用程式專案中加入元件的參考來測試該元件，並加入一些程式碼來呼叫您建立的公用 API。  
  
## <a name="see-also"></a>請參閱  
 [移植到通用 Windows 平台](../porting/porting-to-the-universal-windows-platform-cpp.md)