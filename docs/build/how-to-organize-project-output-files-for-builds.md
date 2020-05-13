---
title: 如何：組織組建的專案輸出檔案
ms.date: 05/06/2019
helpviewer_keywords:
- C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
ms.openlocfilehash: 13aa3d1f8e2993ca34163ecbc0515948db56eb79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328522"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>如何：組織組建的專案輸出檔案

本主題描述組織專案輸出檔的最佳做法。 當您不正確地設定專案輸出檔時，可能會發生建置錯誤。 本主題也會概述組織專案輸出檔之每個替代方案的優缺點。

## <a name="referencing-clr-assemblies"></a>參考 CLR 組件

#### <a name="to-reference-assemblies-with-using"></a>使用 #using 參考組件

1. 您可以使用 #using 指示詞，直接從您的程式碼參考組件，例如 `#using <System.Data.dll>`。 如需詳細資訊，請參閱 [#using 指示詞](../preprocessor/hash-using-directive-cpp.md)。

   指定的檔案可以是 .dll、.exe、.netmodule 或.obj，只要是以 MSIL 撰寫即可。 您可以使用任何語言建置參考的元件。 使用此選項，您將可以存取 IntelliSense，因為系統會從 MSIL 擷取中繼資料。 指定的檔案必須位於專案的路徑中；否則，專案不會編譯，且無法使用 IntelliSense。 判斷檔案是否在路徑中的一個簡單方法是以滑鼠右鍵按一下 #using 行，然後選擇 [開啟文件]**** 命令。 如果找不到檔案，系統會通知您。

   如果您不想要放入檔案的完整路徑，您可以使用 **/AI** 編譯器選項，編輯 #using 參考的搜尋路徑。 如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](reference/ai-specify-metadata-directories.md)。

#### <a name="to-reference-assemblies-with-fu"></a>使用 /FU 參考組件

1. 您不必直接從程式碼檔參考組件 (如上所述)，您可以使用 **/FU** 編譯器選項。 這個方法的優點是，您不需要將個別 #using 陳述式新增至每個參考指定組件的檔案。

   若要設定此選項，請開啟專案的 [屬性頁]****。 展開 [組態屬性]**** 節點，然後展開 [C/C++]**** 節點並選取 [進階]****。 將所需的組件新增至 **Force #using** 旁。 如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](reference/fu-name-forced-hash-using-file.md)。

#### <a name="to-reference-assemblies-with-add-new-reference"></a>使用 [新增參考] 參考組件

1. 這是使用 CLR 組件的最簡單方法。 首先，確定使用 **/clr** 編譯器選項編譯專案。 然後，以滑鼠右鍵按一下 [方案總管]**** 中的專案，然後選取 [新增]****、[參考]****。 [屬性頁]**** 對話方塊隨即出現。

1. 從 [屬性頁]**** 對話方塊，選取 [新增參考]****。 這會顯示一個對話方塊，其中列出所有 .NET、COM 及目前專案中可用的其他組件。 選取所需的組件，然後按一下 [確定]****。

   設定專案參考之後，即會自動處理對應的相依性。 此外，由於中繼資料是組件的一部分，因此不需要新增標頭檔或為要從受控組件使用的項目設計原型。

## <a name="referencing-native-dlls-or-static-libraries"></a>參考原生 DLL 或靜態程式庫

#### <a name="to-reference-native-dlls-or-static-libraries"></a>參考原生 DLL 或靜態程式庫

1. 使用 #include 指示詞參考您程式碼中的適當標頭檔。 標頭檔必須在 Include 路徑中，或是目前專案的一部分。 如需詳細資訊，請參閱 [#include 指示詞 (C/C++)](../preprocessor/hash-include-directive-c-cpp.md)。

1. 您也可以設定專案相依性。 設定專案相依性可確保兩件事。 首先，它會確保專案依正確順序建置，因此專案一可以找到所需的相依檔案。 第二，它會隱含地將相依專案的輸出目錄新增至路徑，讓您可以輕鬆地在連結時找到檔案。

1. 若要部署應用程式，您必須將 DLL 放在適當的位置。 這可以是下列項目之一：

   1. 與可執行檔相同的路徑。

   1. 系統路徑 (**path** 環境變數) 中的任何位置。

   1. 在並存組件中。 如需詳細資訊，請參閱[建置 C/C++ 並存組件](building-c-cpp-side-by-side-assemblies.md)。

## <a name="working-with-multiple-projects"></a>使用多個專案

根據預設，建置專案時，會在專案目錄的子目錄中建立所有輸出檔。 目錄會根據組建組態命名 (例如偵錯或發行)。 為了讓同層級專案彼此參考，每個專案必須明確地將其他專案輸出目錄新增至其路徑，連結才能成功。 這會在您設定專案相依性時自動完成。 不過，如果您未使用相依性，則必須謹慎處理，因為組建可能會變得難以管理。 例如，當專案具有偵錯和發行組態，並包含同層級專案中的外部程式庫時，則應該根據要建置的組態，使用不同的程式庫檔。 因此，硬式編碼這些路徑可能很困難。

所有基本輸出檔 (例如可執行檔、累加連結器檔案和 PDB 檔案) 都會複製到通用方案目錄中。 因此，使用含有數個組態相同之 C++ 專案的方案時，會將所有輸出檔集中在一起，以簡化連結和部署。 若將這些檔案保存在一起，您就可以確定其應用程式/程式庫會如預期般運作 (因為檔案一定會在路徑中)。

部署至生產環境時，輸出檔的位置可能是主要問題。 在 IDE 中執行專案時，內含程式庫的路徑不一定會與生產環境相同。 例如，如果您的程式碼中有 `#using "../../lib/debug/mylib.dll"`，但接著將 mylib.dll 部署到不同的相對位置，則應用程式會在執行階段失敗。 為了避免這個問題，您應該避免在程式碼的 #include 陳述式中使用相對路徑。 您最好確保必要檔案在專案建置路徑中，並同樣地確保對應的生產檔案位置正確。

#### <a name="how-to-specify-where-output-files-go"></a>如何指定輸出檔位置

1. 您可以在專案的 [屬性頁]**** 中找到專案輸出設定的位置。 展開 [組態屬性]**** 旁的節點，然後選取 [一般]****。 在 [輸出目錄]**** 旁指定輸出位置。 如需詳細資訊，請參閱[一般屬性頁 (專案)](reference/general-property-page-project.md)。

## <a name="see-also"></a>請參閱

[Visual Studio 中的 C++ 專案類型](reference/visual-cpp-project-types.md)
