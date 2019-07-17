---
title: 逐步解說：建立並使用您自己的動態連結程式庫 (C++)
description: 在 Visual Studio 中使用 C++ 建立 Windows 動態連結程式庫 (DLL)。
ms.custom: conceptual
ms.date: 07/17/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 8ca89471177ba2d1fa98bfaf51b86ed15dcd6d2f
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299816"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>逐步解說：建立並使用您自己的動態連結程式庫 (C++)

此逐步解說示範如何使用 Visual Studio IDE 來建立您自己的動態連結程式庫 (DLL) (以 C++ 撰寫)，並從另一個 C++ 應用程式使用。 DLL (也就是 UNIX 型作業系統中的共用程式庫) 是其中一種最有用的 Windows 元件。 您可以將其用於共用程式碼和資源，來縮減您的應用程式大小，並讓您的應用程式變得更容易服務與擴充。 在本逐步解說中，您會建立 DLL 來實作一些數學函式，再建立會從 DLL 使用函式的主控台應用程式。 在過程中，您會初步了解一些用於 Windows DLL 的程式設計技術和慣例。

這份逐步解說涵蓋下列工作：

- 在 Visual Studio 中建立 DLL 專案。

- 將匯出的函式和變數新增至 DLL。

- 在 Visual Studio 中建立主控台應用程式專案。

- 在主控台應用程式中使用從 DLL 匯入的函式與變數。

- 執行已完成的應用程式。

如同靜態連結程式庫，DLL 會依名稱「匯出」  變數、函式和資源，且您的應用程式會「匯入」  這些名稱以使用這些變數、函式和資源。 與靜態連結程式庫不同，Windows 會在載入時或在執行階段將應用程式中的匯入連線至 DLL 中的匯出，而不是在連結時將其連線。 Windows 需要不屬於標準 C++ 編譯模型一部分的額外資訊來建立這些連線。 MSVC 編譯器會將一些 Microsoft 特定的延伸模組實作於 C++，以提供這些額外資訊。 我們會逐步說明這些延伸模組。

此逐步解說會建立兩個 Visual Studio 方案；一個是建置 DLL，另一個是建置用戶端應用程式。 DLL 會使用 C 呼叫慣例，因此可以從使用其他語言建置的應用程式來呼叫，只要平台和呼叫與連結慣例相符即可。 用戶端應用程式會使用「隱含連結」  ，其中 Windows 會在載入時將應用程式連結到 DLL。 如同靜態連結程式庫中的函式，此連結可讓應用程式呼叫 DLL 提供的函式。

本逐步解說不涵蓋某些常見的情況。 不會示範其他程式設計語言的 C++ DLL 使用方式。 不會示範如何建立僅限資源的 DLL。 也不會顯示在執行階段 (而非載入時) 載入 DLL 的明確連結使用方式。 請放心, 您可以使用 Visual Studio 來執行所有這些動作。 如需 DLL 的詳細資訊連結，請參閱[在 Visual Studio 中建立 C/C++ DLL](dlls-in-visual-cpp.md)。 如需隱含連結和明確連結的詳細資訊，請參閱[判斷要使用哪一種連結方法](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。 如需建立 C++ DLL 以與使用 C 語言連結之慣例程式設計語言搭配使用的資訊，請參閱[匯出 C++ 函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)。 如需如何建立 DLL 以與 .NET 語言搭配使用的資訊，請參閱[從 Visual Basic 應用程式呼叫 DLL 函式](calling-dll-functions-from-visual-basic-applications.md)。

## <a name="prerequisites"></a>必要條件

- 執行 Microsoft Windows 7 或更新版本的電腦。 建議使用 Windows 10 以獲得最佳開發體驗。

- Visual Studio 的複本。 如需如何下載並安裝 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。 當您執行安裝程式時，請確認已選取**使用 C++ 的桌面開發**工作負載。 如果您在安裝 Visual Studio 時未安裝此工作負載，也不用擔心。 您可以再次執行安裝程式並立即安裝。

   ![使用 C++ 的桌面開發](media/desktop-development-with-cpp.png "使用 C++ 的桌面開發")

- 了解使用 Visual Studio IDE 的基本概念。 如果您先前使用過 Windows 傳統型應用程式，您應能輕鬆跟上。 如需簡介，請參閱 [Visual Studio IDE 功能導覽](/visualstudio/ide/visual-studio-ide)。

- 了解足夠的 C++ 語言基本概念。 別擔心，我們不會進行太複雜的操作。

## <a name="create-the-dll-project"></a>建立 DLL 專案

在這組工作中，您可以為您的 DLL 建立專案、新增程式碼及加以建置。 首先請啟動 Visual Studio IDE，並根據您的需要登入。 指示會依您使用的 Visual studio 版本而略有不同。 請確認您在本頁面左上角的控制項中選取正確版本。

::: moniker range="=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立 DLL 專案

1. 在功能表列上，選擇 [檔案]  > [新增]  > [專案]  ，以開啟 [建立新專案]  對話方塊。

   ![建立新的 DLL 專案](media/create-new-dll-project-2019.png "建立 MathLibrary 專案")

1. 在對話方塊頂端，將 [語言]  設定為 **C++** ，將 [平台]  設定為 **Windows**，並將 [專案類型]  設定為**程式庫**。 

1. 從專案類型的篩選清單中選擇 [動態連結程式庫 (DLL)]  ，然後選擇 [下一步]  。 在下一頁的 [名稱]  方塊中輸入 `MathLibrary` 以指定專案名稱，並依照需要指定專案位置。

1. 選擇 [建立]  按鈕以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中建立 DLL 專案

1. 在功能表列上，選擇 [檔案]  > [新增]  > [專案]  ，以開啟 [新增專案]  對話方塊。

1. 在 [新增專案]  對話方塊的左窗格中，展開 [已安裝]  和 [Visual C++]  (若需要)，然後選擇 [Windows Desktop]  。 在中央窗格中，選取 [Windows 傳統型精靈]  。 在 [名稱]  文字方塊中輸入 `MathLibrary` 以指定專案的名稱。

   ![為 MathLibrary 專案命名](media/mathlibrary-new-project-name-153.png "為 MathLibrary 專案命名")

1. 選擇 [確定]  按鈕以關閉 [新增專案]  對話方塊，並啟動 [Windows 傳統型專案精靈]  。

1. 在 [Windows 傳統型專案精靈]  的 [應用程式類型]  下方，選取 [動態連結程式庫 (.dll)]  。

   ![在 [Windows 傳統型專案精靈] 中建立 DLL](media/mathlibrary-desktop-project-wizard-dll.png "在 [Windows 傳統型專案精靈] 中建立 DLL")

1. 選擇 [確定]  按鈕以建立專案。

> [!NOTE]
> 需採取額外步驟才能修正 Visual Studio 2017 15.3 版中的問題。 請遵循下列指示來查看是否需要進行這項變更。
>
>1. 在 [方案總管]  中，選取 [方案 'MathLibrary']  下方的 [MathLibrary]  (若尚未選取)。
>
>1. 在功能表列上，依序選擇 [專案]  > [屬性]  。
>
>1. 在 [屬性頁]  對話方塊的左窗格中，選取 [組態屬性]   > [C/C++]  下方的 [前置處理器]  。 請檢查**前置處理器定義**屬性的內容。<br/><br/>![檢查前置處理器定義屬性](media/mathlibrary-153bug-preprocessor-definitions-check.png "檢查前置處理器定義屬性")<br/><br/>如果您在**前置處理器定義**清單中看到 **MATHLIBRARY&#95;EXPORTS**，您就不需要變更任何項目。 但如果您看到 **MathLibrary&#95;EXPORTS**，則繼續進行下列步驟。
>
>1. 在 [屬性頁]  對話方塊頂端，將 [組態]  下拉式清單變更為 [所有組態]  。
>
>1. 在屬性窗格中，針對編輯方塊旁的下拉式清單控制項，選取 [前置處理器定義]  ，然後選擇 [編輯]  。<br/><br/>![編輯前置處理器定義屬性](media/mathlibrary-153bug-preprocessor-definitions-property.png "編輯前置處理器定義屬性")
>
>1. 在 [前置處理器定義]  對話方塊的上方窗格中，新增新的符號 `MATHLIBRARY_EXPORTS`。<br/><br/>![新增 MATHLIBRARY_EXPORTS 符號](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "新增 MATHLIBRARY_EXPORTS 符號")
>
>1. 選擇 [確定]  以關閉 [前置處理器定義]  對話方塊，然後選擇 [確定]  以將您的變更儲存至專案屬性。

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>在較舊版本的 Visual Studio 中建立 DLL 專案

1. 在功能表列上，選擇 [檔案]  > [新增]  > [專案]  。

1. 在 [新增專案]  對話方塊的左窗格中，展開 [已安裝]   > [範本]  並選取 [Visual C++]  ，然後在中央窗格中選取 [Win32 主控台應用程式]  。 在 [名稱]  編輯方塊中輸入 `MathLibrary` 以指定專案的名稱。

   ![為 MathLibrary 專案命名](media/mathlibrary-project-name.png "為 MathLibrary 專案命名")

1. 選擇 [確定]  按鈕以關閉 [新增專案]  對話方塊，並啟動 [Win32 應用程式精靈]  。

   ![[Win32 應用程式精靈] 概觀](media/mathlibrary-project-wizard-1.png "[Win32 應用程式精靈] 概觀")

1. 選擇 [下一步]  按鈕。 在 [應用程式設定]  頁面的 [應用程式類型]  下，選取 [DLL]  。

   ![在 [Win32 應用程式精靈] 中建立 DLL](media/mathlibrary-project-wizard-2.png "在 [Win32 應用程式精靈] 中建立 DLL")

1. 選擇 [完成]  按鈕以建立專案。

精靈完成方案後，您可以在 Visual Studio 的 [方案總管]  視窗中，看到產生的專案和來源檔案。

![在 Visual Studio 中產生的方案](media/mathlibrary-solution-explorer-153.png "在 Visual Studio 中產生的方案")

目前，此 DLL 還不能做太多事。 接下來，請建立標頭檔來宣告 DLL 匯出的函式，然後將函式定義新增至 DLL，使其更加實用。

::: moniker-end

### <a name="to-add-a-header-file-to-the-dll"></a>將標頭檔新增至 DLL

1. 若要為您的函式建立標頭檔，請在功能表列選擇 [專案]   > [新增項目]  。

1. 在 [新增項目]  對話方塊的左窗格中，選取 [Visual C++]  。 在中間窗格中，選取 [標頭檔 (.h)]  。 指定 `MathLibrary.h` 作為標頭檔的名稱。

   ![在 [新增項目] 對話方塊中新增標頭](media/mathlibrary-add-new-item-header-file.png "在 [新增項目] 對話方塊中新增標頭")

1. 選擇 [新增]  按鈕以產生空白標頭檔，這會顯示在新的編輯器視窗中。

   ![編輯器中的空白 MathLibrary.h 檔案](media/edit-empty-mathlibrary-header.png "編輯器中的空白 MathLibrary.h 檔案")

1. 使用此程式碼來取代標頭檔的內容：

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

在具有兩個初始值的情況下，此標頭檔會宣告一些函式來產生一般化的 Fibonacci 序列。 對 `fibonacci_init(1, 1)` 的呼叫會產生熟悉的 Fibonacci 數字序列。

請注意檔案頂端的前置處理器陳述式。 根據預設，DLL 的新建專案範本會將 **\<em>PROJECTNAME\</em>&#95;EXPORTS** 新增至 DLL 專案的已定義前置處理器巨集。 在此範例中，當您的 MathLibrary DLL 專案完成建置時，Visual Studio 會定義 **MATHLIBRARY&#95;EXPORTS**。 

::: moniker range="=vs-2017"

(Visual Studio 2017 15.3 版中的精靈不會將此符號定義強制為大寫。 如果您將專案命名為 "MathLibrary"，則符號會定義為 MathLibrary&#95;EXPORTS，而不是 MATHLIBRARY&#95;EXPORTS。 這就是為什麼需要上述額外步驟來新增此符號。)

::: moniker-end

定義 **MATHLIBRARY&#95;EXPORTS** 巨集後，**MATHLIBRARY&#95;API** 巨集會在函式宣告中設定 `__declspec(dllexport)` 修飾詞。 此修飾詞會要求編譯器和連結器從 DLL 匯出函式或變數，以供其他應用程式使用。 如果 **MATHLIBRARY&#95;EXPORTS** 並未定義 (例如當用戶端應用程式包含標頭檔時)，則 **MATHLIBRARY&#95;API** 會將 `__declspec(dllimport)` 修飾詞套用至宣告。 此修飾詞會將應用程式中函式或變數的匯入最佳化。 如需詳細資訊，請參閱 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。

### <a name="to-add-an-implementation-to-the-dll"></a>將實作新增至 DLL

::: moniker range="vs-2019"

1. 在 [方案總管]  中，以滑鼠右鍵按一下 [來源檔案]  節點並新增稱為 `MathLibrary.cpp` 的新 .cpp 檔案，與您在上一個步驟中新增新標頭檔的方式相同。

::: moniker-end

1. 在編輯器視窗中，選取 [MathLibrary.cpp]  索引標籤 (如果已經開啟)。 如果尚未開啟，請在 [方案總管]  中，在 [MathLibrary]  專案的 [來源檔案]  資料夾中開啟 [MathLibrary.cpp]  。

1. 在編輯器中，以下列程式碼取代 MathLibrary.cpp 檔案的內容：

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

為了確認目前為止一切順利，請編譯動態連結程式庫。 在功能表列上選擇 [建置]   > [建置方案]  來編譯。 輸出應該會看起來像這樣。 請注意, DLL 可執行檔和相關編譯器輸出會放在 [方案] 資料夾正下方的資料夾中, 名為*Debug* 。 如果您建立發行組建, 輸出將會放在名為*Release*的資料夾中:

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

恭喜, 您已使用 Visual Studio 建立 DLL! 接下來，您將建立一個用戶端應用程式，該應用程式使用由 DLL 匯出的函式。

## <a name="create-a-client-app-that-uses-the-dll"></a>建立使用 DLL 的用戶端應用程式

當您建立 DLL 時，您必須思考可以如何使用您的 DLL。 若要編譯會呼叫由 DLL 匯出之函式的程式碼，用戶端原始程式碼必須包含宣告。 在連結時，當解析這些對 DLL 函式的呼叫時，連結器必須具有「匯入程式庫」  (特殊程式庫檔案)，其中包含如何尋找函式的 Windows 資訊，而非實際程式碼。 並且，在執行階段，DLL 必須可供用戶端使用，位於作業系統可以找到的位置。

若要利用 DLL (無論是您自己的 DLL 或第三方 DLL)，您的用戶端應用程式專案必須找到宣告 DLL 匯出的標頭、連結器的匯入程式庫與 DLL 本身。 其中一種方法是將所有這些檔案複製到您的用戶端專案中。 針對不太可能在您開發用戶端時變更的第三方 DLL，此方法可能是使用它們的最佳方法。 不過，如果您也要建置 DLL，則最好避免重複。 如果您複製正在開發的 DLL 檔案，您可能會不小心變更標頭檔的其中一個複本，但未變更另一個，或使用過時的程式庫。 為了避免這個問題，我們建議您在您的用戶端專案中設定 Include 路徑，以包含 DLL 專案中的 DLL 標頭檔。 此外，也在您的用戶端專案中設定程式庫路徑，以包含 DLL 專案中的 DLL 匯入程式庫。 最後，將從 DLL 專案中建置的 DLL 複製到組建輸出目錄。 此步驟可讓用戶端應用程式使用您所建置的相同 DLL 程式碼。

::: moniker range="vs-2019"

### <a name="to-create-a-client-app-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立用戶端應用程式

1. 在功能表列上，選擇 [檔案]  > [新增]  > [專案]  ，以開啟 [建立新專案]  對話方塊。

1. 在對話方塊頂端，將 [語言]  設定為 **C++** ，將 [平台]  設定為 **Windows**，並將 [專案類型]  設定為**主控台**。 

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]  ，然後選擇 [下一步]  。 在下一頁的 [名稱]  方塊中輸入 `MathClient` 以指定專案名稱，並依照需要指定專案位置。

   ![命名用戶端專案](media/mathclient-project-name-2019.png "命名用戶端專案")

1. 選擇 [建立]  按鈕以建立用戶端專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>在 Visual Studio 2017 中建立用戶端應用程式

1. 若要建立將使用您建立之 DLL 的 C++ 應用程式，請在功能表列上選擇 [檔案]  > [新增]  > [專案]  。

1. 在 [新增專案]  對話方塊左窗格中的 [已安裝]   > [Visual C++]  下方，選取 [Windows 傳統型]  。 在中央窗格中，選取 [Windows 傳統型精靈]  。 在 [名稱]  編輯方塊中指定專案名稱 `MathClient`。

   ![命名用戶端專案](media/mathclient-new-project-name-153.png "命名用戶端專案")

1. 選擇 [確定]  啟動 [Windows 傳統型專案精靈]  。 在精靈中，選擇 [確定]  以建立用戶端應用程式專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>在較舊版本的 Visual Studio 2017 中建立用戶端應用程式

1. 若要建立將使用您建立之 DLL 的 C++ 應用程式，請在功能表列上選擇 [檔案]  > [新增]  > [專案]  。

1. 在 [新增專案]  對話方塊左窗格中的 [已安裝]   > [範本]   > [Visual C++]  下方，選取 **Win32**。 在中央窗格中，選取 [Win32 主控台應用程式]  。 在 [名稱]  編輯方塊中指定專案名稱 `MathClient`。

   ![命名用戶端專案](media/mathclient-project-name.png "命名用戶端專案")

1. 選擇 [確定]  按鈕以關閉 [新增專案]  對話方塊，並啟動 [Win32 應用程式精靈]  。 在 [Win32 應用程式精靈]  對話方塊的 [概觀]  頁面上，選擇 [下一步]  按鈕。

1. 在 [應用程式設定]  頁面的 [應用程式類型]  下方，選取 [主控台應用程式]  (若尚未選取)。

1. 選擇 [完成]  按鈕以建立專案。

::: moniker-end

精靈完成時，會為您建立最基本的主控台應用程式專案。 主要來源檔案的名稱，與您先前輸入的名稱相同。 在此範例中，其名稱是 **MathClient.cpp**。 您可以建置該檔案，但該檔案尚不會使用您的 DLL。

接下來，為了在您的原始程式碼中呼叫 MathLibrary 函式，您的專案必須包含 MathLibrary.h 檔案。 您可以將此標頭檔複製到用戶端應用程式專案，然後將其新增至專案作為現有的項目。 這個方法對於第三方程式庫是理想選擇。 但是，如果您與用戶端同時處理 DLL 的程式碼，可能會導致標頭檔中的變更不會顯示於另一個標頭檔。 若要避免這個問題，您可以變更您專案中的**其他 Include 目錄**路徑，以包含原始標頭的路徑。

### <a name="to-add-the-dll-header-to-your-include-path"></a>將 DLL 標頭新增至您的 Include 路徑

1. 以滑鼠右鍵按一下 [方案總管]  中的 **MathClient** 節點以開啟 [屬性頁]  對話方塊。

1. 在 [組態]  下拉式清單方塊中，選取 [所有組態]  (若尚未選取)。

1. 在左窗格中，選取 [組態屬性]   > [C/C++]  下方的 [一般]  。

1. 在屬性窗格中，選取 [其他 Include 目錄]  編輯方塊旁的下拉式清單控制項，然後選擇 [編輯]  。

   ![編輯其他 Include 目錄屬性](media/mathclient-additional-include-directories-property.png "編輯其他 Include 目錄屬性")

1. 在上方窗格中按兩下 [其他 Include 目錄]  對話方塊以啟用編輯控制項。

1. 在編輯控制項中，指定 **MathLibrary.h** 標頭檔的位置路徑。 按一下向下箭號, 然後選擇 [  **\<編輯 >** ]。 您可以按一下資料夾圖示, 然後按省略號 ( **...** ) 流覽至正確的資料夾。
 
   您也可以在此情況下, 輸入在用戶端專案中包含 .cpp 檔案之資料夾的相對路徑, 以及 DLL 專案中包含 .h 檔案的資料夾。 如果用戶端專案位於與 DLL 方案相同資料夾的不同方案中，則相對路徑應如下所示：

   `..\MathLibrary\MathLibrary`

   如果您的 DLL 和用戶端專案位於相同的方案中, 或方案位於不同的資料夾中, 則您必須據以調整相對路徑, 或使用先前所述的方法流覽資料夾。

   ![將標頭位置新增至其他 Include 目錄屬性](media/mathclient-additional-include-directories.png "將標頭位置新增至其他 Include 目錄屬性")

1. 在 [**其他 Include 目錄**] 對話方塊中輸入標頭檔的路徑之後, 請選擇 [**確定]** 按鈕以返回 [**屬性頁**] 對話方塊, 然後選擇 [**確定]** 按鈕以儲存變更。

您現在可以包含 **MathLibrary.h** 檔案，並使用其在用戶端應用程式中宣告的函式。 使用此程式碼取代 **MathClient.cpp** 的內容：

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

此程式碼可以編譯，但不可連結，因為連結器找不到建置應用程式所需的匯入程式庫。 連結器必須找到 MathLibrary.lib 檔案以成功連結。 設定 [其他相依性]  屬性，將 MathLibrary.lib 檔案新增至組建。 同樣地，您可以將程式庫檔案複製到您的用戶端應用程式專案，但如果程式庫和用戶端應用程式仍在開發中，可能會導致某複本的變更不會顯示在另一個複本中。 若要避免這個問題，您可以變更您專案中的 [其他程式庫目錄]  路徑，以在您連結時包含原始程式庫的路徑。

### <a name="to-add-the-dll-import-library-to-your-project"></a>將 DLL 匯入程式庫新增至您的專案

1. 以滑鼠右鍵按一下 [方案總管]  中的 **MathClient** 節點以開啟 [屬性頁]  對話方塊。

1. 在 [組態]  下拉式清單方塊中，選取 [所有組態]  (若尚未選取)。 此設定可確保將路徑設定用於偵錯與發行組建。

1. 在左窗格中，選取 [組態屬性]   > [連結器]  下方的 [輸入]  。 在屬性窗格中，選取 [其他相依性]  編輯方塊旁的下拉式清單控制項，然後選擇 [編輯]  。

   ![編輯 [其他相依性] 屬性](media/mathclient-additional-dependencies-property.png "編輯 [其他相依性] 屬性")

1. 在 [其他相依性]  對話方塊中，將 `MathLibrary.lib` 新增至上方編輯控制項的清單中。

   ![新增程式庫相依性](media/mathclient-additional-dependencies.png "新增程式庫相依性")

1. 選擇 [確定]  返回 [屬性頁]  對話方塊。

1. 在左窗格中，選取 [組態屬性]   > [連結器]  下方的 [一般]  。 在屬性窗格中，選取 [其他程式庫目錄]  編輯方塊旁的下拉式清單控制項，然後選擇 [編輯]  。

   ![編輯 [其他程式庫目錄] 屬性](media/mathclient-additional-library-directories-property.png "編輯 [其他程式庫目錄] 屬性")

1. 在 [其他程式庫目錄]  對話方塊的上方窗格中按兩下以啟用編輯控制項。 在編輯控制項中，指定 **MathLibrary.lib** 檔案的位置路徑。 它位於您方案資料夾下`Debug`的直接名為的資料夾中。 如果您建立發行組建, 輸出將會放在名`Release`為的資料夾中。 您可以使用下列宏, 讓連結器可以找到您的 DLL, 而不論您所建立的組建種類為何:

   **Visual Studio 2019:**

   `..\MathLibrary\$(IntDir)`

   **Visual Studio 2017 和更早版本:**

   `..\..\MathLibrary\$(IntDir)`

   ![新增程式庫目錄](media/mathclient-additional-library-directories.png "新增程式庫目錄")

1. 一旦您在 [其他程式庫目錄]  對話方塊中輸入程式庫檔案的路徑，請選擇 [確定]  按鈕返回 [屬性頁]  對話方塊。

您的用戶端應用程式現在可以編譯並成功連結，但仍不具備執行所需的所有項目。 當作業系統載入您的應用程式時，會尋找 MathLibrary DLL。 如果作業系統無法在特定系統目錄、環境路徑或本機應用程式目錄中找到該 DLL，則載入將會失敗。 避免此問題之其中一個方法是將 DLL 複製到包含用戶端可執行檔的目錄，作為建置程序的一部分。 若要複製 DLL，您可以將**建置後事件**新增至您的專案，以新增會將 DLL 複製到建置輸出目錄的命令。 此處指定的命令只會在 DLL 遺失或已變更時複製 DLL，並使用巨集複製到組態的正確偵錯或發行位置 (或從該位置複製)。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>在建置後事件中複製 DLL

1. 以滑鼠右鍵按一下 [方案總管]  中的 **MathClient** 節點以開啟 [屬性頁]  對話方塊。

1. 在 [組態] 下拉式清單方塊中，選取 [所有組態]  (若尚未選取)。

1. 在左窗格中，選取 [組態屬性]   > [建置事件]  下方的 [建置後事件]  。

1. 在屬性窗格中，選取 [命令列]  欄位中的編輯控制項，然後輸入此命令：

   **Visual Studio 2019:**

   `xcopy /y /d "..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

    **Visual Studio 2017 和更早版本:**

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![新增建置後命令](media/mathclient-post-build-command-line.png "新增建置後命令")

1. 選擇 [確定]  按鈕，儲存您對專案屬性進行的變更。

現在您的用戶端應用程式已具備建置與執行所需所有項目。 選擇功能表列上的 [建置]   > [建置方案]  以建置應用程式。 Visual Studio 中的 [**輸出**] 視窗應該會有類似下列範例的內容, 視您的 Visual Studio 版本而定:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

恭喜，您已建立可在 DLL 中呼叫函式的應用程式。 現在，執行您的應用程式以查看其功能。 在功能表列上，依序選擇 [偵錯]   > [啟動但不偵錯]  。 Visual Studio 會開啟命令視窗，供程式執行。 輸出的最後一部分看起來應該如下所示：

![啟動用戶端應用程式但不偵錯](media/mathclient-run-without-debugging.png "啟動用戶端應用程式但不偵錯")

按任意鍵以關閉命令視窗。

您已建立 DLL 和用戶端應用程式，現在您可以進行實驗。 請嘗試在用戶端應用程式的程式碼中設定中斷點，並在偵錯工具中執行應用程式。 查看當您逐步執行程式庫呼叫時會發生什麼事。 將其他函式新增至程式庫，或撰寫可使用您 DLL 的另一個用戶端應用程式。

部署您的應用程式時，您也必須部署其使用的 DLL。 讓應用程式可以使用您建置的 DLL (或您從第三方取得的 DLL)，最簡單的方法是將其放在與應用程式相同的目錄中，也稱為「應用程式本機部署」  。 如需部署的詳細資訊，請參閱 [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[從 Visual Basic 應用程式呼叫 DLL 函式](calling-dll-functions-from-visual-basic-applications.md)
