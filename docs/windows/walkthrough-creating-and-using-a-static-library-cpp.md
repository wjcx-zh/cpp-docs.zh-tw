---
title: "逐步解說： 建立和使用靜態程式庫 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3af6bc41d353f82bb1f95c73f079e530da19dba0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>逐步解說：建立和使用靜態程式庫 (C++)
本逐步解說示範如何建立搭配 C++ 應用程式使用的靜態程式庫 (.lib 檔案)。 使用靜態程式庫是重複使用程式碼的好方法。 您只要在靜態程式庫中撰寫這些常式一次，然後從需要其功能的應用程式中加以參考，就不需在每個應用程式中都重新實作相同的常式。 從靜態程式庫連結的程式碼會變成應用程式的一部分，您不必安裝另一個檔案即可使用程式碼。  
  
 這份逐步解說涵蓋下列工作：  
  
-   [建立靜態程式庫專案](#BKMK_CreateLibProject)  
  
-   [將類別加入靜態程式庫](#BKMK_AddClassToLib)  
  
-   [建立參考靜態程式庫的 C++ 主控台應用程式](#BKMK_CreateAppToRefTheLib)  
  
-   [在應用程式中使用靜態程式庫的功能](#BKMK_UseLibInApp)  
  
-   [執行應用程式](#BKMK_RunApp)  
  
## <a name="prerequisites"></a>必要條件  
 對 C++ 語言基本知識的了解。  
  
##  <a name="BKMK_CreateLibProject"></a> 建立靜態程式庫專案  
  
#### <a name="to-create-a-static-library-project"></a>建立靜態程式庫專案  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在 [新增專案]  對話方塊的左窗格中，依序展開 [已安裝的] 、[範本] 、[Visual C++] ，然後選取 [Win32] 。  
  
3.  在中央窗格中，選取 [Win32 主控台應用程式] 。  
  
4.  在 [名稱] 方塊中指定專案的名稱，例如 **MathFuncsLib** 。 在 [方案名稱] 方塊中指定方案的名稱，例如 **StaticLibrary** 。 選擇 [確定]  按鈕。  
  
5.  在 [Win32 應用程式精靈]  對話方塊的 [概觀]  頁面上，選擇 [下一步]  按鈕。  
  
6.  在 [應用程式設定]  頁面的 [應用程式類型] 下，選取 [靜態程式庫]   
  
7.  在 [應用程式設定]  頁面的 [其他選項] 下，清除 [先行編譯標頭檔]  核取方塊。  
  
8.  選擇 [完成]  按鈕以建立專案。  
  
##  <a name="BKMK_AddClassToLib"></a> 將類別加入靜態程式庫  
  
#### <a name="to-add-a-class-to-the-static-library"></a>將類別加入靜態程式庫  
  
1.  若要建立新類別的標頭檔，請在方案總管  中開啟 **MathFuncsLib**專案的捷徑功能表，然後選擇 [加入] 、[新項目] 。 在 [加入新項目]  對話方塊的左窗格中，選取 [Visual C++] 底下的 [程式碼] 。 在中間窗格中，選取 [標頭檔 (.h)] 。 指定標頭檔的名稱 (例如 **MathFuncsLib.h**)，然後選擇 [加入]  按鈕。 空白標頭檔隨即顯示。  
  
2.  加入要執行一般算術運算 (例如加法、減法、乘法和除法) 的類別，名稱為 **MyMathFuncs** 。 程式碼應該會與以下相似：  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]  
  
3.  若要建立新類別的原始程式檔，請在方案總管  中開啟 **MathFuncsLib**專案的捷徑功能表，然後選擇 [加入] 、[新項目] 。 在 [加入新項目]  對話方塊的左窗格中，選取 [Visual C++] 底下的 [程式碼] 。 在中間窗格中，選取 [C++ 檔 (.cpp)] 。 指定原始程式檔的名稱 (例如 **MathFuncsLib.cpp**)，然後選擇 [加入]  按鈕。 空白原始程式檔隨即顯示。  
  
4.  使用這個原始程式檔來實作 **MyMathFuncs**的功能。 程式碼應該會與以下相似：  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]  
  
5.  從功能表列中選取 [建置] 、[建置方案]  ，以編譯靜態程式庫。 這會建立可供其他程式使用的靜態程式庫。  
  
    > [!NOTE]
    >  從 Visual Studio 命令列建置時，您必須以兩個步驟建置程式。 首先，執行 **cl /c /EHsc MathFuncsLib.cpp** ，以編譯程式碼並建立名為 **MathFuncsLib.obj**的目的檔( **Cl**命令會叫用編譯器 Cl.exe，而**/c**選項則指定編譯而不連結。 如需詳細資訊，請參閱[/c （編譯而不連結）](../build/reference/c-compile-without-linking.md)。)其次，執行**lib MathFuncsLib.obj**以連結程式碼並建立靜態程式庫**MathFuncsLib.lib**。 ( **lib** 命令會叫用程式庫管理員 Lib.exe。 (如需詳細資訊，請參閱 [LIB Reference](../build/reference/lib-reference.md))。  
  
##  <a name="BKMK_CreateAppToRefTheLib"></a> 建立參考靜態程式庫的 C++ 主控台應用程式  
  
#### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>建立參考靜態程式庫的 C++ 主控台應用程式  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在左窗格中，選取 [Visual C++] 下方的 [Win32] 。  
  
3.  在中央窗格中，選取 [Win32 主控台應用程式] 。  
  
4.  在 [名稱] 方塊中指定專案的名稱，例如 **MyExecRefsLib** 。 在 [方案] 旁邊的下拉式清單中，選取 [加入至方案] 。 這樣會將新專案加入含有靜態程式庫的方案中。 選擇 [確定]  按鈕。  
  
5.  在 [Win32 應用程式精靈]  對話方塊的 [概觀]  頁面上，選擇 [下一步]  按鈕。  
  
6.  在 [應用程式設定]  頁面的 [應用程式類型] 下，選取 [主控台應用程式] 。  
  
7.  在 [應用程式設定]  頁面的 [其他選項] 下，清除 [先行編譯標頭檔]  核取方塊。  
  
8.  選擇 [完成]  按鈕以建立專案。  
  
##  <a name="BKMK_UseLibInApp"></a> 在應用程式中使用靜態程式庫的功能  
  
#### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在應用程式中使用靜態程式庫的功能  
  
1.  建立主控台應用程式之後，系統會自動為您建立空白程式。 原始程式檔的名稱與您先前選擇的名稱相同。 在本範例中，其名稱為 **MyExecRefsLib.cpp**。  
  
2.  您必須先參考數學常式，才能在靜態程式庫中使用它。 若要這麼做，請在方案總管  中開啟 **MyExecRefsLib**專案的捷徑功能表，然後選擇 [參考] 。 在**MyExecRefsLibProperty 頁面**對話方塊方塊中，展開 **通用屬性**節點中，選取**架構和參考**，然後選擇 **新增新的參考** 按鈕。 如需有關**參考**對話方塊中，請參閱[將參考加入](../ide/adding-references-in-visual-cpp-projects.md)。  
  
3.  [加入參考]  對話方塊會列出您可以參考的程式庫。 [專案]  索引標籤會列出目前方案中的專案，以及這些專案含有的任何程式庫。 在 [專案]  索引標籤上，選取 [MathFuncsLib]  核取方塊，然後選擇 [確定]  按鈕。  
  
4.  若要參考 **MathFuncsLib.h** 標頭檔，您必須修改包含的目錄路徑。 在 **MyExecRefsLib** 的 [屬性頁] 對話方塊中，依序展開 [組態屬性]  節點、[C/C++]  節點，然後選取 [一般] 。 在 [其他 Include 目錄] 旁邊，指定 **MathFuncsLib** 目錄的路徑或瀏覽至其位置。  
  
     若要瀏覽至目錄路徑，請開啟屬性值下拉式清單，然後選擇 [編輯] 。 在**其他 Include 目錄**對話方塊中的，在文字方塊中，選取空白行，然後選擇 省略符號按鈕 (**...**) 結尾的行。 在 [選取目錄]  對話方塊中，選取 **MathFuncsLib** 目錄，然後選擇 [選取資料夾]  按鈕以儲存選取項目並關閉對話方塊。 在 [其他 Include 目錄]  對話方塊中，選擇 [確定]  按鈕，然後在 [屬性頁]  對話方塊中選擇 [確定]  按鈕，將您的變更儲存至專案。  
  
5.  您現在可以在這個應用程式中使用 **MyMathFuncs** 類別。 若要這樣做，請以下列程式碼取代 **MyExecRefsLib.cpp** 的內容：  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]  
  
6.  選擇功能表列上的 [建置] 、[建置方案]  ，以建置可執行檔。  
  
##  <a name="BKMK_RunApp"></a> 執行應用程式  
  
#### <a name="to-run-the-app"></a>執行應用程式  
  
1.  在方案總管  中開啟 **MyExecRefsLib** 的捷徑功能表，然後選擇 [設定為啟始專案] ，確定已選取 **MyExecRefsLib**做為預設專案。  
  
2.  若要執行專案，請在功能表列上選擇 [偵錯] 、[啟動但不偵錯] 。 輸出應該會與以下相似：  
  
    ```Output  
    a + b = 106.4  
    a - b = -91.6  
    a * b = 732.6  
    a / b = 0.0747475  
    ```  
  
## <a name="see-also"></a>請參閱  
 [逐步解說：建立和使用動態連結程式庫 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [傳統型應用程式 (Visual C++)](../windows/desktop-applications-visual-cpp.md)