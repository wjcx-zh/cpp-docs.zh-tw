---
title: 使用程式庫和元件中的C++專案
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: dff057977e6b6ff0c36d3a888bc4d5c3aa778576
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274785"
---
# <a name="consuming-libraries-and-components"></a>使用程式庫和元件

通常，C++專案，就必須呼叫函式，或存取資料的靜態程式庫 （.lib 檔案），例如二進位檔案的 DLL，Windows 執行階段元件、 COM 元件或.NET 組件。 在這些情況下，您必須設定專案，以便它可以在建置階段找到該二進位檔。 特定步驟取決於您的專案的二進位檔類型的類型及是否正在為您專案相同的方案中建置二進位檔。 

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Vcpkg 透過使用文件庫下載

若要使用您已下載所使用的程式庫**vcpkg**套件管理員 中，您可以忽略下列指示。 請參閱 [vcpkg：C++適用於 Windows、 Linux 和 MacOS 套件管理員](vcpkg.md#integrate-with-visual-studio-windows)如需詳細資訊。

## <a name="consuming-static-libraries"></a>取用的靜態程式庫

如果正在相同方案中建置靜態程式庫專案：

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>包含使用引號括起來的靜態程式庫標頭檔案。 在典型的方案路徑的開頭`../<library project name>`。 IntelliSense 會協助您找到它。
2. 加入靜態程式庫專案的參考。 以滑鼠右鍵按一下**參考**中的 應用程式 專案節點下**方案總管**，然後選擇 **加入參考**。 

如果靜態程式庫不是方案的一部分：

1. 中的應用程式專案節點上按一下滑鼠右鍵**方案總管**，然後選擇**屬性**。 
2. 在  **VC + + 目錄**屬性頁面上，將.lib 檔中所呈現的所在目錄的路徑**程式庫路徑**並將路徑新增至程式庫標頭檔，在**Include 目錄**.  
3. 在 [**連結器 > 輸入**] 屬性頁面上，新增的.lib 檔案名稱**其他相依性**。

## <a name="dynamic-link-libraries"></a>動態連結程式庫

如果正在建置 DLL 做為應用程式的相同方案的一部分，請遵循相同的步驟，對於靜態程式庫。

如果 DLL 不是應用程式解決方案的一部分，您需要 DLL 檔案，標頭與原型匯出的函式和類別，並提供必要的連結資訊的.lib 檔案。

1. 將 DLL 複製到您的專案的輸出資料夾，或標準的 Windows 搜尋路徑中的另一個資料夾的 Dll。 請參閱[動態連結程式庫搜尋順序](/windows/desktop/dlls/dynamic-link-library-search-order)。
2. 請遵循步驟 1-3 的靜態程式庫提供的標頭和.lib 檔的路徑。

## <a name="com-objects"></a>COM 物件

如果您的原生C++應用程式需要使用 COM 物件，而該物件是*註冊*，那麼您只需要呼叫 CoCreateInstance 並傳入物件的 CLSID。 系統會在 Windows 登錄中找到它，並將其載入。 C++/CLI 專案可以取用 COM 物件，在相同的方式，或將參考加入從**的 加入參考 > COM**清單，並使用它透過其[執行階段可呼叫包裝函式](/dotnet/framework/interop/runtime-callable-wrapper)。 

## <a name="net-assemblies-and-windows-runtime-components"></a>.NET 組件和 Windows 執行階段元件

在 UWP 中或C++/CLI 專案，您可以使用.NET 組件或 Windows 執行階段元件加上*參考*組件或元件。 底下**參考**UWP 中的節點或C++/CLI 專案中，您會看到常用元件的參考。 以滑鼠右鍵按一下**參考**中的節點**方案總管**以顯示**參考管理員**及瀏覽系統所識別的其他元件。 按一下 **瀏覽**按鈕巡覽至任何自訂元件所在的資料夾。 因為.NET 組件和 Windows 執行階段元件包含內建型別資訊，您可以檢視其方法和類別上按一下滑鼠右鍵，然後選擇**在物件瀏覽器中的檢視**。 

## <a name="reference-properties"></a>參考屬性

每種參考類型都包含屬性。 您可以在方案總管中選取參考，然後按 **Alt + Enter**，或按一下滑鼠右鍵並選擇 [屬性] ，來檢視屬性。 部分屬性是唯讀的，而部分屬性則可以修改。 不過，您通常不需要手動修改這些屬性。

### <a name="activex-reference-properties"></a>ActiveX 參考屬性

ActiveX 參考屬性僅適用於 COM 元件的參考。 這些屬性僅在 [參考]  窗格中選取 COM 元件時才會顯示。 屬性不能修改。

- **控制項完整路徑**

   顯示參考控制項的目錄路徑。

- **控制項 GUID**

   顯示 ActiveX 控制項的 GUID。

- **控制項版本**

   顯示參考 ActiveX 控制項的版本。

- **類型程式庫名稱**

   顯示參考類型程式庫的名稱。

- **包裝函式工具**

   顯示用來從參考 COM 程式庫或 ActiveX 控制項建置 Interop 組件的工具。

### <a name="assembly-reference-properties-ccli"></a>組件參考屬性 (C++/CLI)

僅適用於.NET Framework 中的組件的參考組件參考屬性，是C++/CLI 專案。 這些屬性會顯示在選取的.NET Framework 組件時才**參考**窗格。 屬性不能修改。

- **相對路徑**

   顯示從專案目錄到參考組件的相對路徑。

### <a name="build-properties"></a>組建屬性

各種參考類型都會提供下列屬性。 這些屬性可讓您指定如何使用參考進行建置。

- **複製到本機**

   指定是否要在建置期間，自動將參考組件複製到目標位置。

- **複製本機附屬組件 (C++/CLI)**

   指定是否要在建置期間，自動將參考組件的附屬組件複製到目標位置。 僅在 [複製到本機] 為 **true** 時才會使用。

- **參考組件輸出**

   指定這個組件用於建置流程。 如果為 **true**，則組件會在建置期間用於編譯器命令列上。

### <a name="project-to-project-reference-properties"></a>專案對專案參考屬性

下列屬性會定義*專案對專案參考*從專案中選取**參考**窗格，即可對相同方案中的另一個專案。 如需詳細資訊，請參閱[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。

- **連結程式庫相依性**

   當這個屬性為 **True**時，專案系統會將獨立專案所產生的 .lib 檔案連結至相依專案。 一般而言，您將指定為 **True**。

- **專案識別項**

   用來唯一識別獨立專案。 屬性值是無法修改的內部系統 GUID。

- **使用程式庫相依性輸入**

   當這個屬性為 **False**時，專案系統不會將獨立專案所產生的程式庫 .obj 檔案連結至相依專案。 因此，這個值會停用累加連結。 一般而言，您將指定為 **False** ，因為若有許多的獨立專案，建置應用程式可能會花很長的時間。

### <a name="read-only-reference-properties-com--net"></a>唯讀參考屬性 （COM 和.NET）

下列屬性位於 COM 和 .NET 組件參考中，而且無法修改。

- **組件名稱**

   顯示參考組件的組件名稱。

- **文化特性**

   顯示選取參考的文化特性。

- **描述**

   顯示選取參考的描述。

- **完整路徑**

   顯示參考組件的目錄路徑。

- **身分識別**

   針對 .NET Framework 組件，則會顯示完整路徑。 針對 COM 元件，則會顯示 GUID。

- **Label**

   顯示參考的標籤。

- **名稱**

   顯示參考的名稱。

- **公開金鑰語彙基元**

   顯示用來識別參考組件的公開金鑰語彙基元。

- **強式名稱**

   如果參考組件具有強式名稱，則為`true` 。 強式命名組件是唯一版本。

- **版本**

   顯示參考組件的版本。

## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](reference/property-pages-visual-cpp.md)<br>
[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](working-with-project-properties.md)