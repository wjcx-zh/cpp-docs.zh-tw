---
title: "逐步解說：建立和使用動態連結程式庫 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 逐步解說"
  - "程式庫 [C++], DLL"
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
caps.latest.revision: 36
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：建立和使用動態連結程式庫 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本逐步解說示範如何建立搭配 C\+\+ 應用程式使用的動態連結程式庫 \(DLL\)。  使用程式庫是重複使用程式碼的好方法。  無需在您建立的每一個程式中，重新實作相同的常式，您只要撰寫常式一次，然後從需要該功能的應用程式中參考它們即可。  透過將程式碼放入 DLL，您可以節省參考該 DLL 之每一個應用程式中的空間，且您可以更新 DLL 而無需重新編譯所有應用程式。  如需 DLL 的詳細資訊，請參閱 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)。  
  
 這份逐步解說涵蓋下列工作：  
  
-   建立 DLL 專案。  
  
-   將類別加入至 DLL。  
  
-   建立主控台應用程式，其使用載入時間動態連結，來參考 DLL。  
  
-   透過應用程式中的類別使用該功能。  
  
-   執行應用程式。  
  
 此逐步解說會建立僅可以從使用 C\+\+ 呼叫慣例之應用程式呼叫的 DLL。  如需如何建立 DLL 以與其他語言搭配使用的詳細資訊，請參閱[從 Visual Basic 應用程式中呼叫 DLL 函式](../build/calling-dll-functions-from-visual-basic-applications.md)。  
  
## 必要條件  
 本主題假設您已了解 C\+\+ 語言的基本概念。  
  
### 建立動態連結程式庫 \(DLL\) 專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊的左窗格中，依序展開 \[**已安裝的**\]、\[**範本**\]、\[**Visual C\+\+**\]，然後選取 \[**Win32**\]。  
  
3.  在中央窗格中，選取 \[**Win32 主控台應用程式**\]。  
  
4.  在 \[名稱\] 方塊中指定專案的名稱，例如 MathFuncsDll。  在 \[方案名稱\] 方塊中指定方案的名稱，例如 DynamicLibrary。  選擇 \[**確定**\] 按鈕。  
  
5.  在 \[**Win32 應用程式精靈**\] 對話方塊的 \[**概觀**\] 頁上選擇 \[**下一步**\] 按鈕。  
  
6.  在 \[應用程式設定\] 頁面的 \[應用程式類型\] 下，選取 \[DLL\]。  
  
7.  選擇 \[**完成**\] 按鈕以建立專案。  
  
### 將類別加入至動態連結程式庫  
  
1.  若要針對新類別建立標頭檔，請選擇 \[專案\]、\[加入新項目\]。  在 \[**加入新項目**\] 對話方塊的左窗格中，選取 \[**Visual C\+\+**\] 底下的 \[**程式碼**\]。  在中間窗格中，選取 \[**標頭檔 \(.h\)**\]。  指定標頭檔的名稱 \(例如，MathFuncsDll.h\)，然後選擇 \[加入\] 按鈕。  空白標頭檔會顯示。  
  
2.  將下面的程式碼加入至標頭檔的開頭：  
  
     [!code-cpp[NVC_Create_DLL_Walkthrough#100](../build/codesnippet/CPP/walkthrough-creating-and-using-a-dynamic-link-library-cpp_1.h)]  
  
3.  加入要執行一般算術運算 \(例如加法、減法、乘法和除法\) 的基本類別，名稱為 MyMathFuncs。  程式碼應該會與以下相似：  
  
     [!code-cpp[NVC_Create_DLL_Walkthrough#101](../build/codesnippet/CPP/walkthrough-creating-and-using-a-dynamic-link-library-cpp_2.h)]  
  
     當定義 MATHFUNCSDLL\_EXPORTS 符號時，MATHFUNCSDLL\_API 符號會在此程式碼的成員函式宣告中，設定 `__declspec(dllexport)` 修飾詞。  此修飾詞會啟用要由 DLL 匯出的函式，以便可供其他應用程式使用。  當未定義 MATHFUNCSDLL\_EXPORTS 時 \(例如，當某應用程式包含標頭檔時\)，MATHFUNCSDLL\_API 會在成員函式宣告中定義 `__declspec(dllimport)` 修飾詞。  此修飾詞會最佳化應用程式中函式的匯入。  根據預設，DLL 的 \[新建專案\] 範本會將 `PROJECTNAME`\_EXPORTS 加入至 DLL 專案的已定義符號。  在此範例中，當建置 MathFuncsDll 專案時，會定義 MATHFUNCSDLL\_EXPORTS。  如需詳細資訊，請參閱[dllexport、dllimport](../cpp/dllexport-dllimport.md)。  
  
    > [!NOTE]
    >  如果您在命令列上建置 DLL 專案，請使用 **\/D** 編譯器選項，來定義 MATHFUNCSDLL\_EXPORTS 符號。  
  
4.  在 \[方案總管\] 的 \[MathFuncsDll\] 專案中，於 \[原始程式檔\] 資料夾內，開啟 MathFuncsDll.cpp。  
  
5.  實作原始程式檔中 MyMathFuncs 的功能。  程式碼應該會與以下相似：  
  
     [!code-cpp[NVC_Create_DLL_Walkthrough#110](../build/codesnippet/CPP/walkthrough-creating-and-using-a-dynamic-link-library-cpp_3.cpp)]  
  
6.  在功能表列上選擇 \[建置\]、\[建置方案\]，以編譯動態連結程式庫。  
  
    > [!NOTE]
    >  如果您使用的 Express 版未顯示 \[建置\] 功能表，請在功能表列上，選擇 \[工具\]、\[設定\]、\[專家設定\] 啟用它，然後選擇 \[建置\]、\[建置方案\]。  
  
    > [!NOTE]
    >  如果您在命令列上建置專案，請使用 **\/LD** 編譯器選項，來指定該輸出檔要作為 DLL。  如需詳細資訊，請參閱[\/MD、\/MT、\/LD \(使用執行階段程式庫\)](../build/reference/md-mt-ld-use-run-time-library.md)。  使用 **\/EHsc** 編譯器選項，來啟用 C\+\+ 例外狀況處理。  如需詳細資訊，請參閱[\/EH \(例外狀況處理模型\)](../build/reference/eh-exception-handling-model.md)。  
  
### 建立參考 DLL 的應用程式  
  
1.  若要建立將參考及使用您剛剛所建立之 DLL 的 C\+\+ 應用程式，請在功能表列上，選擇 \[檔案\]、\[開新檔案\]、\[專案\]。  
  
2.  在左窗格中，選取 \[**Visual C\+\+**\] 下方的 \[**Win32**\]。  
  
3.  在中央窗格中，選取 \[**Win32 主控台應用程式**\]。  
  
4.  在 \[名稱\] 方塊中指定專案的名稱，例如 MyExecRefsDll。  在 \[方案\] 旁邊的下拉式清單中，選取 \[加入至方案\]。  這樣會將新專案加入至含有 DLL 的相同方案中。  選擇 \[**確定**\] 按鈕。  
  
5.  在 \[**Win32 應用程式精靈**\] 對話方塊的 \[**概觀**\] 頁上選擇 \[**下一步**\] 按鈕。  
  
6.  在 \[**應用程式設定**\] 頁面的 \[**應用程式類型**\] 下，選取 \[**主控台應用程式**\]。  
  
7.  在 \[**應用程式設定**\] 頁面的 \[**其他選項**\] 下，清除 \[**先行編譯標頭檔**\] 核取方塊。  
  
8.  選擇 \[**完成**\] 按鈕以建立專案。  
  
### 在應用程式中使用類別程式庫的功能  
  
1.  建立主控台應用程式之後，就會自動為您建立空白程式。  原始程式檔的名稱與您先前選擇的名稱相同。  在本範例中，它會命名為 MyExecRefsDll.cpp。  
  
2.  若要在應用程式中使用您在 DLL 中建立的數學常式，您必須對其進行參考。  若要這樣做，請在 \[方案總管\] 中，選取 MyExecRefsDll 專案，然後在功能表列上，選擇 \[專案\]、\[參考\]。  在 \[屬性頁\] 對話方塊中，展開 \[通用屬性\] 節點，選取 \[架構和參考\]，然後選擇 \[加入新參考\] 按鈕。  如需 \[**參考**\] 對話方塊的詳細資訊，請參閱[加入參考](../ide/adding-references-in-visual-cpp-projects.md)。  
  
3.  \[**加入參考**\] 對話方塊會列出您可以參考的程式庫。  \[專案\] 索引標籤會列出目前方案中的專案，以及這些專案含有的任何程式庫。  在 \[專案\] 索引標籤上，選取 \[MathFuncsDll\] 旁邊的核取方塊，然後選擇 \[確定\] 按鈕。  
  
4.  若要參考 DLL 的標頭檔，您必須修改包含的目錄路徑。  如要這樣做，請在 \[屬性頁\] 對話方塊中，依序展開 \[組態屬性\] 節點、\[C\/C\+\+\] 節點，然後選取 \[一般\]。  在 \[其他 Include 目錄\] 旁邊，指定 MathFuncsDll.h 標頭位置的路徑。  您可以使用相對路徑，例如 ..\\MathFuncsDll\\，然後選擇 \[確定\] 按鈕。  
  
5.  您現在可以在這個應用程式中使用 MyMathFuncs 類別。  將 MyExecRefsDll.cpp 的內容取代為下列程式碼：  
  
     [!code-cpp[NVC_Create_DLL_Walkthrough#120](../build/codesnippet/CPP/walkthrough-creating-and-using-a-dynamic-link-library-cpp_4.cpp)]  
  
6.  選擇功能表列上的 \[**建置**\]、\[**建置方案**\]，以建置可執行檔。  
  
### 若要執行應用程式  
  
1.  確保將 MyExecRefsDll 選取為預設專案。  在 \[方案總管\] 中，選取 MyExecRefsDll，然後在功能表列上選擇 \[專案\]、\[設定為啟始專案\]。  
  
2.  若要執行專案，請在功能表列上選擇 \[**偵錯**\]、\[**啟動但不偵錯**\]。  輸出應該會與以下相似：  
  
  **a \+ b \= 106.4**  
**a \- b \= \-91.6**  
**a \* b \= 732.6**  
**a \/ b \= 0.0747475**  
**攔截到例外狀況：b 不能為零！**  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)   
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [逐步解說：部署程式 \(C\+\+\)](../ide/walkthrough-deploying-your-program-cpp.md)   
 [從 Visual Basic 應用程式中呼叫 DLL 函式](../build/calling-dll-functions-from-visual-basic-applications.md)