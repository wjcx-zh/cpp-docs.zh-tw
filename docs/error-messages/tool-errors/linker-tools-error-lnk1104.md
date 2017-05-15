---
title: "連結器工具錯誤 LNK1104 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: c6121f598bc2913b65fe781b07bcc27e6b55375b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="linker-tools-error-lnk1104"></a>連結器工具錯誤 LNK1104
無法開啟檔案 '*filename*'  
  
連結器無法開啟指定的檔案。  
  
## <a name="possible-causes-and-solutions"></a>可能原因和解決方案
  
連結器嘗試開啟檔案進行讀取或寫入時，會發生此錯誤。 發生此問題最常見原因是檔案不存在，找不到其中一個目錄中，連結器搜尋時，或正在使用中，由另一個處理序鎖定。 較少，您可能已用盡磁碟空間、 檔案可能太大，檔案的路徑可能太長，或您沒有存取檔案的權限。  

請檢查這些常見的問題的其中一個︰  

-   當您嘗試加以重新建置您的應用程式已經在執行。 如果無法開啟的檔案是可執行檔或偵錯例如.pdb 檔案，這是常見的原因。 若要修正此問題，停止程式並從偵錯工具卸載再重新建立它。  
  
-   檔案*filename*建置您的方案，但尚不存在時，連結器嘗試存取它。 一個專案相依於另一個專案來產生這個檔案，但未以正確的順序建置專案時，也可能會發生。 若要修正此問題，請確定您的專案參考的專案中，會使用檔案，因此需要之前建立遺失的檔案設定。 如需詳細資訊，請參閱[Visual c + + 專案中加入參考](../../ide/adding-references-in-visual-cpp-projects.md)和[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。  
  
-   檔案名稱或命令列上或 #pragma lib 指示詞中指定的路徑不正確，或包含無效的磁碟機規格。 請檢查拼字正確，並確認檔案存在指定的位置。  
  
-   如果您使用 Visual Studio IDE 建置專案，從另一部電腦複製，程式庫的安裝位置可能會不同。 檢查程式庫目錄屬性[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)和必要時加以更新。 若要查看及編輯目前的程式庫路徑中的 IDE 設定，選擇 [程式庫目錄] 屬性的下拉式清單控制項，選擇**編輯**。 **評估值**程式庫目錄 對話方塊的區段會列出目前搜尋程式庫檔案的路徑。  
  
-   如果您要建置的專案使用較舊版本的 Visual Studio 所建立，該版本的程式庫與平台工具組可能不被安裝。 若要修正此問題，您有兩個選項︰ 您可以升級專案以便使用您已安裝，目前的平台工具組，或者您可以安裝舊版的工具組，並建置專案保持不變。 如需詳細資訊，請參閱[從較早版本的 Visual c + + 升級專案](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)和[使用原生多目標 Visual Studio 中建置舊專案](../../porting/use-native-multi-targeting.md)。
  
-   目前的專案組態或平台工具組的程式庫不會安裝。 請確認在平台工具組和 Windows SDK 指定[一般 屬性頁](../../ide/general-property-page-project.md)為您的專案已安裝，並且確認必要的程式庫中指定之程式庫目錄中，您可以使用[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)的組態設定。 有不同的偵錯和零售組態設定，因此如果其中一個建置的運作方式，但其他會導致錯誤，請確定設定正確，而且需要的工具和程式庫已安裝這兩種設定。  
  
-   Windows SDK 的路徑已過期。 如果您已安裝的版本比您的 Visual Studio 版本還新的 Windows sdk，請確定中指定的路徑[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)更新以符合新的 SDK。 如果您使用開發人員命令提示字元，請確定初始化環境變數的批次檔會更新為新的 SDK 路徑。  
  
-   其他程式可能開啟該檔案，而使連結器無法寫入。 防毒程式經常會暫時封鎖新建立的檔案的存取權。 若要修正此問題，請嘗試將專案組建目錄排除防毒掃描程式。  
  
-   如果您使用平行組建選項，很可能在 Visual Studio 已鎖定另一個執行緒上的檔案。 若要修正此問題，請確認不建置相同的程式碼物件或程式庫中多個專案，並挑選建置的二進位檔，在您的專案中使用的組建相依性或專案參考。  
  
-   您有不正確的 LIB 環境變數。 在命令列組建，請確認 LIB 環境變數會設定，且包含您所使用的程式庫的目錄。 在 ide 中 LIB 變數由程式庫目錄屬性上設定[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)。 請確定所有此處所列的目錄，其中包含您需要的程式庫。 如果您需要提供程式庫目錄會覆寫標準程式庫目錄，您可以使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)) 命令列中或其他程式庫目錄中的屬性連結器屬性頁，為您的專案上的選項。  
  
-   當指定個別的程式庫的專案屬性頁 對話方塊中，程式庫名稱必須是以空格分隔，不是逗號。  
  
-   路徑*filename*超過 260 個字元。 變更名稱，或重新排列您的目錄結構，如有需要可縮短必要檔案的路徑。  
  
-   檔案太大。 程式庫或物件的多個 gb 的大小可能會造成問題的 32 位元連結器檔案。 可能的修正此問題是使用 64 位元工具組。 如需有關如何在命令列執行這項操作的詳細資訊，請參閱[How to︰ 啟用在命令列上的 64 位元 Visual c + + 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。 如需如何在 IDE 中執行這項操作的資訊，請參閱[使用 MSBuild，搭配 64 位元編譯器和工具](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)和此堆疊溢位的 post:[如何讓 Visual Studio 中使用原生 amd64 工具鏈](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。  
  
-   您有檔案權限不足以存取*filename*。 這種情況您存取受保護的系統目錄中的程式庫檔案，或使用擁有其原始的權限的其他使用者從複製的檔案設定。 若要修正此問題，請將檔案移到可寫入的專案目錄。 如果檔案是可寫入的目錄中，但有存取權限，您可以使用系統管理員命令提示字元並執行 takeown.exe 命令，以取得檔案的擁有權。  
  
-   您沒有足夠的磁碟空間。 連結器在幾種情況下會使用暫存檔。 即使您有足夠的磁碟空間，非常大型的連結可以耗盡或片段的可用磁碟空間。 請考慮使用[/editandcontinue （最佳化）](../../build/reference/opt-optimizations.md)選項; 執行可轉移的 comdat 刪除讀取所有目的檔多次。  
  
-   如果*filename*名為 LNK*n*、 連結器為暫存檔所產生的檔案名稱、 TMP 環境變數中指定的目錄可能不存在，或為 TMP 環境變數可指定多個目錄。 只有一個目錄路徑應指定為 TMP 環境變數。  
  
-   如果錯誤訊息是因某程式庫名稱而出現，且您最近才移植了一個舊版 Microsoft Visual C++ 開發系統的 .mak 檔，該程式庫可能不再有效。 請確認程式庫名稱正確，且仍然存在於指定的位置，或更新 LIB 路徑以指向新位置。  

