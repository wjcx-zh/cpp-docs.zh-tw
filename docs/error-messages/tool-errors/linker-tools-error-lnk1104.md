---
title: 連結器工具錯誤 LNK1104
ms.date: 09/06/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: f3effd9054954a90f69c5b18d8f099e6d705d9a3
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808845"
---
# <a name="linker-tools-error-lnk1104"></a>連結器工具錯誤 LNK1104

> 無法開啟檔案 '*filename*'

連結器無法開啟指定的檔案。 此問題最常見的原因是檔案正在使用中，或被其他進程鎖定。 也可能是檔案不存在，或在連結器搜尋的其中一個目錄中找不到。 或者，您可能沒有足夠的許可權可以存取檔案。 較少的情況下，您可能已用盡磁碟空間、檔案可能太大，或檔案的路徑可能太長。

## <a name="possible-causes-and-solutions"></a>可能的原因和解決方案

當連結器嘗試開啟檔案以進行讀取或寫入時，就會發生此錯誤。 若要縮小可能的原因，請先檢查它是哪種檔案類型。 然後，使用下列各節來協助識別並修正特定的問題。

### <a name="cant-open-your-app-or-its-pdb-file"></a>無法開啟您的應用程式或其 .pdb 檔案

如果檔案名是您的專案所建立的可執行檔，或相關聯的 .pdb 檔案，最常見的原因是您的應用程式在您嘗試重建它時已在執行，或已在偵錯工具中載入。 若要修正此問題，請先停止該程式，然後將它從偵錯工具中卸載，再重新建立。 如果應用程式已在另一個程式中開啟（例如資源編輯器），請將它關閉。 在極端情況下，您可能需要使用 [工作管理員] 來結束進程，或停止並重新啟動 Visual Studio。

防毒程式通常會暫時封鎖對新建立之檔案的存取，特別是 .exe 和 .dll 可執行檔。 若要修正此問題，請嘗試從防毒軟體掃描程式排除您的專案組建目錄。

### <a name="cant-open-a-microsoft-library-file"></a>無法開啟 Microsoft 程式庫檔案

如果無法開啟的檔案是由 Microsoft 提供的其中一個標準程式庫檔案（例如 kernel32.dll），您可能會發生專案設定錯誤或安裝錯誤。 確認已安裝 Windows SDK，如果您的專案需要其他 Microsoft 程式庫（例如 MFC），請確定 Visual Studio 安裝程式也已安裝 MFC 元件。 您可以重新執行安裝程式，隨時新增選用的元件。 如需詳細資訊，請參閱[Modify Visual Studio](/visualstudio/install/modify-visual-studio)。 使用安裝程式中的 [個別元件] 索引標籤，選擇特定的程式庫和 Sdk。

通用 Windows （UWP）應用程式或元件沒有 Spectre 緩和的程式庫。 如果錯誤報表提及*vccorlib.h* ，您可能已在 UWP 專案中啟用[/Qspectre](../../build/reference/qspectre.md) 。 停用 **/Qspectre**編譯器選項以修正此問題。 在 Visual Studio 中，變更 [專案**屬性頁**] 對話方塊之 [ **CC++/**  > 程式**代碼產生**] 頁面中的**Spectre 緩和**屬性。

如果您要建立使用舊版 Visual Studio 所建立的專案，則可能不會安裝該版本的平臺工具組和程式庫。 如果錯誤訊息是針對已建立版本的程式庫名稱（例如 msvcr100.dll）而發生，這可能是原因。 若要修正這個問題，您有兩個選項：您可以將專案升級為使用您已安裝的最新平臺工具組，也可以安裝舊版工具組並將專案建立為未變更。 如需詳細資訊，請參閱[從舊版視覺效果C++升級專案](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)和[在 Visual Studio 中使用原生多目標，以建立舊的專案](../../porting/use-native-multi-targeting.md)。

如果您在建立新的目標平臺或設定時看到此錯誤，則可能不會安裝該專案設定或平臺工具組的程式庫。 確認已安裝專案的 [[一般] 屬性頁](../../build/reference/general-property-page-project.md)中所指定的**平臺工具**組和**Windows SDK 版本**，並確認所需的程式庫可用於指定的連結**庫目錄**您設定的 [ [VC + + 目錄] 屬性頁](../../build/reference/vcpp-directories-property-page.md)。 有一些不同的偵錯工具和零售設定，以及32位和64位的設定，因此如果有一個組建可運作，但另一個則造成錯誤，請確定設定正確，且已針對每個安裝必要的工具和程式庫您所建立的設定。

如果您使用 Visual Studio IDE 來建立從另一部電腦複製的專案，則程式庫的安裝位置可能會不同。 檢查項目的 [ [VC + + 目錄] 屬性頁](../../build/reference/vcpp-directories-property-page.md)上的 [連結**庫目錄**] 屬性，並視需要加以更新。 若要查看和編輯 IDE 中設定的目前程式庫路徑，請選擇 [連結**庫目錄**] 屬性的下拉式控制項，然後選擇 [**編輯**]。 [連結**庫目錄**] 對話方塊的 [**評估值**] 區段會列出目前搜尋程式庫檔案的路徑。

當 Windows SDK 的路徑已過期時，也可能會發生此錯誤。 如果您安裝的 Windows SDK 版本比 Visual Studio 的版本更新，請確定已更新 [ [VC + + 目錄] 屬性頁](../../build/reference/vcpp-directories-property-page.md)中指定的路徑，以符合新的 SDK。 如果您使用開發人員命令提示字元，請確定已針對新的 SDK 路徑更新初始化環境變數的批次檔。 藉由使用 Visual Studio 安裝程式來安裝更新的 Sdk，可以避免這個問題。

### <a name="cannot-open-a-third-party-library-file"></a>無法開啟協力廠商程式庫檔案

此問題有幾個常見的原因：

- 您的程式庫檔案路徑可能不正確，或者您可能未將它指定至連結器。

- 您可能已安裝32位版本的程式庫，但您正在建立64位，或反之亦然。

- 程式庫可能相依于未安裝的其他程式庫。

若要修正路徑問題，請確認已針對您所建立的每個設定，設定 LIB 環境變數，並包含您所使用之程式庫的所有目錄。 在 IDE 中，LIB 變數是由 [ [VC + + 目錄] 屬性頁](../../build/reference/vcpp-directories-property-page.md)上的 [連結**庫目錄**] 屬性所設定。 針對您所建立的每個設定，請確定這裡列出包含您所需程式庫的所有目錄。

如果您需要提供覆寫標準程式庫目錄的程式庫目錄，您可以在命令列上使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項，或在 IDE 中，使用設定屬性中的 [**其他程式庫目錄**] 屬性 **> 連結器 > 專案的 [一般**] 屬性頁。

請確定您已安裝您所建立之設定所需的每個程式庫版本。 請考慮使用[vcpkg](../../vcpkg.md)套件管理公用程式，將許多常見程式庫的安裝和設定自動化。 當您可以時，最好是建立您自己的協力廠商程式庫複本，因此您一定要擁有程式庫所需的所有本機相依性，而且它們是針對與您專案相同的設定所建立。

### <a name="cannot-open-a-file-built-by-your-project"></a>無法開啟專案所建立的檔案

如果您的*方案已建立檔案名，* 但當連結器嘗試存取時還不存在，您可能會看到這個錯誤。 當某個專案相依于另一個專案，但不是以正確的順序建立專案時，就會發生這種情況。 若要修正此問題，請確定已在使用檔案的專案中設定您的專案參考，以便在需要時建立遺漏的檔案。 如需詳細資訊，請參閱[在 Visual Studio C++專案中加入參考](../../build/adding-references-in-visual-cpp-projects.md)和[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。

### <a name="cannot-open-file-cprogramobj"></a>無法開啟檔案 ' C：\\Program .obj '

如果您看到此錯誤，或涉及磁片磁碟機根目錄中非預期 .obj 檔案的類似錯誤，則問題幾乎就是不以雙引號括住的程式庫路徑。

若要修正命令列組建的這個問題，請檢查[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項參數、LIB 環境變數中指定的路徑，以及命令列上指定的路徑，並務必在包含空格的任何路徑前後加上雙引號。

若要在 IDE 中修正此問題，請檢查 [設定屬性] [> [VC + + 目錄](../../build/reference/vcpp-directories-property-page.md)] 屬性頁上的 [連結**庫目錄**] 屬性，設定屬性 > 連結器中的 [**其他程式庫目錄**] 屬性 **> [一般**] 屬性頁和 [設定屬性] 中的 [其他相依性 **]** 屬性， **> 連結器 >** 專案的輸入屬性頁。 如有必要，請確定包含您所需程式庫的所有目錄路徑都以雙引號括住。

### <a name="other-common-issues"></a>其他常見的問題

當命令列或[#pragma 批註（lib、"library_name"）](../../preprocessor/comment-c-cpp.md)指示詞中的程式庫檔案名或路徑不正確，或路徑具有不正確磁片磁碟機規格時，就會發生此錯誤。 檢查您的拼寫和副檔名，並確認檔案存在於指定的位置。

其他程式可能開啟該檔案，而使連結器無法寫入。 防毒程式通常會暫時封鎖對新建立檔案的存取。 若要修正此問題，請嘗試從防毒軟體掃描程式排除您的專案組建目錄。

如果您使用平行組建選項，Visual Studio 可能已在另一個執行緒上鎖定檔案。 若要修正此問題，請確認您未在多個專案中建立相同的程式碼物件或程式庫，而且您使用組建相依性或專案參考來挑選項目中的內建二進位檔。

當您直接在 [其他相依性 **]** 屬性中指定個別程式庫時，請使用空格來分隔程式庫名稱，而不是逗號或分號。 如果您使用 [**編輯**] 功能表項目來開啟 [**其他**相依性] 對話方塊，請使用 [分行符號] 來分隔名稱，而不是逗號、分號或空格。 當您在 [連結**庫目錄**] 和 [**其他程式庫目錄**] 對話方塊中指定程式庫路徑時，也請使用分行符號。

當*檔案名*的路徑擴充為超過260個字元時，您可能會看到此錯誤。 如有需要，請變更名稱或重新整理您的目錄結構，以縮短所需檔案的路徑。

發生此錯誤的原因可能是檔案太大。 大小超過 gb 的程式庫或物件檔案可能會造成32位連結器的問題。 此問題的可能修正方法是使用64位工具組。 如需如何在命令列執行此動作的詳細資訊，請[參閱如何：在命令列](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)上啟用 64 C++位的視覺化檢視組。 如需如何在 IDE 中執行此動作的相關資訊，請參閱[使用 MSBuild 搭配64位編譯器和工具](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)和此 Stack Overflow 文章：[如何讓 Visual Studio 使用原生的 amd64 工具鏈](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

如果您的檔案許可權不足，無法存取*檔案名*，就會發生此錯誤。 如果您使用一般使用者帳戶並嘗試存取受保護系統目錄中的程式庫檔案，或使用已設定原始許可權的其他使用者所複製的檔案，就可能發生這種情況。 若要修正此問題，請將檔案移至可寫入的專案目錄。 如果檔案位於可寫入的目錄，但具有無法存取的許可權，您可以使用系統管理員命令提示字元，並執行 takeown 命令來取得檔案的擁有權。

當您沒有足夠的磁碟空間時，就會發生此錯誤。 連結器在幾種情況下會使用暫存檔。 即使您有足夠的磁碟空間，非常大的連結也可能會耗盡或分割可用的磁碟空間。 請考慮使用[/opt （優化）](../../build/reference/opt-optimizations.md)選項;執行可轉移的 COMDAT 排除會多次讀取所有的物件檔案。

如果*檔案名*名為「.lnk*nnn*」，這是連結器為暫存檔案產生的檔案名，則 tmp 環境變數中指定的目錄可能不存在，或可能為 TMP 環境變數指定一個以上的目錄。 只應為 TMP 環境變數指定一個目錄路徑。
