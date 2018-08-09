---
title: 逐步解說： 建立和使用靜態程式庫 （c + +） |Microsoft Docs
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ebcf09fd4fdda4269edec66f863b239e00e51e1d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652971"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>逐步解說：建立和使用靜態程式庫 (C++)
本逐步解說示範如何建立搭配 C++ 應用程式使用的靜態程式庫 (.lib 檔案)。 使用靜態程式庫是重複使用程式碼的好方法。 您只要在靜態程式庫中撰寫這些常式一次，然後從需要其功能的應用程式中加以參考，就不需在每個應用程式中都重新實作相同的常式。 從靜態程式庫連結的程式碼會變成應用程式的一部分，您不必安裝另一個檔案即可使用程式碼。  
  
 這份逐步解說涵蓋下列工作：  
  
-   [建立靜態程式庫專案](#CreateLibProject)  
  
-   [將類別加入靜態程式庫](#AddClassToLib)  
  
-   [建立 c + + 主控台應用程式會參考靜態程式庫](#CreateAppToRefTheLib)  
  
-   [靜態程式庫的應用程式中使用的功能](#UseLibInApp)  
  
-   [執行應用程式](#RunApp)  
  
## <a name="prerequisites"></a>必要條件  
 對 C++ 語言基本知識的了解。  
  
##  <a name="CreateLibProject"></a> 建立靜態程式庫專案  
  
### <a name="to-create-a-static-library-project"></a>建立靜態程式庫專案  
  
1.  在功能表列上，選擇 [檔案] > [新增] > [專案]。  
  
2. 在左窗格中**新的專案**對話方塊方塊中，展開**已安裝，Visual c + +**，然後選取**Windows Desktop**。
  
3. 在中央窗格中，選取**Windows Desktop 精靈**。  
  
4.  指定專案的名稱 — 例如， *MathFuncsLib*— 在**名稱** 方塊中。 指定方案的名稱 — 例如， *StaticLibrary*— 在**方案名稱** 方塊中。 選擇 [確定]  按鈕。  
  
5. 底下**應用程式類型**，選取 靜態程式庫 (.lib)。  
  
6. 底下**其他選項**，取消核取**先行編譯標頭**核取方塊。
  
7. 選擇**確定**建立專案。  
 
##  <a name="AddClassToLib"></a> 將類別加入靜態程式庫  
  
### <a name="to-add-a-class-to-the-static-library"></a>將類別加入靜態程式庫  
  
1.  若要建立新類別的標頭檔，請在方案總管  中開啟 **MathFuncsLib**專案的捷徑功能表，然後選擇 [加入] 、[新項目] 。 在 [加入新項目]  對話方塊的左窗格中，選取 [Visual C++] 底下的 [程式碼] 。 在中間窗格中，選取 [標頭檔 (.h)] 。 指定標頭檔的名稱 — 比方說， *MathFuncsLib.h*，然後選擇**新增**按鈕。 空白標頭檔隨即顯示。  
  
2.  加入要執行一般算術運算 (例如加法、減法、乘法和除法) 的類別，名稱為 **MyMathFuncs** 。 程式碼應該會與以下相似：  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]  
  
3.  若要建立新類別的原始程式檔，請在方案總管  中開啟 **MathFuncsLib**專案的捷徑功能表，然後選擇 [加入] 、[新項目] 。 在 [加入新項目]  對話方塊的左窗格中，選取 [Visual C++] 底下的 [程式碼] 。 在中間窗格中，選取 [C++ 檔 (.cpp)] 。 指定原始程式檔的名稱 — 比方說， *MathFuncsLib.cpp*，然後選擇**新增** 按鈕。 空白原始程式檔隨即顯示。  
  
4.  使用這個原始程式檔來實作 **MyMathFuncs**的功能。 程式碼應該會與以下相似：  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]  
  
5.  選取編譯靜態程式庫**建置** > **建置方案**功能表列上。 這會建立可供其他程式使用的靜態程式庫。  
  
    > [!NOTE]
    >  從 Visual Studio 命令列建置時，您必須以兩個步驟建置程式。 首先，執行`cl /c /EHsc MathFuncsLib.cpp`編譯的程式碼，並建立物件的檔案，稱為**MathFuncsLib.obj**。(`cl` 命令會叫用編譯器 Cl.exe，而 `/c` 選項則指定編譯但不連結。 如需詳細資訊，請參閱 < [/c （編譯而不連結）](../build/reference/c-compile-without-linking.md)。)其次，執行**lib MathFuncsLib.obj**連結程式碼，並建立靜態程式庫**MathFuncsLib.lib**。 (`lib` 命令會叫用程式庫管理員 Lib.exe。 (如需詳細資訊，請參閱 [LIB Reference](../build/reference/lib-reference.md))。  
  
##  <a name="CreateAppToRefTheLib"></a> 建立 c + + 主控台應用程式會參考靜態程式庫  
  
### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>建立參考靜態程式庫的 C++ 主控台應用程式  
  
1.  在功能表列上，選擇 [檔案] > [新增] > [專案]。  
  
2. 在左窗格中**新的專案**對話方塊方塊中，展開**已安裝，Visual c + +**，然後選取**Windows Desktop**。  

3. 在中央窗格中，選取**Windows Desktop 精靈**。  
  
4.  指定專案的名稱 — 例如， *MyExecRefsLib*— 在**名稱** 方塊中。 在 [方案] 旁邊的下拉式清單中，選取 [加入至方案] 。 這樣會將新專案加入含有靜態程式庫的方案中。 選擇 [確定]  按鈕。  
5. 底下**應用程式類型**，選取**主控台應用程式 (.exe)**。

6. 底下**Additioal 選項**，取消核取**先行編譯標頭**核取方塊。

7. 選擇**確定**建立專案。  
  
##  <a name="UseLibInApp"></a> 靜態程式庫的應用程式中使用的功能  
  
### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在應用程式中使用靜態程式庫的功能  
  
1.  建立主控台應用程式之後，系統會自動為您建立空白程式。 原始程式檔的名稱與您先前選擇的名稱相同。 在本範例中，其名稱為 **MyExecRefsLib.cpp**。  
  
2.  您必須先參考數學常式，才能在靜態程式庫中使用它。 若要這樣做，開啟 MyExecRefsLib 專案中的捷徑功能表**方案總管**，然後選擇**新增** > **參考**。  
  
3.  [加入參考]  對話方塊會列出您可以參考的程式庫。 [專案]  索引標籤會列出目前方案中的專案，以及這些專案含有的任何程式庫。 在 [專案]  索引標籤上，選取 [MathFuncsLib]  核取方塊，然後選擇 [確定]  按鈕。  
  
4.  若要參考 **MathFuncsLib.h** 標頭檔，您必須修改包含的目錄路徑。 在 **MyExecRefsLib** 的 [屬性頁] 對話方塊中，依序展開 [組態屬性]  節點、[C/C++]  節點，然後選取 [一般] 。 在 [其他 Include 目錄] 旁邊，指定 **MathFuncsLib** 目錄的路徑或瀏覽至其位置。  
  
     若要瀏覽至目錄路徑，請開啟屬性值下拉式清單，然後選擇 [編輯] 。 在 **其他 Include 目錄**對話方塊中，在文字方塊中，選取空白行，然後選擇 省略符號按鈕 (**...**) 結尾的行。 在 [選取目錄]  對話方塊中，選取 **MathFuncsLib** 目錄，然後選擇 [選取資料夾]  按鈕以儲存選取項目並關閉對話方塊。 在 [其他 Include 目錄]  對話方塊中，選擇 [確定]  按鈕，然後在 [屬性頁]  對話方塊中選擇 [確定]  按鈕，將您的變更儲存至專案。  
  
5.  您現在可以在這個應用程式中使用 **MyMathFuncs** 類別。 若要這樣做，請以下列程式碼取代 **MyExecRefsLib.cpp** 的內容：  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]  
  
6.  選擇來建立可執行檔**建置** > **建置方案**功能表列上。  
  
##  <a name="RunApp"></a> 執行應用程式  
  
### <a name="to-run-the-app"></a>執行應用程式  
  
1.  在方案總管  中開啟 **MyExecRefsLib** 的捷徑功能表，然後選擇 [設定為啟始專案] ，確定已選取 **MyExecRefsLib**做為預設專案。  
  
2.  若要執行專案，在功能表列上，選擇**偵錯** > **啟動但不偵錯**。 輸出應該會與以下相似：  
  
    ```Output  
    a + b = 106.4  
    a - b = -91.6  
    a * b = 732.6  
    a / b = 0.0747475  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：建立和使用動態連結程式庫 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [傳統型應用程式 (Visual C++)](../windows/desktop-applications-visual-cpp.md)