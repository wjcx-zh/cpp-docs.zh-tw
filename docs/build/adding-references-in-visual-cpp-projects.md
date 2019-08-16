---
title: 在專案中C++使用程式庫和元件
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: a65ad69914b14e7b8b37c321fa7d06740af57e3a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493378"
---
# <a name="consuming-libraries-and-components"></a>使用程式庫和元件

C++專案通常需要呼叫函數或存取二進位檔案中的資料, 例如靜態程式庫 (.lib 檔案)、DLL、Windows 執行階段元件、COM 元件或 .net 元件。 在這些情況下, 您必須設定專案, 讓它可以在組建階段找到該二進位檔。 特定步驟取決於您專案的類型、二進位檔的類型, 以及二進位檔是否與您的專案建立在相同的方案中。 

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>使用透過 vcpkg 下載的程式庫

若要取用您使用**vcpkg**封裝管理員下載的程式庫, 您可以略過下列指示。 請參閱 [vcpkg：適用C++于 Windows、Linux 和 MacOS](vcpkg.md#integrate-with-visual-studio-windows)的套件管理員, 以取得詳細資訊。

## <a name="consuming-static-libraries"></a>使用靜態程式庫

如果您的靜態程式庫專案是建立在相同的方案中:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>包含靜態程式庫的標頭檔, 並使用引號括住。 在典型的解決方案中, 路徑的開頭`../<library project name>`會是。 IntelliSense 可協助您找到它。
2. 加入靜態程式庫專案的參考。 在**方案總管**中, 以滑鼠右鍵按一下應用程式專案節點底下的 [**參考**], 然後選擇 [**加入參考**]。 

如果靜態程式庫不是解決方案的一部分:

1. 以滑鼠右鍵按一下**方案總管**中的應用程式專案節點, 然後選擇 [**屬性**]。 
2. 在 [ **VC + + 目錄**] 屬性頁的 [連結**庫路徑**] 中, 將路徑加入至 .lib 檔案所在的目錄中, 然後在 [ **Include 目錄**] 中新增程式庫標頭檔的路徑。  
3. 在 [**連結器 > 輸入**] 屬性頁中, 將 .lib 檔案的名稱加入至**其他**相依性。

## <a name="dynamic-link-libraries"></a>動態連結程式庫

如果 DLL 是建立為與應用程式相同的方案之一部分, 請遵循與靜態程式庫相同的步驟。

如果 DLL 不是應用程式方案的一部分, 您需要 DLL 檔案、已匯出函式和類別之原型的標頭, 以及提供必要連結資訊的 .lib 檔案。

1. 將 DLL 複製到您專案的輸出檔案夾, 或是 Dll 的標準 Windows 搜尋路徑中的另一個資料夾。 請參閱[動態連結程式庫搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order)。
2. 遵循適用于靜態程式庫的步驟 1-3, 提供標頭和 .lib 檔案的路徑。

## <a name="com-objects"></a>COM 物件

如果您的C++原生應用程式需要使用 COM 物件, 且該物件已*註冊*, 則您只需要呼叫 CoCreateInstance 並傳入物件的 CLSID。 系統會在 Windows 登錄中找到它, 並將它載入。 C++/Cli 專案可以使用相同的方式取用 COM 物件, 或從 [**新增參考] > COM**清單中加入參考, 然後透過其執行時間可呼叫[包裝](/dotnet/framework/interop/runtime-callable-wrapper)函式來取用它。 

## <a name="net-assemblies-and-windows-runtime-components"></a>.NET 元件和 Windows 執行階段元件

在 UWP 或C++/cli 專案中, 您可以藉由加入元件或元件的*參考*, 來使用 .Net 元件或 Windows 執行階段元件。 在 UWP或C++/Cli 專案的 [參考] 節點底下, 您會看到常用元件的參考。 以滑鼠右鍵按一下**方案總管**中的 [**參考**] 節點, 以顯示**參考管理員**, 並流覽系統已知的其他元件。 按一下 [**流覽]** 按鈕, 流覽至自訂群組件所在的任何資料夾。 由於 .NET 元件和 Windows 執行階段元件包含內建型別資訊, 因此您可以**在物件瀏覽器中**按一下滑鼠右鍵並選擇 [view], 來查看其方法和類別。 

## <a name="reference-properties"></a>參考屬性

每種參考類型都包含屬性。 您可以在方案總管中選取參考，然後按 **Alt + Enter**，或按一下滑鼠右鍵並選擇 [屬性]，來檢視屬性。 部分屬性是唯讀的，而部分屬性則可以修改。 不過，您通常不需要手動修改這些屬性。

### <a name="activex-reference-properties"></a>ActiveX 參考屬性

ActiveX 參考屬性僅適用於 COM 元件的參考。 這些屬性僅在 [參考] 窗格中選取 COM 元件時才會顯示。 屬性不能修改。

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

### <a name="assembly-reference-properties-ccli"></a>元件參考屬性 (C++/cli)

元件參考屬性僅適用于/Cli 專案中C++.NET Framework 元件的參考。 只有在 [**參考**] 窗格中選取了 .NET Framework 元件時, 才會顯示這些屬性。 屬性不能修改。

- **相對路徑**

   顯示從專案目錄到參考組件的相對路徑。

### <a name="build-properties"></a>組建屬性

各種參考類型都會提供下列屬性。 這些屬性可讓您指定如何使用參考進行建置。

- **複製到本機**

   指定是否要在建置期間，自動將參考組件複製到目標位置。

- **複製本機附屬元件 (C++/cli)**

   指定是否要在建置期間，自動將參考組件的附屬組件複製到目標位置。 僅在 [複製到本機] 為 **true** 時才會使用。

- **參考組件輸出**

   指定這個組件用於建置流程。 如果為 **true**，則組件會在建置期間用於編譯器命令列上。

### <a name="project-to-project-reference-properties"></a>專案對專案參考屬性

下列屬性會從 [**參考**] 窗格中選取的專案, 將專案*對專案參考*定義為相同方案中的另一個專案。 如需詳細資訊，請參閱[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。

- **連結程式庫相依性**

   當這個屬性為 **True**時，專案系統會將獨立專案所產生的 .lib 檔案連結至相依專案。 一般而言，您將指定為 **True**。

- **專案識別項**

   用來唯一識別獨立專案。 屬性值是無法修改的內部系統 GUID。

- **使用程式庫相依性輸入**

   當這個屬性為 **False**時，專案系統不會將獨立專案所產生的程式庫 .obj 檔案連結至相依專案。 因此，這個值會停用累加連結。 一般而言，您將指定為 **False** ，因為若有許多的獨立專案，建置應用程式可能會花很長的時間。

### <a name="read-only-reference-properties-com--net"></a>唯讀參考屬性 (COM & .NET)

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