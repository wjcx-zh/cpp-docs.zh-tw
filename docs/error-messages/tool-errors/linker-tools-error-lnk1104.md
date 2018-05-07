---
title: 連結器工具錯誤 LNK1104 |Microsoft 文件
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b832d4bceab88fbf3fbe8325a414669d11073c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1104"></a>連結器工具錯誤 LNK1104

> 無法開啟檔案 '*filename*'

連結器無法開啟指定的檔案。 發生此問題最常見原因是檔案，正在使用中或遭其他處理序、 不存在、 在其中一個連結器搜尋時，目錄中找不到，或您可能沒有足夠的權限存取檔案。 較少，您可能已用盡磁碟空間、 檔案可能太大，或檔案的路徑可能太長。

## <a name="possible-causes-and-solutions"></a>可能原因和解決方案

連結器嘗試開啟檔案進行讀取或寫入時，會發生此錯誤。 縮小可能的原因，先檢查何種檔案，並使用下列各節來協助識別並修正特定的問題。

### <a name="cannot-open-your-app-or-its-pdb-file"></a>無法開啟您的應用程式或其.pdb 檔案

如果檔案名稱是可執行檔建置您的專案，或關聯的.pdb 檔案，最常見的原因是當您嘗試重新建置，或它載入偵錯工具中，已經執行您的應用程式。 若要修正此問題，停止程式並從偵錯工具卸載再重新建立它。 如果應用程式已開啟另一個程式中，例如資源編輯器中，將它關閉。 在極端的情況下，您可能需要使用工作管理員來終止此程序，或停止並重新啟動 Visual Studio。

防毒程式通常暫時封鎖存取新建立的檔案，特別是.exe 和.dll 可執行檔。 若要修正此問題，請嘗試將專案組建目錄排除防毒掃描程式。

### <a name="cannot-open-a-microsoft-library-file"></a>無法開啟 Microsoft 程式庫檔案

如果無法開啟的檔案是其中一個標準程式庫檔案，Microsoft 提供的例如 kernel32.lib，您可能必須專案組態錯誤或安裝錯誤。 確認已安裝 Windows SDK，如果您的專案需要 MFC 等其他 Microsoft 程式庫，請確定，MFC 元件同時安裝了 Visual Studio 安裝程式。 您可以執行安裝程式一次在任何時候新增選用元件。 如需詳細資訊，請參閱[修改 Visual Studio](/visualstudio/install/modify-visual-studio)。 使用安裝程式中的個別元件 索引標籤，來選擇特定程式庫和 Sdk。

如果您正在建置使用較舊版本的 Visual Studio 所建立的專案，該版本的程式庫與平台工具組可能未安裝。 如果已建立版本的程式庫名稱，例如 msvcr100.lib，就會出現錯誤訊息，則這可能是原因。 若要修正此問題，您有兩個選項： 您可以升級專案以便使用您已安裝，目前的平台工具組，或者您可以安裝舊版的工具組，並建置專案保持不變。 如需詳細資訊，請參閱[從較早版本的 Visual c + + 升級專案](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)和[使用原生多目標 Visual Studio 中建置舊專案](../../porting/use-native-multi-targeting.md)。

如果當您建置新的目標平台或組態，您會看到這個錯誤，可能未安裝該專案的組態或平台工具組的程式庫。 確認**平台工具組**和**Windows SDK 版本**中所指定[一般 屬性頁](../../ide/general-property-page-project.md)為您的專案已安裝，並且確認所需中的程式庫可用**程式庫目錄**中所指定[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)的組態設定。 有不同的偵錯設定和零售組態，以及 32 位元和 64 位元的組態，因此如果其中一個建置的運作方式，但另一個會產生錯誤，請確定設定正確，而且已安裝必要的工具和程式庫每個您所建立的組態。

如果您使用 Visual Studio IDE 建置專案，從另一部電腦複製，程式庫的安裝位置可能會不同。 檢查**程式庫目錄**屬性[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)專案並且如有必要更新它。 若要查看及編輯目前的程式庫路徑中的 IDE 設定，選擇 下拉式清單控制項**程式庫目錄**屬性，然後選擇 **編輯**。 **評估值**區段**程式庫目錄**對話方塊會列出目前搜尋程式庫檔案的路徑。

Windows SDK 的路徑已過期時，也會發生這個錯誤。 如果您已安裝的版本比您的 Visual Studio 版本還新的 Windows sdk，請確定中指定的路徑[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)更新以符合新的 SDK。 如果您使用開發人員命令提示字元，請確定初始化環境變數的批次檔會更新為新的 SDK 路徑。 使用 Visual Studio 安裝程式來安裝更新的 Sdk，可以避免這個問題。

### <a name="cannot-open-a-third-party-library-file"></a>無法開啟協力廠商程式庫檔案

有數個常見的原因，此問題：

- 程式庫檔案的路徑可能不正確，或您可能不會指定它至連結器。

- 您可能已安裝的 32 位元版本的程式庫，但您要建置為 64 位元，反之亦然。

- 程式庫可能相依於未安裝其他程式庫。

若要修正路徑問題，請確認 LIB 環境變數會設定，且包含使用您建立每個組態的程式庫的目錄。 LIB 變數在 ide 中設定**程式庫目錄**屬性[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)。 請確定您建立每個組態，列出所有目錄，其中包含您需要的程式庫。

如果您需要提供程式庫目錄會覆寫標準程式庫目錄，您可以使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項命令列上，或在 IDE 中，您可以使用**其他程式庫目錄**中的屬性**組態屬性 > 連結器 > 一般**專案屬性頁面。

請確定您已安裝您所建立的組態所需的程式庫的每個版本。 請考慮使用[vcpkg](../../vcpkg.md)封裝管理公用程式自動安裝和安裝程式的許多常見的程式庫。 可能的話，最好組建的協力廠商程式庫，您的複本，因此請確定所有本機相依程式庫需要，且它們會建立與您專案相同的組態。

### <a name="cannot-open-a-file-built-by-your-project"></a>無法開啟您專案所建置的檔案

您可能會看到這個錯誤，如果檔案*filename*建置您的方案，但尚不存在時，連結器嘗試存取它。 一個專案相依於另一個專案，但未以正確的順序建置專案時，也可能會發生。 若要修正此問題，請確定您的專案參考的專案中，會使用檔案，因此需要之前建立遺失的檔案設定。 如需詳細資訊，請參閱[Visual c + + 專案中加入參考](../../ide/adding-references-in-visual-cpp-projects.md)和[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。

### <a name="cannot-open-file-cprogramobj"></a>無法開啟檔案 ' c:\\Program.obj'

如果您看到此錯誤或類似的錯誤與您的磁碟機根目錄中的非預期的.obj 檔案，問題是幾乎肯定不會經過包裝在雙引號內的程式庫路徑。

若要修正此問題的命令列組建，請檢查[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項參數、 LIB 環境變數中指定的路徑和命令列上指定的路徑，並確定使用雙引號括住任何路徑包含空格。

若要在 IDE 中修正此問題，請檢查**程式庫目錄**屬性[組態屬性 > VC + + 目錄](../../ide/vcpp-directories-property-page.md)屬性頁**其他程式庫目錄**中的屬性**組態屬性 > 連結器 > 一般**屬性頁上，而**其他相依性**屬性**組態內容 > 連結器 > 輸入**專案屬性頁面。 請確定所有的目錄路徑，包含您需要的程式庫包裝在雙引號中如有必要。

### <a name="other-common-issues"></a>其他常見的問題

連結器命令列上或在指定的程式庫檔案名稱或路徑時，會發生此錯誤[#pragma 註解 （程式庫，"library_name 」）](../../preprocessor/comment-c-cpp.md)指示詞不正確，或包含無效的磁碟機規格。 請檢查您的拼字和副檔名，並確認檔案存在指定的位置。

其他程式可能開啟該檔案，而使連結器無法寫入。 防毒程式經常會暫時封鎖新建立的檔案的存取權。 若要修正此問題，請嘗試將專案組建目錄排除防毒掃描程式。

如果您使用平行組建選項，很可能在 Visual Studio 已鎖定另一個執行緒上的檔案。 若要修正此問題，請確認不建置相同的程式碼物件或程式庫中多個專案，並挑選建置的二進位檔，在您的專案中使用的組建相依性或專案參考。

當您指定個別的程式庫中**其他相依性**屬性直接管理，以空格分開的文件庫名稱、 不逗號或分號。 如果您使用**編輯**功能表項目，以開啟**其他相依性**對話方塊中，使用換行，來分隔名稱、 不是逗號、 分號或空格。 當您指定程式庫路徑中的也使用換行**程式庫目錄**和**其他程式庫目錄**對話方塊。

您可能會看到這個錯誤時的路徑*filename*超過 260 個字元。 變更名稱，或重新排列您的目錄結構，如有需要可縮短必要檔案的路徑。

因為檔案太大，就會發生此錯誤。 程式庫或物件的多個 gb 的大小可能會造成問題的 32 位元連結器檔案。 可能的修正此問題是使用 64 位元工具組。 如需有關如何在命令列執行這項操作的詳細資訊，請參閱[How to： 啟用在命令列上的 64 位元 Visual c + + 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。 如需如何在 IDE 中執行這項操作的資訊，請參閱[使用 MSBuild，搭配 64 位元編譯器和工具](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)和此堆疊溢位的 post:[如何讓 Visual Studio 中使用原生 amd64 工具鏈](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

如果您有足夠的檔案存取權限，會發生此錯誤*filename*。 這種情形，如果您使用一般使用者帳戶和嘗試存取受保護的系統目錄中的程式庫檔案，或使用擁有其原始的權限的其他使用者從複製的檔案設定。 若要修正此問題，請將檔案移到可寫入的專案目錄。 如果檔案是可寫入的目錄中，但有存取權限，您可以使用系統管理員命令提示字元並執行 takeown.exe 命令，以取得檔案的擁有權。

當您沒有足夠的磁碟空間時，會發生錯誤。 連結器在幾種情況下會使用暫存檔。 即使您有足夠的磁碟空間，非常大型的連結可以耗盡或片段的可用磁碟空間。 請考慮使用[/editandcontinue （最佳化）](../../build/reference/opt-optimizations.md)選項; 執行可轉移 COMDAT 刪除讀取所有目的檔多次。

如果*filename*名為 LNK*nnn*，這是連結器為暫存檔所產生的檔案名稱、 TMP 環境變數中指定的目錄可能不存在，或可能是一個以上的目錄指定為 TMP 環境變數。 只有一個目錄路徑應指定為 TMP 環境變數。
