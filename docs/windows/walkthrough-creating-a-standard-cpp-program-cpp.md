---
title: "逐步解說：建立 Win32 主控台程式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vcfirstapp"
  - "vccreatefirst"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令列應用程式 [C++], 標準"
  - "標準應用程式 [C++]"
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：建立 Win32 主控台程式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在 Visual Studio 整合式開發環境 \(IDE\) 中使用 Visual C\+\+，以建立 Standard C\+\+ 程式。  遵循本逐步解說中的步驟，您即可使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 建立專案、將新的檔案加入至專案、修改檔案以加入 C\+\+ 程式碼，然後編譯及執行程式。  
  
 您可以輸入自己的 C\+\+ 程式，或是使用其中一個範例程式，  本逐步解說中的範例程式是主控台應用程式。  這個應用程式會使用「標準樣板程式庫」\( Standard Template Library，STL\) 中的 `set` 容器。  
  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 符合 2003 C\+\+ 標準，但有下列主要例外狀況：兩階段名稱查閱、例外狀況規格和匯出。  此外，[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 支援數種 C\+\+0x 功能，例如，lambdas、auto、static\_assert、rvalue 參考和 extern 範本。  
  
> [!NOTE]
>  如果一定要符合此標準，請使用 **\/Za** 編譯器選項來停用 Microsoft 對此標準的擴充功能。  如需詳細資訊，請參閱[\/Za、\/Ze \(停用語言擴充功能\)](../build/reference/za-ze-disable-language-extensions.md)。  
  
## 必要條件  
 若要完成此逐步解說，您必須了解 C\+\+ 語言的基礎。  
  
### 若要建立專案並加入原始程式檔  
  
1.  指向 \[**檔案**\] 功能表上的 \[**新增**\]，然後按一下 \[**專案**\]，即可建立專案。  
  
2.  在 \[**Visual C\+\+**\] 專案類型窗格中，按一下 \[**Win32**\]，再按一下 \[**Win32 主控台應用程式**\]。  
  
3.  輸入專案的名稱。  
  
     根據預設，包含此專案的方案具有與專案相同的名稱，但您可以輸入不同的名稱。  您也可以輸入不同的專案位置。  
  
     按一下 \[**確定**\] 建立專案。  
  
4.  在 \[**Win32 應用程式精靈**\] 中，按 \[**下一步**\]，選取 \[**空專案**\]，再按一下 \[**完成**\]。  
  
5.  如果 \[**方案總管**\] 並未顯示，請在 \[**檢視**\] 功能表上，按一下 \[**方案總管**\]。  
  
6.  如下所述，將新的原始程式檔加入至專案。  
  
    1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**原始程式檔**\] 資料夾，指向 \[**加入**\]，然後按一下 \[**新增項目**\]。  
  
    2.  在 \[**程式碼**\] 節點中，按一下 \[**C\+\+ 檔 \(.cpp\)**\]，輸入檔案的名稱，然後按一下 \[**加入**\]。  
  
     .cpp 檔會出現在 \[**方案總管**\] 的 \[原始程式檔\] 資料夾中，並且在 Visual Studio 編輯器中開啟。  
  
7.  在編輯器中的檔案中，輸入使用 Standard C\+\+ 程式庫的有效 C\+\+ 程式，或是複製其中一個範例程式並貼到檔案中。  
  
     例如，您可以使用 [set::find](../misc/set-find-stl-samples.md) 範例程式，這是 \[說明\] 內含的其中一個標準樣板程式庫範例。  
  
     如果您使用範例程式，請注意 `using namespace std;` 指示詞。  這個指示詞讓程式能夠使用 `cout` 和 `endl`，而不需使用完整名稱 \(`std::cout` 和 `std::endl`\)。  
  
8.  儲存檔案。  
  
9. 在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     \[**輸出**\] 視窗會顯示有關編譯進度的資訊，例如，建置記錄檔的位置以及表示建置狀態的訊息。  
  
10. 在 \[**偵錯**\] 功能表上，按一下 \[**啟動但不偵錯**\]。  
  
     如果您是使用範例程式，就會出現命令視窗，顯示出是否在集合中找到特定整數。  
  
## 後續步驟  
 **上一個主題**：[Creating Command\-Line Applications \(C\+\+\)](http://msdn.microsoft.com/zh-tw/2505d9ed-aca4-426a-9071-078a2d707254)。  **下一個主題**：[逐步解說：在命令列上編譯原生 C\+\+ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)