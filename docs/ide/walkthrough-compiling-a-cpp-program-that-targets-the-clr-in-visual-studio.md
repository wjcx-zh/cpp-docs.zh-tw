---
title: "編譯 c + + 程式為目標 CLR |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
caps.latest.revision: "40"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 152d26874af277d742b106db29a4d9dd9c254c9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>逐步解說：編譯針對 Visual Studio 中 CLR 的 C++ 程式
您可以建立使用.NET 類別，並使用 Visual Studio 開發環境中進行編譯的 Visual c + + 程式。  
  
 此程序，您可以輸入自己的 Visual c + + 程式，或使用其中一種範例程式。 我們在此程序中使用的範例程式會建立名為 textfile.txt 的文字檔，並將它儲存到專案目錄。  
  
## <a name="prerequisites"></a>必要條件  
 這些主題假設您已了解 c + + 語言的基本概念。  
  
### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>若要在 Visual Studio 中建立新的專案，並加入新的來源檔案  
  
1.  建立新的專案。 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
2.  從 Visual c + + 專案類型中，按一下  **CLR**，然後按一下  **CLR 空專案**。  
  
3.  輸入專案名稱。  
  
     根據預設，包含專案的方案具有相同名稱做為新的專案，但您可以輸入不同的名稱。 如果您想要您可以輸入不同的專案位置。  
  
     按一下**確定**建立新的專案。  
  
4.  如果看不到 方案總管 中，按一下**方案總管 中**上**檢視**功能表。  
  
5.  將新的來源檔案加入專案：  
  
    -   以滑鼠右鍵按一下**原始程式檔**資料夾在方案總管 中，指向**新增**按一下**新項目**。  
  
    -   按一下**c + + 檔 (.cpp)**並輸入檔案名稱，然後按一下**新增**。  
  
     **.Cpp**檔案會出現在**原始程式檔**資料夾在方案總管] 和 [索引標籤式的視窗就會顯示將程式碼輸入您想在該檔案。  
  
6.  在 Visual Studio 中的 [新建] 索引標籤中按一下並輸入有效的 Visual c + + 程式，或複製並貼的範例程式。  
  
     例如，您可以使用[如何： 寫入文字檔 (C + + CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md)範例程式 (在**檔案處理和 I/O**程式設計指南 》 的節點)。  
  
     如果您使用範例程式，請注意，您會使用`gcnew`關鍵字取代`new`.NET 物件，而且在建立時`gcnew`傳回的控制代碼 (`^`) 而不是指標 (`*`):  
  
     `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
     如需新 Visual c + + 語法的詳細資訊，請參閱[執行階段平台的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)。  
  
7.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     **輸出**視窗會顯示有關編譯進度，例如組建記錄檔和一個訊息，指出組建狀態的位置資訊。  
  
     如果您進行變更，並執行程式，而不會進行建置，對話方塊可能表示專案已過期。 選取此對話方塊上的核取方塊，再按一下 **確定**如果您想要永遠使用目前版本的檔案，而不是每次提示您的 Visual Studio 建置應用程式。  
  
8.  在**偵錯**功能表上，按一下 **啟動但不偵錯**。  
  
9. 如果您執行程式時，會使用範例程式會顯示命令視窗，指出已建立文字檔案。 按任意鍵關閉命令視窗。  
  
     **Textfile.txt**文字檔現在位於專案目錄中。 您可以使用 [記事本] 開啟此檔案。  
  
    > [!NOTE]
    >  選擇 空白的 CLR 專案範本會自動將設定**/clr**編譯器選項。 若要確認這種情況，請以滑鼠右鍵按一下中的專案**方案總管 中**，然後按一下**屬性**，然後核取**Common Language Runtime 支援**中選項**一般**節點**組態屬性**。  
  
## <a name="whats-next"></a>後續步驟  
 **上一步：** [逐步解說： 編譯原生 c + + 程式命令列上](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)&#124;**下一步：**[逐步解說： 編譯 C 程式命令列上](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
  
## <a name="see-also"></a>另請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)