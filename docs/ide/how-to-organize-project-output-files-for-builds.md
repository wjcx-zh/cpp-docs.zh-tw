---
title: "如何： 組織組建的專案輸出檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 648321c41fe02541eeb746bae24236c40dc5325e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-organize-project-output-files-for-builds"></a>如何：組織組建的專案輸出檔案
本主題描述組織專案輸出檔的最佳作法。 建置不正確地設定專案輸出檔時，可能會發生錯誤。 本主題也概述每一種組織專案輸出檔的優缺點。  
  
## <a name="referencing-clr-assemblies"></a>參考 CLR 組件  
  
#### <a name="to-reference-assemblies-with-using"></a>參考組件的 #using  
  
1.  您可以直接從程式碼參考的組件，透過 #using 指示詞，例如`#using <System.Data.dll>`。 如需詳細資訊，請參閱[#using 指示詞](../preprocessor/hash-using-directive-cpp.md)。  
  
     指定的檔案可以是.dll、.exe、.netmodule 或.obj，只要它會在 MSIL。 以任何語言，可以建立參考的元件。 使用此選項，您可以存取 intellisense 因為會從 MSIL 擷取中繼資料。 有問題的檔案必須位於專案的路徑否則，將不會編譯專案，並將無法使用 Intellisense。 判斷檔案是否在路徑中的簡單方法是以滑鼠右鍵按一下 #using 列，並選擇**開啟的文件**命令。 如果找不到檔案，系統會通知您。  
  
     如果您不想要放置檔案的完整路徑，您可以使用**/AI**編譯器選項，若要編輯的搜尋路徑 #using 參考。 如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](../build/reference/ai-specify-metadata-directories.md)。  
  
#### <a name="to-reference-assemblies-with-fu"></a>參考組件與 /FU  
  
1.  而不是直接從程式碼檔參考組件，如上面所述，您可以使用**/FU**編譯器選項。 這個方法的優點是，您不需要另外加 #using 陳述式會參考指定組件的每個檔案。  
  
     若要設定此選項，開啟**屬性頁**專案。 展開**組態屬性** 節點，然後展開**C/c + +**節點，然後選取**進階**。 加入所需的組件旁**強制 #using**。 如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](../build/reference/fu-name-forced-hash-using-file.md)。  
  
#### <a name="to-reference-assemblies-with-add-new-reference"></a>若要加入新參考與參考組件  
  
1.  這是最簡單的方式來使用 CLR 組件。 首先，請確定專案會編譯與**/clr**編譯器選項。 然後，以滑鼠右鍵按一下專案，從**方案總管 中**選取**新增**，**參考**。 **屬性頁**對話方塊隨即出現。  
  
2.  從**屬性頁**對話方塊中，選取**加入新參考**。 會出現一個對話方塊，列出所有.NET、 COM 及目前的專案中可用的其他組件。 選取所需的組件，然後按一下**確定**。  
  
     一旦設定專案參考，會自動處理對應的相依性。 此外，因為中繼資料是組件的一部分，不是需要加入標頭檔或原型正在使用的項目從 managed 組件。  
  
## <a name="referencing-native-dlls-or-static-libraries"></a>原生 Dll 或靜態程式庫參考  
  
#### <a name="to-reference-native-dlls-or-static-libraries"></a>以參考原生 Dll 或靜態程式庫  
  
1.  參考適當的標頭檔，在程式碼中使用 #include 指示詞。 標頭檔必須在 include 路徑或目前專案的一部分。 如需詳細資訊，請參閱[#include 指示詞 （C/c + +）](../preprocessor/hash-include-directive-c-cpp.md)。  
  
2.  您也可以設定專案相依性。 設定專案相依性，可確保兩件事。 首先，它會確保專案建置以正確的順序，讓專案可以總是找出它所需的相依檔案。 第二，它以隱含方式加入相依專案的輸出目錄路徑，可以輕鬆地找到檔案，在連結時間。  
  
3.  若要部署應用程式，您必須將 DLL 放在適當的位置。 這可以是下列其中一項：  
  
    1.  可執行檔相同的路徑。  
  
    2.  在系統路徑中的任何位置 (**路徑**環境變數)。  
  
    3.  中的-並存組件。 如需詳細資訊，請參閱[建置 C/c + + 並存組件](../build/building-c-cpp-side-by-side-assemblies.md)。  
  
## <a name="working-with-multiple-projects"></a>使用多個專案  
 根據預設，專案建置時，所有輸出檔案都建立專案目錄的子目錄中。 目錄的名稱為根據的組建組態 （例如偵錯或發行）。 為了讓同層級的專案彼此參考，每個專案必須明確地加入其他專案輸出目錄其路徑中的連結才會成功。 當您設定專案相依性，這會自動完成。 不過，如果您不使用相依性，您必須謹慎處理，因為組建可能會變得難以管理。 比方說，當專案偵錯和發行組態，且其中包含同層級專案中的外部程式庫，它應該使用不同的程式庫檔案，根據的建置組態。 因此，硬式編碼這些路徑可能很困難。  
  
 （例如可執行檔、 incremental 連結器檔案和 PDB 檔案） 的所有必要的輸出檔會複製到通用的方案目錄中。 因此，當使用包含數個對等設定的 c + + 專案的方案，所有輸出檔為集中都式的簡化連結和部署中。 您可以確定其應用程式/程式庫能夠如預期般如果它們保持這些檔案 （因為檔案一定會在路徑中）。  
  
 部署至生產環境時，輸出檔案的位置可能是主要的問題。 在 IDE 中執行專案，包括的程式庫路徑不一定是實際執行環境相同。 例如，如果您有`#using "../../lib/debug/mylib.dll"`但然後程式碼中將 mylib.dll 部署到不同的相對位置、 應用程式將會在執行階段失敗。 若要避免這個問題，您應該避免使用中的相對路徑 #include 陳述式在程式碼中。 最好是確定必要的檔案位於專案的建置路徑，而且所有相關的工作檔案的位置是正確。  
  
#### <a name="how-to-specify-where-output-files-go"></a>如何指定輸出檔位置  
  
1.  專案的位置輸出的專案中可以找到設定**屬性頁**。 展開節點旁**組態屬性**選取**一般**。 指定的輸出位置旁**輸出目錄**。 如需詳細資訊，請參閱[一般屬性頁 （專案）](../ide/general-property-page-project.md)。  
  
## <a name="see-also"></a>請參閱  
 [Visual C++ 專案類型](../ide/visual-cpp-project-types.md)