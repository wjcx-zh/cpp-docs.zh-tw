---
title: 連結器工具錯誤 LNK1104
description: 說明 Microsoft C 和C++ （MSVC）連結器錯誤 LNK1104、其原因，以及可能的解決方案。
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: 8878db1b0829703b22b2f7863eb7955d17ad3096
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301778"
---
# <a name="linker-tools-error-lnk1104"></a>連結器工具錯誤 LNK1104

> 無法開啟檔案 '*filename*'

當連結器無法開啟檔案（讀取或寫入）時，就會回報此錯誤。 此問題最常見的兩個原因是：

- 您的程式已在執行中，或已在偵錯工具中載入，而

- 您的程式庫路徑不正確，或不是以雙引號括住。

此錯誤有許多其他可能的原因。 若要縮小範圍，請先檢查哪種檔案*檔案名*是。 然後，使用下列各節來協助識別並修正特定的問題。

## <a name="cant-open-your-app-or-its-pdb-file"></a>無法開啟您的應用程式或其 .pdb 檔案

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>您的應用程式正在執行，或已在偵錯工具中載入

當*filename*是可執行檔的名稱或相關聯的 .pdb 檔案時，請查看您的應用程式是否已在執行中。 然後檢查是否已在偵錯工具中載入。 若要修正此問題，請先停止該程式，然後將它從偵錯工具中卸載，再重新建立。 如果應用程式已在另一個程式中開啟（例如資源編輯器），請將它關閉。 如果您的程式沒有回應，您可能需要使用 [工作管理員] 來結束進程。 您可能也需要關閉並重新啟動 Visual Studio。

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>您的應用程式受到防毒軟體掃描鎖定

防毒程式通常會暫時封鎖對新建立之檔案的存取，特別是 .exe 和 .dll 可執行檔。 若要修正此問題，請嘗試從防毒軟體掃描程式排除您的專案組建目錄。

## <a name="cant-open-a-microsoft-library-file"></a>無法開啟 Microsoft 程式庫檔案

### <a name="windows-libraries-such-as-kernel32lib"></a>Windows 程式庫，例如 kernel32.dll

如果無法開啟的檔案是由 Microsoft 提供的其中一個標準程式庫檔案（例如*kernel32.dll*），您可能會發生專案設定錯誤或安裝錯誤。 確認已安裝 Windows SDK。 如果您的專案需要其他 Microsoft 程式庫（例如 MFC），請確定 Visual Studio 安裝程式也會安裝 MFC 元件。 您可以重新執行安裝程式，隨時新增選用的元件。 如需詳細資訊，請參閱[Modify Visual Studio](/visualstudio/install/modify-visual-studio)。 使用安裝程式中的 [**個別元件**] 索引標籤，選擇特定的程式庫和 sdk。

### <a name="versioned-vcruntime-libraries"></a>已建立版本的 vcruntime 程式庫

如果錯誤訊息有已建立版本的 Microsoft 程式庫（例如*msvcr120.dll*），則可能不會安裝該編譯器版本的平臺工具組。 若要修正這個問題，您有兩個選項：將專案升級為使用目前的平臺工具組，或安裝較舊的工具組並以未變更的方式建立專案。 如需詳細資訊，請參閱[從舊版視覺效果C++升級專案](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)和[在 Visual Studio 中使用原生多目標，以建立舊的專案](../../porting/use-native-multi-targeting.md)。

### <a name="retail-debug-or-platform-specific-libraries"></a>零售、Debug 或平臺特定程式庫

當您第一次建立新的目標平臺或設定（例如零售或 ARM64）時，可能會發生此錯誤。 在 IDE 中，確認已安裝 [[一般] 屬性頁](../../build/reference/general-property-page-project.md)中所指定的**平臺工具**組和**Windows SDK 版本**。 此外，也請確認在 [ [VC + + 目錄] 屬性頁](../../build/reference/vcpp-directories-property-page.md)中指定的連結**庫目錄**中有提供所需的程式庫。 檢查每個設定的屬性，例如 Debug、Retail、x86 或 ARM64。 如果一個組建可以運作，但另一個不是，請比較兩者的設定。 安裝任何遺失的必要工具和程式庫。

### <a name="the-vccorliblib-library"></a>Vccorlib.h .lib 程式庫

通用 Windows （UWP）應用程式或元件沒有 Spectre 緩和的程式庫。 如果錯誤訊息包含*vccorlib.h*，您可能已在 UWP 專案中啟用[/Qspectre](../../build/reference/qspectre.md) 。 停用 **/Qspectre**編譯器選項以修正此問題。 在 Visual Studio 中，變更**Spectre 緩和**屬性。 它位於 [專案**屬性頁**] 對話方塊的 [ **CC++ /**  > 程式**代碼產生**] 頁面中。

### <a name="libraries-in-projects-from-online-or-other-sources"></a>來自線上或其他來源之專案中的程式庫

如果您建立從另一部電腦複製的專案，則程式庫安裝位置可能會不同。 針對命令列組建，請確認已為組建正確設定 LIB 環境變數和程式庫路徑。 在 Visual Studio 中，您可以在專案的屬性頁中，看到並編輯為目前設定的程式庫路徑。 在 [ **VC + + 目錄**] 頁面中，選擇 [連結**庫目錄**] 屬性的下拉式控制項，然後選擇 [**編輯**]。 [連結**庫目錄**] 對話方塊的 [**評估值**] 區段會列出目前搜尋程式庫檔案的路徑。 更新這些路徑以指向您的本機程式庫。

### <a name="updated-windows-sdk-libraries"></a>已更新 Windows SDK 程式庫

當 Windows SDK 的 Visual Studio 路徑已過期時，就會發生此錯誤。 如果您安裝與 Visual Studio 安裝程式無關的較新 Windows SDK，可能會發生此問題。 若要在 IDE 中修正此問題，請更新 [ [VC + + 目錄] 屬性頁](../../build/reference/vcpp-directories-property-page.md)中指定的路徑。 設定路徑中的版本，以符合新的 SDK。 如果您使用開發人員命令提示字元，請更新使用新的 SDK 路徑來初始化環境變數的批次檔。 藉由使用 Visual Studio 安裝程式來安裝更新的 Sdk，可以避免這個問題。

## <a name="cant-open-a-third-party-library-file"></a>無法開啟協力廠商程式庫檔案

此問題有幾個常見的原因：

- 程式庫檔案的路徑可能不正確，或不是以雙引號括住。 或者，您可能尚未將它指定給連結器。

- 您可能已安裝32位版本的程式庫，但您正在建立64位或其他方式。

- 程式庫可能相依于未安裝的其他程式庫。

若要修正命令列組建的路徑問題，請確認已設定 LIB 環境變數。 請確定它包含您所使用之所有程式庫的路徑，以及您所建立的每個設定。 在 IDE 中，程式庫路徑是由**VC + + 目錄** > 連結**庫目錄**屬性所設定。 針對您所建立的每個設定，請確定這裡列出包含您所需程式庫的所有目錄。

您可能需要提供可覆寫標準程式庫目錄的程式庫目錄。 在命令列上，使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項。 在 IDE 中，使用專案的 設定**屬性 > 連結器 > 一般** 屬性頁中的 **其他程式庫目錄** 屬性。

請務必安裝您所建立之設定所需的每個程式庫版本。 請考慮使用[vcpkg](../../vcpkg.md)套件管理公用程式，將許多常見程式庫的安裝和設定自動化。 當您可以時，最好建立自己的協力廠商程式庫複本。 接著，您可以確定所有程式庫的本機相依性，都是針對與您專案相同的設定所建立。

## <a name="cant-open-a-file-built-by-your-project"></a>無法開啟專案所建立的檔案

當連結器嘗試存取時，如果*filename*尚未存在，您可能會看到此錯誤。 當某個專案相依于方案中的另一個專案時，可能會發生這種情況，但專案的建立順序不正確。 若要修正此問題，請確定已在使用檔案的專案中設定您的專案參考。 然後，遺失的檔案會在需要之前建立。 如需詳細資訊，請參閱[在 Visual Studio C++專案中加入參考](../../build/adding-references-in-visual-cpp-projects.md)和[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。

## <a name="cannot-open-file-cprogramobj"></a>無法開啟檔案 ' C：\\程式 .obj '

如果您在錯誤訊息中看到檔案名*C：\\程式 .obj* ，請以雙引號括住您的程式庫路徑。 當以*C：\\程式*檔案開頭的未包裝路徑傳遞至連結器時，就會發生此錯誤。 未包裝的路徑可能也會造成類似的錯誤。 一般而言，它們會在磁片磁碟機的根目錄中顯示非預期的 .obj 檔案。

若要修正命令列組建的這個問題，請檢查[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項參數。 另請檢查 LIB 環境變數中指定的路徑，以及在命令列上指定的路徑。 請務必使用雙引號括住包含空格的任何路徑。

若要在 IDE 中修正此問題，請視需要為您的專案新增下列屬性的雙引號：

- [設定屬性] > [ [VC + + 目錄](../../build/reference/vcpp-directories-property-page.md)] 屬性頁上的 [連結**庫目錄**] 屬性，

- 設定 > 屬性 中的 **其他程式庫目錄** 屬性會 **> 一般** 屬性頁，

- [設定屬性] 中的 [其他相依性 **]** 屬性會 **> 連結器 > 輸入**屬性頁。

## <a name="other-common-issues"></a>其他常見問題

### <a name="path-or-filename-issues"></a>路徑或檔案名問題

當指定給連結器的程式庫檔案名或路徑不正確時，就會發生這個錯誤。 或者，當路徑具有不正確磁片磁碟機規格時。 查看命令列或任何[#pragma 批註（lib、"library_name"）](../../preprocessor/comment-c-cpp.md)指示詞中的問題。 檢查您的拼寫和副檔名，並確認檔案存在於指定的位置。

### <a name="parallel-build-synchronization"></a>平行組建同步處理

如果您使用的是 [平行組建] 選項，Visual Studio 可能已在另一個執行緒上鎖定檔案。 若要修正此問題，請確認相同的程式碼物件或程式庫並未內建在多個專案中。 使用組建相依性或專案參考，在您的專案中挑選已建立的二進位檔。

### <a name="additional-dependencies-specified-in-the-ide"></a>IDE 中指定的其他相依性

當您直接在 [其他相依性 **]** 屬性中指定個別程式庫時，請使用空格來分隔程式庫名稱。 請勿使用逗號或分號。 如果您使用 [**編輯**] 功能表項目來開啟 [**其他**相依性] 對話方塊，請使用 [分行符號] 來分隔名稱，而不是逗號、分號或空格。 當您在 [連結**庫目錄**] 和 [**其他程式庫目錄**] 對話方塊中指定程式庫路徑時，也請使用分行符號。

### <a name="paths-that-are-too-long"></a>太長的路徑

當*檔案名*的路徑擴充為超過260個字元時，您可能會看到此錯誤。 如有需要，請重新排列您的目錄結構，或縮短您的資料夾和檔案名，以縮短路徑。

### <a name="files-that-are-too-large"></a>太大的檔案

發生此錯誤的原因可能是檔案太大。 大小超過 gb 的程式庫或物件檔案可能會造成32位連結器的問題。 此問題的可能修正方法是使用64位工具組。 如需如何在命令列使用64位工具組的詳細資訊，請參閱[如何：在命令列上啟用64位的C++視覺化檢視](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)組。 如需如何在 IDE 中使用64位工具組的相關資訊，請參閱搭配[使用 MSBuild 與64位編譯器和工具](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)。 另請參閱這篇 Stack Overflow 文章：[如何讓 Visual Studio 使用原生的 amd64 工具鏈](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

### <a name="incorrect-file-permissions"></a>不正確的檔案許可權

如果您的檔案許可權不足，無法存取*檔案名*，就會發生此錯誤。 如果您使用一般使用者帳戶來存取受保護系統目錄中的程式庫檔案，可能會發生此問題。 或者，如果您使用的檔案是從仍具有原始許可權的其他使用者所複製，則為。 若要修正此問題，請將檔案移至可寫入的專案目錄。 如果移動的檔案具有無法存取的許可權，請在系統管理員命令視窗中執行 takeown 命令，以取得檔案的擁有權。

### <a name="insufficient-disk-space"></a>磁碟空間不足

當您沒有足夠的磁碟空間時，就會發生此錯誤。 連結器在幾種情況下會使用暫存檔。 即使您有足夠的磁碟空間，大型連結也可能會耗盡或分割可用的磁碟空間。 請考慮使用[/opt （優化）](../../build/reference/opt-optimizations.md)選項;執行可轉移的 COMDAT 排除會多次讀取所有的物件檔案。

### <a name="problems-in-the-tmp-environment-variable"></a>TMP 環境變數中的問題

如果*檔案名*名為「.lnk*nnn*」，則它是連結器為暫存檔案產生的檔案名。 TMP 環境變數中指定的目錄可能不存在。 或者，可能會為 TMP 環境變數指定一個以上的目錄。 只應為 TMP 環境變數指定一個目錄路徑。

## <a name="help-my-issue-isnt-listed-here"></a>說明，我的問題並未列于此處！

如果此處未列出任何問題，您可以使用 Visual Studio 中的意見反應工具來取得協助。 在 IDE 中，移至功能表列，然後選擇 [說明] **> [傳送意見**反應] > [回報問題]。 或者，使用 說明 > 傳送意見反應 來提交建議， **> 傳送建議**。 您也可以使用 Visual Studio C++ [開發人員社區](https://developercommunity.visualstudio.com/spaces/62/index.html)）網站。 用它來搜尋問題的答案，並尋求協助。 如需詳細資訊，請參閱[如何回報視覺效果C++工具組或檔的問題](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果您已探索到修正此問題的新方法，我們應該新增到本文中，請讓我們知道。 您可以使用**此頁面**下方的按鈕，將意見反應傳送給我們。 在我們的[ C++檔 GitHub](https://github.com/MicrosoftDocs/cpp-docs/issues)存放庫中使用它來建立新的問題。 謝謝！
