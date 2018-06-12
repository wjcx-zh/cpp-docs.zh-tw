---
title: 在 Visual C++ 專案中新增參考 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.References
dev_langs:
- C++
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda420768b1ff0819ba666f71d62bfffa86e2105
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336104"
---
# <a name="adding-references-in-visual-c-projects"></a>在 Visual C++ 專案中加入參考
程式通常會在 DLL、Windows 執行階段元件、擴充功能 SDK、COM 元件和 .NET 組件等其他二進位檔中，呼叫應用程式開發介面。 您的程式尋找這些二進位檔的方式，取決於您專案的類型和二進位檔類型。  
  
 在原生 C++ 專案中，如果您想要使用不是由方案中的另一個專案所產生的原生 DLL 或 COM 元件，您可以使用 LoadLibrary 或 CoCreateInstance 來指定該二進位檔的路徑，或是讓系統在妥善定義的特定位置中查詢並找出該路徑。  
  
 在 UWP 專案或 C++/CLI 專案等其他專案類型中，或是當二進位檔是由方案中的另一個專案所產生時，您可以在組件、元件或專案中加入 *「參考」* (Reference)。   參考基本上是可讓您的程式找到二進位檔並與其通訊的一組資料。       當您加入參考時，Visual Studio 會處理低階詳細資料 若要將來自 C++ 專案的參考設定為 .NET Framework 組件 (僅限 C++/CLI)、COM 元件、方案中的其他專案 (包括共用專案) 或連線服務，請以滑鼠右鍵按一下 [方案總管] 中的 [參考] 節點，以顯示 [參考管理員]。 您在 [參考管理員] 中看到的內容會視專案類型而有所不同。  
  
 在原生 C++ 專案 (ATL) 中， *「參考」* (Reference) 的概念僅適用於方案中的其他專案 (包括共用專案)，因此您只會在 [參考管理員] 中看到這些專案：  
  
 ![Visual C&#43;&#43; 參考管理員 &#40;ATL 專案&#41;](../ide/media/visual-c---reference-manager--atl-projects-.png "Visual C++ 參考管理員 (ATL 專案)")  
  
 在 C++/CLI 或通用 Windows 平台專案中，參考的概念除了適用於方案中的其他專案之外，還適用於更多類型的二進位檔。  這些類型全部都會在 [參考管理員] 中公開。
  
## <a name="reference-properties"></a>參考屬性  
 每種參考類型都包含屬性。 您可以在方案總管中選取參考，然後按 **Alt + Enter**，或按一下滑鼠右鍵並選擇 [屬性] ，來檢視屬性。 部分屬性是唯讀的，而部分屬性則可以修改。 不過，您通常不需要手動修改這些屬性。  
  
### <a name="activex-reference-properties"></a>ActiveX 參考屬性  
 ActiveX 參考屬性僅適用於 COM 元件的參考。 這些屬性僅在 [參考]  窗格中選取 COM 元件時才會顯示。 屬性不能修改。  
  
 **控制項完整路徑**  
 顯示參考控制項的目錄路徑。  
  
 **控制項 GUID**  
 顯示 ActiveX 控制項的 GUID。  
  
 **控制項版本**  
 顯示參考 ActiveX 控制項的版本。  
  
 **類型程式庫名稱**  
 顯示參考類型程式庫的名稱。  
  
 **包裝函式工具**  
 顯示用來從參考 COM 程式庫或 ActiveX 控制項建置 Interop 組件的工具。  
  
### <a name="assembly-reference-properties"></a>組件參考屬性  
 組件參考屬性僅適用於 C++/CLI 專案中 .NET Framework 組件的參考。 這些屬性僅在 [參考] 窗格中選取 .NET Framework 組件時才會顯示。 屬性不能修改。  
  
 **相對路徑**  
 顯示從專案目錄到參考組件的相對路徑。  
  
### <a name="build-properties"></a>組建屬性  
 各種參考類型都會提供下列屬性。 這些屬性可讓您指定如何使用參考進行建置。  
  
 **複製到本機**  
 指定是否要在建置期間，自動將參考組件複製到目標位置。  
  
 **複製附屬組件到本機**  
 指定是否要在建置期間，自動將參考組件的附屬組件複製到目標位置。 僅在 [複製到本機]  為 `true`時才會使用。  
  
 **參考組件輸出**  
 指定這個組件用於建置流程。 如果為 `true`，則組件會在建置期間用於編譯器命令列上。  
  
### <a name="project-to-project-reference-properties"></a>專案對專案參考屬性  
 下列屬性會將 [參考]  窗格中所選取專案的 **「專案對專案參考」** (Project-to-Project Reference) 定義至相同方案的另一個專案。 如需詳細資訊，請參閱[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。  
  
 **連結程式庫相依性**  
 當這個屬性為 **True**時，專案系統會將獨立專案所產生的 .lib 檔案連結至相依專案。 一般而言，您將指定為 **True**。  
  
 **專案識別項**  
 用來唯一識別獨立專案。 屬性值是無法修改的內部系統 GUID。  
  
 **使用程式庫相依性輸入**  
 當這個屬性為 **False**時，專案系統不會將獨立專案所產生的程式庫 .obj 檔案連結至相依專案。 因此，這個值會停用累加連結。 一般而言，您將指定為 **False** ，因為若有許多的獨立專案，建置應用程式可能會花很長的時間。  
  
### <a name="reference-properties"></a>參考屬性  
 下列屬性位於 COM 和 .NET 組件參考中，而且無法修改。  
  
 **組件名稱**  
 顯示參考組件的組件名稱。  
  
 **文化特性**  
 顯示選取參考的文化特性。  
  
 **描述**  
 顯示選取參考的描述。  
  
 **完整路徑**  
 顯示參考組件的目錄路徑。  
  
 **身分識別**  
 針對 .NET Framework 組件，則會顯示完整路徑。 針對 COM 元件，則會顯示 GUID。  
  
 **Label**  
 顯示參考的標籤。  
  
 **名稱**  
 顯示參考的名稱。  
  
 **公開金鑰語彙基元**  
 顯示用來識別參考組件的公開金鑰語彙基元。  
  
 **強式名稱**  
 如果參考組件具有強式名稱，則為 `true`。 強式命名組件是唯一版本。  
  
 **版本**  
 顯示參考組件的版本。  
  
## <a name="see-also"></a>請參閱  
 [屬性頁](../ide/property-pages-visual-cpp.md)   
 [使用專案屬性](../ide/working-with-project-properties.md)