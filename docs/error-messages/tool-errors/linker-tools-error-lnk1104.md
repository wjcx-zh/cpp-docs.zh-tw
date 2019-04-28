---
title: 連結器工具錯誤 LNK1104
ms.date: 05/17/2017
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: eadeeb7ac19e3975a37a1364502b33400018cb05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255509"
---
# <a name="linker-tools-error-lnk1104"></a>連結器工具錯誤 LNK1104

> 無法開啟檔案 '*filename*'

連結器無法開啟指定的檔案。 此問題最常見原因是檔案，正在使用中或由另一個處理序鎖定，不存在，在其中一個連結器搜尋時，目錄中找不到，或您可能沒有足夠的權限來存取檔案。 較少，您可能已用盡磁碟空間、 檔案可能是太大，或檔案的路徑可能太長。

## <a name="possible-causes-and-solutions"></a>可能原因和解決方案

連結器會嘗試開啟檔案進行讀取或寫入時，會發生此錯誤。 若要縮小可能的原因，首先檢查何種檔案，並使用下列各節來協助識別及修正特定的問題。

### <a name="cannot-open-your-app-or-its-pdb-file"></a>無法開啟您的應用程式或其.pdb 檔案

如果檔案名稱是可執行檔建置您的專案，或關聯的.pdb 檔案，最常見的原因是當您嘗試重建它，或載入偵錯工具中，已經執行您的應用程式。 若要修正此問題，請停止程式，並從 偵錯工具加以卸載，才再次建置它。 如果應用程式已在另一個程式中，開啟資源編輯器，例如關閉它。 在極端的情況下，您可能需要使用終止處理序，或停止並重新啟動 Visual Studio 的 工作管理員。

防毒程式通常暫時封鎖存取新建立的檔案，特別是.exe 和.dll 可執行檔。 若要修正此問題，請嘗試從防毒掃描程式排除您專案的組建目錄。

### <a name="cannot-open-a-microsoft-library-file"></a>無法開啟 Microsoft 程式庫檔案

如果無法開啟的檔案是其中一個標準程式庫檔案，例如 kernel32.lib，由 Microsoft 提供您可能專案設定錯誤或安裝錯誤。 確認已安裝 Windows SDK，而且如果您的專案需要其他 Microsoft 程式庫，例如 MFC，請確定，MFC 元件也已安裝 Visual Studio 安裝程式。 您可以執行安裝程式以在任何時候新增選用元件。 如需詳細資訊，請參閱 <<c0> [ 修改 Visual Studio](/visualstudio/install/modify-visual-studio)。 使用安裝程式中的 [個別元件] 索引標籤，來選擇特定的程式庫和 Sdk。

如果您正在建置使用較舊版本的 Visual Studio 所建立的專案，該版本的程式庫與平台工具組可能未安裝。 如果已建立版本的程式庫名稱，例如 msvcr100.lib，就會出現錯誤訊息，則這可能是原因。 若要修正此問題，您有兩個選項： 您可以升級專案以使用您已安裝，目前的平台工具組，或者您可以安裝舊版的工具組，並建置專案保持不變。 如需詳細資訊，請參閱 <<c0> [ 升級的專案，從較早版本的 Visual C++ ](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)並[使用原生多目標在 Visual Studio 來建置舊專案](../../porting/use-native-multi-targeting.md)。</c0>

如果當您建立新的目標平台或組態時，您會看到此錯誤，可能不會安裝該專案的組態或平台工具組的程式庫。 確認**平台工具組**並**Windows SDK 版本**中指定[一般 屬性頁](../../build/reference/general-property-page-project.md)安裝為您的專案之後，並確認所需程式庫有**程式庫目錄**中指定[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)的組態設定。 有不同的設定，進行偵錯和零售組態，以及 32 位元和 64 位元的組態，因此如果其中一個建置的運作方式，但另一個會產生錯誤，請確定設定正確無誤，而且所需的工具與程式庫會針對安裝每個您所建置的組態。

如果您使用 Visual Studio IDE 來建置專案時，已從另一部電腦複製，程式庫的安裝位置可能會不同。 請檢查**程式庫目錄**屬性上的[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)專案並視需要更新它。 若要查看及編輯目前的程式庫路徑中的 IDE 設定，選擇的下拉式清單控制項**程式庫目錄**屬性，然後選擇**編輯**。 **評估值**一節**程式庫目錄**對話方塊會列出目前搜尋程式庫檔案的路徑。

Windows SDK 的路徑已過期時，也會發生此錯誤。 如果您已安裝的版本比您的 Visual Studio 版本的 Windows sdk，請確定在指定的路徑[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)更新以符合新的 SDK。 如果您使用開發人員命令提示字元，請確定初始化環境變數的批次檔會更新為新的 SDK 路徑。 若要安裝更新的 Sdk 使用 Visual Studio 安裝程式，可以避免這個問題。

### <a name="cannot-open-a-third-party-library-file"></a>無法開啟協力廠商程式庫檔案

有幾個常見的原因，此問題：

- 您的程式庫檔案的路徑可能不正確，或您可能不會指定它為連結器。

- 您可能已安裝 32 位元版本的程式庫，但您要建置 64 位元，或反之亦然。

- 程式庫可能相依於未安裝其他程式庫。

若要修正路徑問題，請確認 LIB 環境變數會設定，且包含使用您建立每個組態之程式庫的所有目錄。 在 IDE 中，LIB 變數會設定**程式庫目錄**屬性上的[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)。 請確定包含您所需的程式庫的所有目錄都列在這裡，方便您建置每個組態。

如果您需要提供程式庫目錄，就會覆寫標準程式庫目錄，您可以使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項命令列上，或在 IDE 中，您可以使用**其他程式庫目錄**中的屬性**組態屬性 > 連結器 > 一般**專案屬性頁面。

請確定您已安裝您建置的組態所需的程式庫的每個版本。 請考慮使用[vcpkg](../../vcpkg.md)套件管理公用程式自動安裝和設定許多常用的程式庫。 可以的話，最好是建置您自己的協力廠商程式庫的複本，讓您確定所有本機相依性需要程式庫，且它們會建立在與專案相同的組態。

### <a name="cannot-open-a-file-built-by-your-project"></a>無法開啟專案建置的檔案

您會看到此錯誤，如果檔案*filename*是您的方案所建置，但尚不存在時，連結器會嘗試存取它。 這種情形時一個專案相依於另一個專案，但並不是專案建置正確的順序。 若要修正此問題，請確定您的專案參考會設定專案中所使用的檔案，因此除非必要，內建遺失的檔案。 如需詳細資訊，請參閱 <<c0> [ 將參考加入至視覺效果C++專案](../../build/adding-references-in-visual-cpp-projects.md)並[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。</c0>

### <a name="cannot-open-file-cprogramobj"></a>無法開啟檔案 ' c:\\Program.obj'

如果您看到這個錯誤或包含您的磁碟機的根目錄中的非預期的.obj 檔案類似的錯誤，問題很可是不會包裝在雙引號括住的程式庫路徑。

若要修正此問題，命令列建置，請檢查[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項參數、 LIB 環境變數中指定的路徑和命令列上指定的路徑，並請務必使用雙精度浮點數-用引號括住的任何路徑包含空格。

若要在 IDE 中修正此問題，請檢查**程式庫目錄**屬性上的[組態屬性 > VC + + 目錄](../../build/reference/vcpp-directories-property-page.md)屬性頁上，**其他程式庫目錄**中的屬性**組態屬性 > 連結器 > 一般**屬性頁上，而**其他相依性**中的屬性**組態屬性 > 連結器 > 輸入**專案屬性頁面。 請確定包含您所需的程式庫的所有目錄路徑會都包裝雙引號括住，如有必要。

### <a name="other-common-issues"></a>其他常見的問題

連結器命令列上或在指定的程式庫檔案名稱或路徑時，會發生此錯誤[#pragma 註解 （"library_name 」 中的 程式庫）](../../preprocessor/comment-c-cpp.md)指示詞不正確，或是路徑中有無效的磁碟機規格。 請檢查拼字和副檔名，並確認檔案存在指定的位置。

其他程式可能開啟該檔案，而使連結器無法寫入。 通常防毒程式暫時封鎖新建立的檔案的存取權。 若要修正此問題，請嘗試從防毒掃描程式排除您專案的組建目錄。

如果您使用的平行組建選項，就可以在 Visual Studio 已鎖定另一個執行緒上的檔案。 若要修正此問題，請確認未建置的相同程式碼的物件或程式庫中多個專案，並挑選已建置的二進位檔，在您的專案中使用組建相依性或專案參考。

當您指定個別的程式庫中**其他相依性**屬性直接使用空格來分隔程式庫名稱、 沒有逗號或分號。 如果您使用**編輯**若要開啟的功能表項目**其他相依性** 對話方塊中，使用換行符號分隔的名稱，不是逗號、 分號或空格。 當您指定程式庫路徑中的也使用換行符號**程式庫目錄**並**其他程式庫目錄**對話方塊。

您可能會看到此錯誤時的路徑*filename*展開至超過 260 個字元。 變更名稱，或重新排列您的目錄結構，如果需要縮短所需的檔案的路徑。

因為檔案太大，就會發生此錯誤。 程式庫或物件的檔案超過 1 gb 大小的 32 位元連結器可能會發生問題。 可能的修正此問題是使用 64 位元工具組。 如需有關如何在命令列執行這項操作的詳細資訊，請參閱[How to:啟用 64 位元視覺效果C++命令列上的工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。 如需如何執行這項操作，在 IDE 中的資訊，請參閱[使用的 MSBuild 與 64 位元編譯器和工具](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)和這個 Stack Overflow 文章：[如何讓 Visual Studio 使用 amd64 原生工具鏈](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

如果您有足夠的檔案存取權限，會發生此錯誤*filename*。 這種情形，如果您使用的一般使用者帳戶及嘗試存取受保護的系統目錄中的程式庫檔案，或使用擁有其原始的權限的其他使用者從複製的檔案設定。 若要修正此問題，請將檔案移至可寫入的專案目錄。 如果檔案是在可寫入的目錄中，但無法存取的權限，您可以使用系統管理員命令提示字元並執行 takeown.exe 命令來取得檔案的擁有權。

當您沒有足夠的磁碟空間時，會發生錯誤。 連結器在幾種情況下會使用暫存檔。 即使您有足夠的磁碟空間，非常大型的連結可以耗盡，或片段的可用磁碟空間。 請考慮使用[/OPT （最佳化）](../../build/reference/opt-optimizations.md)選項; 在進行可轉移 COMDAT 刪除讀取所有目的檔多次。

如果*檔名*稱為 LNK*nnn*、 連結器為暫存檔所產生的檔案名稱、 TMP 環境變數中指定的目錄可能不存在，或可能是多個目錄指定為 TMP 環境變數。 只有一個目錄路徑應指定為 TMP 環境變數。
