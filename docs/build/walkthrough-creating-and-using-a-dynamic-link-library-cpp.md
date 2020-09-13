---
title: '逐步解說：建立和使用您自己的動態連結程式庫 (c + +) '
description: 在 Visual Studio 中使用 C++ 建立 Windows 動態連結程式庫 (DLL)。
ms.custom: conceptual
ms.date: 08/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: adca441a1b1b4e5e7b7efa44c4a292a8f1ddec35
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042195"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>逐步解說：建立和使用您自己的動態連結程式庫 (c + +) 

本逐步解說將示範如何使用 Visual Studio IDE 來建立您自己的動態連結程式庫 (DLL) 以 Microsoft c + + (MSVC) 撰寫。 然後，它會顯示如何從另一個 c + + 應用程式使用 DLL。 Dll (也稱為 UNIX 作業系統中的 *共用程式庫*) 是其中一種最有用的 Windows 元件。 您可以使用它們作為共用程式碼和資源的方式，並縮減應用程式的大小。 Dll 甚至可以讓您更輕鬆地服務及擴充您的應用程式。

在這個逐步解說中，您將建立可執行一些數學函數的 DLL。 然後，您將建立主控台應用程式，該應用程式會使用來自 DLL 的函式。 您也將瞭解 Windows Dll 中使用的一些程式設計技巧和慣例。

這份逐步解說涵蓋下列工作：

- 在 Visual Studio 中建立 DLL 專案。

- 將匯出的函式和變數新增至 DLL。

- 在 Visual Studio 中建立主控台應用程式專案。

- 在主控台應用程式中使用從 DLL 匯入的函式與變數。

- 執行完成的應用程式。

如同靜態連結的程式庫，DLL 會依名稱 _匯出_ 變數、函式和資源。 用戶端應用程式會匯 _入_ 名稱以使用這些變數、函式和資源。 與靜態連結程式庫不同，Windows 會在載入時或在執行階段將應用程式中的匯入連線至 DLL 中的匯出，而不是在連結時將其連線。 Windows 需要不屬於標準 C++ 編譯模型一部分的額外資訊來建立這些連線。 MSVC 編譯器會將一些 Microsoft 特定的延伸模組實作於 C++，以提供這些額外資訊。 我們會逐步說明這些延伸模組。

此逐步解說會建立兩個 Visual Studio 方案；一個是建置 DLL，另一個是建置用戶端應用程式。 DLL 會使用 C 呼叫慣例。 您可以從以其他程式設計語言撰寫的應用程式呼叫它，只要平臺、呼叫慣例和連結慣例相符即可。 用戶端應用程式會使用「隱含連結」__，其中 Windows 會在載入時將應用程式連結到 DLL。 如同靜態連結程式庫中的函式，此連結可讓應用程式呼叫 DLL 提供的函式。

本逐步解說不涵蓋某些常見的情況。 程式碼不會顯示其他程式設計語言使用 c + + Dll。 它不會示範如何 [建立僅含資源的 DLL](creating-a-resource-only-dll.md)，或如何在執行時間使用 [明確連結](linking-an-executable-to-a-dll.md#linking-explicitly) 來載入 dll，而不是在載入時使用。 請放心，您可以使用 MSVC 和 Visual Studio 來執行上述所有作業。

如需 DLL 的詳細資訊連結，請參閱[在 Visual Studio 中建立 C/C++ DLL](dlls-in-visual-cpp.md)。 如需隱含連結和明確連結的詳細資訊，請參閱 [判斷要使用哪一個連結方法](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。 如需有關建立 c + + Dll 以搭配使用 C 語言連結慣例之程式設計語言的詳細資訊，請參閱 [匯出 c + + 函式以用於 c 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)。 如需如何建立 DLL 以與 .NET 語言搭配使用的資訊，請參閱[從 Visual Basic 應用程式呼叫 DLL 函式](calling-dll-functions-from-visual-basic-applications.md)。

## <a name="prerequisites"></a>必要條件

- 執行 Microsoft Windows 7 或更新版本的電腦。 建議使用 Windows 10 以獲得最佳開發體驗。

::: moniker range=">=vs-2017"

- Visual Studio 的複本。 如需如何下載並安裝 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。 當您執行安裝程式時，請確認已選取**使用 C++ 的桌面開發**工作負載。 如果您在安裝 Visual Studio 時未安裝此工作負載，也不用擔心。 您可以再次執行安裝程式並立即安裝。

   ![使用 C++ 開發桌面](media/desktop-development-with-cpp.png "使用 C++ 的傳統型開發")

::: moniker-end

::: moniker range="vs-2015"

- Visual Studio 的複本。 如需有關如何下載及安裝 Visual Studio 2015 的詳細資訊，請參閱 [安裝 Visual Studio 2015](/visualstudio/install/install-visual-studio-2015?view=vs-2015&preserve-view=true)。 您可以使用 **自訂** 安裝來安裝 c + + 編譯器和工具，因為預設不會安裝它們。

::: moniker-end

- 了解使用 Visual Studio IDE 的基本概念。 如果您先前使用過 Windows 傳統型應用程式，您應能輕鬆跟上。 如需簡介，請參閱 [Visual Studio IDE 功能導覽](/visualstudio/ide/visual-studio-ide)。

- 了解足夠的 C++ 語言基本概念。 別擔心，我們不會進行太複雜的操作。

::: moniker range="vs-2017"

> [!NOTE]
> 本逐步解說假設您使用的是 Visual Studio 2017 15.9 版或更新版本。 某些舊版的 Visual Studio 2017 在程式碼範本中有瑕疵，或使用不同的使用者介面對話方塊。 若要避免問題，請使用 Visual Studio 安裝程式將 Visual Studio 2017 更新至15.9 版或更新版本。

::: moniker-end

## <a name="create-the-dll-project"></a>建立 DLL 專案

在這組工作中，您可以為您的 DLL 建立專案、新增程式碼及加以建置。 首先請啟動 Visual Studio IDE，並根據您的需要登入。 這些指示會根據您所使用的 Visual Studio 版本而稍有不同。 請確認您在本頁面左上角的控制項中選取正確版本。

::: moniker range=">=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立 DLL 專案

1. 在功能表列上，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

   ![建立新的 DLL 專案](media/create-new-dll-project-2019.png "建立 MathLibrary 專案")

1. 在對話方塊頂端，將 [語言]**** 設定為 **C++**，將 [平台]**** 設定為 **Windows**，並將 [專案類型]**** 設定為**程式庫**。

1. 從專案類型的篩選清單中，選取 [ **動態連結程式庫] (DLL) **，然後選擇 **[下一步]**。

1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中輸入*MathLibrary* ，以指定專案的名稱。 保留預設 **位置** 和 **方案名稱** 值。 設定 **解決方案** 以 **建立新的解決方案**。 取消核取 **[將方案和專案放置在相同的目錄中** （如果已核取）]。

1. 選擇 [建立] **** 按鈕以建立專案。

建立方案時，您可以在 Visual Studio 的 [ **方案總管** ] 視窗中看到產生的專案和原始程式檔。

![Visual Studio 中產生的解決方案](media/mathlibrary-solution-explorer-162.png "Visual Studio 中產生的解決方案")

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中建立 DLL 專案

1. 在功能表列上，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [新增專案]**** 對話方塊。

1. 在 [**新增專案**] 對話方塊的左窗格中，選取 [**已安裝**  >  **Visual C++**  >  **Windows 桌面**]。 在中央窗格中，選取 [ **動態連結程式庫] (DLL) **。 在 [**名稱**] 方塊中輸入*MathLibrary* ，以指定專案的名稱。 保留預設 **位置** 和 **方案名稱** 值。 設定 **解決方案** 以 **建立新的解決方案**。 如果未核取 [ **為方案建立目錄** ]，請檢查它。

   ![命名 MathLibrary 專案](media/mathlibrary-new-project-name-159.png "命名 MathLibrary 專案")

1. 選擇 [確定]**** 按鈕以建立專案。

建立方案時，您可以在 Visual Studio 的 [ **方案總管** ] 視窗中看到產生的專案和原始程式檔。

![Visual Studio 中產生的解決方案](media/mathlibrary-solution-explorer-159.png "Visual Studio 中產生的解決方案")

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-dll-project-in-visual-studio-2015-and-older-versions"></a>若要在 Visual Studio 2015 及更舊版本中建立 DLL 專案

1. 在功能表列上 **，選擇 [** 檔案 > **新增** > **專案**]。

1. 在 [新增專案]**** 對話方塊的左窗格中，展開 [已安裝]**** > [範本]**** 並選取 [Visual C++]****，然後在中央窗格中選取 [Win32 主控台應用程式]****。 在 [**名稱**] 編輯方塊中輸入*MathLibrary* ，以指定專案的名稱。 保留預設 **位置** 和 **方案名稱** 值。 設定 **解決方案** 以 **建立新的解決方案**。 如果未核取 [ **為方案建立目錄** ]，請檢查它。

   ![命名 MathLibrary 專案](media/mathlibrary-project-name.png "命名 MathLibrary 專案")

1. 選擇 [確定]**** 按鈕以關閉 [新增專案]**** 對話方塊，並啟動 [Win32 應用程式精靈]****。

   ![Win32 應用程式精靈總覽](media/mathlibrary-project-wizard-1.png "Win32 應用程式精靈總覽")

1. 選擇 [下一步]**** 按鈕。 在 [應用程式設定]**** 頁面的 [應用程式類型]**** 下，選取 [DLL]****。

   ![在 Win32 應用程式中建立 DLL](media/mathlibrary-project-wizard-2.png "在 Win32 應用程式中建立 DLL")

1. 選擇 [完成] **** 按鈕以建立專案。

精靈完成方案後，您可以在 Visual Studio 的 [方案總管]**** 視窗中，看到產生的專案和來源檔案。

![Visual Studio 中產生的解決方案](media/mathlibrary-solution-explorer-153.png "Visual Studio 中產生的解決方案")

::: moniker-end

目前，此 DLL 還不能做太多事。 接下來，您將建立標頭檔來宣告 DLL 匯出的函式，然後將函式定義加入 DLL 以使其更有用。

### <a name="to-add-a-header-file-to-the-dll"></a>將標頭檔新增至 DLL

1. 若要建立函式的標頭檔，請在功能表列上選擇 [**專案**  >  **加入新專案**]。

1. 在 [新增項目]**** 對話方塊的左窗格中，選取 [Visual C++]****。 在中間窗格中，選取 [標頭檔 (.h)] ****。 將 *MathLibrary* 指定為標頭檔的名稱。

   ![在 [加入新專案] 對話方塊中新增標頭](media/mathlibrary-add-new-item-header-file.png "在 [加入新專案] 對話方塊中加入標頭檔")

1. 選擇 [新增]**** 按鈕以產生空白標頭檔，這會顯示在新的編輯器視窗中。

   ![編輯器中的空白 MathLibrary .h 檔案](media/edit-empty-mathlibrary-header.png "編輯器中的空白 MathLibrary .h 檔案")

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

請注意檔案頂端的前置處理器陳述式。 DLL 專案的新專案範本會將 **_專案名稱_&#95;匯出** 新增至已定義的預處理器宏。 在此範例中，當您的 MathLibrary DLL 專案完成建置時，Visual Studio 會定義 **MATHLIBRARY&#95;EXPORTS**。

定義 **MATHLIBRARY&#95;EXPORTS** 巨集後，**MATHLIBRARY&#95;API** 巨集會在函式宣告中設定 `__declspec(dllexport)` 修飾詞。 此修飾詞會告知編譯器和連結器從 DLL 匯出函式或變數，以供其他應用程式使用。 如果 **MATHLIBRARY&#95;EXPORTS** 並未定義 (例如當用戶端應用程式包含標頭檔時)，則 **MATHLIBRARY&#95;API** 會將 `__declspec(dllimport)` 修飾詞套用至宣告。 此修飾詞會將應用程式中函式或變數的匯入最佳化。 如需詳細資訊，請參閱 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。

### <a name="to-add-an-implementation-to-the-dll"></a>將實作新增至 DLL

::: moniker range=">=vs-2019"

1. 在**方案總管**中，以滑鼠右鍵按一下 [**來源**檔案] 節點，然後選擇 [**加入**  >  **新專案**]。 以您在上一個步驟中加入新標頭檔的相同方式，建立名為 *MathLibrary*的新 .cpp 檔案。

1. 在編輯器視窗中，選取 [MathLibrary.cpp]**** 索引標籤 (如果已經開啟)。 如果沒有，請**在方案總管**中，按兩下**MathLibrary**專案的 [**原始**程式檔] 資料夾中的 [ **MathLibrary** ]，將它開啟。

1. 在編輯器中，以下列程式碼取代 MathLibrary.cpp 檔案的內容：

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "pch.h" // use stdafx.h in Visual Studio 2017 and earlier
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

::: moniker-end

::: moniker range="<=vs-2017"

1. 在編輯器視窗中，選取 [MathLibrary.cpp]**** 索引標籤 (如果已經開啟)。 如果沒有，請**在方案總管**中，按兩下**MathLibrary**專案的 [**原始**程式檔] 資料夾中的 [ **MathLibrary** ]，將它開啟。

1. 在編輯器中，以下列程式碼取代 MathLibrary.cpp 檔案的內容：

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019 and later
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

::: moniker-end

為了確認目前為止一切順利，請編譯動態連結程式庫。 若要進行編譯**Build**，請選擇  >  功能表列上的 [組建**組建方案**]。 DLL 和相關的編譯器輸出會放在方案資料夾正下方的 [ *Debug* ] 資料夾中。 如果您建立發行組建，則會將輸出放在名為 *release*的資料夾中。 輸出應該看起來像這樣：

::: moniker range=">=vs-2019"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>pch.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2017"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2015"

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

::: moniker-end

恭喜，您已使用 Visual Studio 建立 DLL！ 接下來，您將建立一個用戶端應用程式，該應用程式使用由 DLL 匯出的函式。

## <a name="create-a-client-app-that-uses-the-dll"></a>建立使用 DLL 的用戶端應用程式

當您建立 DLL 時，請考慮用戶端應用程式可能使用它的方式。 若要呼叫函式或存取由 DLL 匯出的資料，用戶端原始程式碼在編譯階段必須有宣告可用。 在連結時，連結器需要資訊來解析函式呼叫或資料存取。 DLL 會在匯 *入程式庫*中提供這項資訊，這是一個檔案，其中包含如何尋找函式和資料，而不是實際程式碼的相關資訊。 並且，在執行階段，DLL 必須可供用戶端使用，位於作業系統可以找到的位置。

無論是您自己或協力廠商，用戶端應用程式專案都需要使用多個資訊片段才能使用 DLL。 它需要找出宣告 DLL 匯出的標頭、連結器的匯入程式庫，以及 DLL 本身。 其中一個解決方法是將所有這些檔案複製到您的用戶端專案。 針對不太可能在您開發用戶端時變更的第三方 DLL，此方法可能是使用它們的最佳方法。 不過，如果您也要建置 DLL，則最好避免重複。 如果您在開發期間建立 DLL 檔案的本機複本，您可能會不小心變更一個複本中的標頭檔，而不是使用過期的程式庫。

若要避免同步處理常式代碼，建議您在用戶端專案中設定 include 路徑，以便直接從 DLL 專案包含 DLL 標頭檔。 此外，也在您的用戶端專案中設定程式庫路徑，以包含 DLL 專案中的 DLL 匯入程式庫。 最後，從 DLL 專案將建立的 DLL 複製到您的用戶端組建輸出目錄中。 此步驟可讓用戶端應用程式使用您所建置的相同 DLL 程式碼。

::: moniker range=">=vs-2019"

### <a name="to-create-a-client-app-in-visual-studio"></a>若要在 Visual Studio 中建立用戶端應用程式

1. 在功能表列上 **，選擇 [** 檔案 > **新增** > **專案** ] 以開啟 [ **建立新專案** ] 對話方塊。

1. 在對話方塊頂端，將 [語言]**** 設定為 **C++**，將 [平台]**** 設定為 **Windows**，並將 [專案類型]**** 設定為**主控台**。

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]****，然後選擇 [下一步]****。

1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中輸入 *>mathclient.cpp* ，以指定專案的名稱。 保留預設 **位置** 和 **方案名稱** 值。 設定 **解決方案** 以 **建立新的解決方案**。 取消核取 **[將方案和專案放置在相同的目錄中** （如果已核取）]。

   ![命名用戶端專案](media/mathclient-project-name-2019.png "命名用戶端專案")

1. 選擇 [建立]**** 按鈕以建立用戶端專案。

系統會為您建立基本的主控台應用程式專案。 主要來源檔案的名稱，與您先前輸入的名稱相同。 在此範例中，其名稱是 **MathClient.cpp**。 您可以建置該檔案，但該檔案尚不會使用您的 DLL。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>在 Visual Studio 2017 中建立用戶端應用程式

1. 若要建立將使用您建立之 DLL 的 C++ 應用程式，請在功能表列上選擇 [檔案]** [新增]** > ** [專案]** > ****。

1. 在 [新增專案]**** 對話方塊左窗格中的 [已安裝]**** > [Visual C++]**** 下方，選取 [Windows 傳統型]****。 在中央窗格中，選取 [ **Windows 主控台應用程式**]。 在 [**名稱**] 編輯方塊中指定專案的名稱 *>mathclient.cpp*。  保留預設 **位置** 和 **方案名稱** 值。 設定 **解決方案** 以 **建立新的解決方案**。 如果未核取 [ **為方案建立目錄** ]，請檢查它。

   ![命名用戶端專案](media/mathclient-new-project-name-159.png "命名用戶端專案")

1. 選擇 **[確定]** 以建立用戶端應用程式專案。

系統會為您建立基本的主控台應用程式專案。 主要來源檔案的名稱，與您先前輸入的名稱相同。 在此範例中，其名稱是 **MathClient.cpp**。 您可以建置該檔案，但該檔案尚不會使用您的 DLL。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-visual-studio-2015"></a>在 Visual Studio 2015 中建立用戶端應用程式

1. 若要建立將使用您建立之 DLL 的 C++ 應用程式，請在功能表列上選擇 [檔案]** [新增]** > ** [專案]** > ****。

1. 在 [新增專案]**** 對話方塊左窗格中的 [已安裝]**** > [範本]**** > [Visual C++]**** 下方，選取 **Win32**。 在中央窗格中，選取 [Win32 主控台應用程式] ****。 在 [**名稱**] 編輯方塊中指定專案的名稱 *>mathclient.cpp*。 保留預設 **位置** 和 **方案名稱** 值。 設定 **解決方案** 以 **建立新的解決方案**。 如果未核取 [ **為方案建立目錄** ]，請檢查它。

   ![命名用戶端專案](media/mathclient-project-name.png "命名用戶端專案")

1. 選擇 [確定]**** 按鈕以關閉 [新增專案]**** 對話方塊，並啟動 [Win32 應用程式精靈]****。 在 [Win32 應用程式精靈] **** 對話方塊的 [概觀] **** 頁面上，選擇 [下一步] **** 按鈕。

1. 在 [應用程式設定]**** 頁面的 [應用程式類型]**** 下方，選取 [主控台應用程式]**** (若尚未選取)。

1. 選擇 [完成] **** 按鈕以建立專案。

精靈完成時，會為您建立最基本的主控台應用程式專案。 主要來源檔案的名稱，與您先前輸入的名稱相同。 在此範例中，其名稱是 **MathClient.cpp**。 您可以建置該檔案，但該檔案尚不會使用您的 DLL。

::: moniker-end

接下來，若要在原始程式碼中呼叫 MathLibrary 函式，您的專案必須包含 *MathLibrary .h* 檔案。 您可以將此標頭檔複製到用戶端應用程式專案，然後將其新增至專案作為現有的項目。 這個方法對於第三方程式庫是理想選擇。 但是，如果您同時處理 DLL 和用戶端的程式碼，標頭檔可能會不同步。若要避免這個問題，請在專案中設定 **其他 Include 目錄** 路徑，以包含原始標頭的路徑。

### <a name="to-add-the-dll-header-to-your-include-path"></a>將 DLL 標頭新增至您的 Include 路徑

1. 以滑鼠右鍵按一下 [方案總管]**** 中的 **MathClient** 節點以開啟 [屬性頁]**** 對話方塊。

1. **在 [設定**] 下拉式清單方塊中，選取 [**所有**設定] （如果尚未選取）。

1. 在左窗格中，選取 [設定**屬性**  >  **C/c + +**  >  **一般**]。

1. 在屬性窗格中，選取 [其他 Include 目錄]**** 編輯方塊旁的下拉式清單控制項，然後選擇 [編輯]****。

   ![編輯其他 Include 目錄屬性](media/mathclient-additional-include-directories-property.png "編輯其他 Include 目錄屬性")

1. 在上方窗格中按兩下 [其他 Include 目錄]**** 對話方塊以啟用編輯控制項。 或者，選擇資料夾圖示來建立新專案。

1. 在編輯控制項中，指定 **MathLibrary.h** 標頭檔的位置路徑。 您可以選擇省略號 (**...**) 控制項流覽至正確的資料夾。

   您也可以輸入從用戶端來源檔案到包含 DLL 標頭檔的資料夾的相對路徑。 如果您遵循指示將用戶端專案放在 DLL 的不同方案中，相對路徑看起來應該像這樣：

   `..\..\MathLibrary\MathLibrary`

   如果您的 DLL 和用戶端專案位於相同的方案中，相對路徑可能如下所示：

   `..\MathLibrary`

   當 DLL 和用戶端專案位於其他資料夾時，請調整相對路徑以符合。 或者，使用省略號控制項來流覽資料夾。

   ![將標頭位置新增至其他 Include 目錄屬性](media/mathclient-additional-include-directories.png "將標頭位置新增至其他 Include 目錄屬性")

1. 在 [ **其他 Include 目錄** ] 對話方塊中輸入標頭檔的路徑之後，請選擇 [ **確定]** 按鈕。 在 [ **屬性頁** ] 對話方塊中，選擇 [ **確定]** 按鈕以儲存您的變更。

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

您可以編譯此程式碼，但不會連結。 如果您現在建立用戶端應用程式，則錯誤清單會顯示數個 LNK2019 錯誤。 這是因為您的專案遺漏了部分資訊：您尚未指定專案相依于 *MathLibrary .lib* 程式庫。 而且，您尚未告訴連結器如何尋找 *MathLibrary .lib* 檔案。

若要修正此問題，您可以將程式庫檔案直接複製到您的用戶端應用程式專案。 連結器會自動尋找並使用它。 但是，如果程式庫和用戶端應用程式都在開發中，可能會導致某個複本中的變更不會顯示在另一個複本中。 若要避免這個問題，您可以設定 [其他相依性 **]** 屬性，告知組建系統您的專案相依于 *MathLibrary .lib*。 此外，您可以在專案中設定額外的連結 **庫目錄** 路徑，以在連結時包含原始程式庫的路徑。

### <a name="to-add-the-dll-import-library-to-your-project"></a>將 DLL 匯入程式庫新增至您的專案

1. 在**方案總管**中的 [ **>mathclient.cpp** ] 節點上按一下滑鼠右鍵，然後選擇 [**屬性**] 以開啟 [**屬性頁**] 對話方塊。

1. **在 [設定**] 下拉式清單方塊中，選取 [**所有**設定] （如果尚未選取）。 它可確保任何屬性變更都適用于 Debug 和 Release 組建。

1. 在左窗格中，選取 [設定**屬性**  >  **連結器**  >  **輸入**]。 在屬性窗格中，選取 [其他相依性]**** 編輯方塊旁的下拉式清單控制項，然後選擇 [編輯]****。

   ![編輯 [其他相依性] 屬性](media/mathclient-additional-dependencies-property.png "編輯 [其他相依性] 屬性")

1. 在 [ **其他** 相依性] 對話方塊中，將 [ *MathLibrary* ] 新增至頂端編輯控制項中的清單。

   ![新增程式庫相依性](media/mathclient-additional-dependencies.png "新增程式庫相依性")

1. 選擇 [確定]**** 返回 [屬性頁]**** 對話方塊。

1. 在左窗格中，選取 [設定**屬性**  >  **連結器**  >  **一般**]。 在屬性窗格中，選取 [其他程式庫目錄]**** 編輯方塊旁的下拉式清單控制項，然後選擇 [編輯]****。

   ![編輯 [其他程式庫目錄] 屬性](media/mathclient-additional-library-directories-property.png "編輯 [其他程式庫目錄] 屬性")

1. 在 [其他程式庫目錄]**** 對話方塊的上方窗格中按兩下以啟用編輯控制項。 在編輯控制項中，指定 **MathLibrary.lib** 檔案的位置路徑。 根據預設，它位於 DLL 方案資料夾底下的 [ *Debug* ] 資料夾中。 如果您建立發行組建，檔案會放在名為 *release*的資料夾中。 您可以使用 `$(IntDir)` 宏，讓連結器可以找到您的 DLL，無論您建立的組建種類為何。 如果您遵循指示將用戶端專案放在 DLL 專案的不同方案中，相對路徑看起來應該像這樣：

   `..\..\MathLibrary\$(IntDir)`

   如果您的 DLL 和用戶端專案位於其他位置，請調整相對路徑以符合。

   ![新增程式庫目錄](media/mathclient-additional-library-directories.png "新增程式庫目錄")

1. 一旦您在 [其他程式庫目錄]**** 對話方塊中輸入程式庫檔案的路徑，請選擇 [確定]**** 按鈕返回 [屬性頁]**** 對話方塊。 選擇 **[確定]** 以儲存屬性變更。

您的用戶端應用程式現在可以編譯並成功連結，但仍不具備執行所需的所有項目。 當作業系統載入您的應用程式時，會尋找 MathLibrary DLL。 如果作業系統無法在特定系統目錄、環境路徑或本機應用程式目錄中找到該 DLL，則載入將會失敗。 視作業系統而定，您會看到類似下面的錯誤訊息：

![找不到 MathLibrary DLL 錯誤](media/mathclient-system-error-mathlibrary-dll-not-found.png "找不到 MathLibrary DLL 錯誤")

避免此問題之其中一個方法是將 DLL 複製到包含用戶端可執行檔的目錄，作為建置程序的一部分。 您可以將 **建立後事件** 新增至您的專案，以加入將 DLL 複製到組建輸出目錄的命令。 此處指定的命令只會在遺失或變更時複製 DLL。 它會根據您的組建設定，使用宏來複製到偵錯工具或發行位置。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>在建置後事件中複製 DLL

1. 在**方案總管**中的 [ **>mathclient.cpp** ] 節點上按一下滑鼠右鍵，然後選擇 [**屬性**] 以開啟 [**屬性頁**] 對話方塊。

1. **在 [設定**] 下拉式清單方塊中，選取 [**所有**設定] （如果尚未選取）。

1. 在左窗格中，選取 [設定**屬性**  >  **組建事件建立**  >  **後事件**]。

1. 在 [屬性] 窗格中，選取 [ **命令列** ] 欄位中的編輯控制項。 如果您遵循指示將用戶端專案放在 DLL 專案的不同方案中，請輸入下列命令：

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   如果您的 DLL 和用戶端專案是在其他目錄中，請將對應的相對路徑變更為相符的 DLL。

   ![新增建立後命令](media/mathclient-post-build-command-line.png "新增建立後命令")

1. 選擇 [確定]**** 按鈕，儲存您對專案屬性進行的變更。

現在您的用戶端應用程式已具備建置與執行所需所有項目。 在功能表列上選擇 [**組建**  >  **組建方案**]，以建立應用程式。 根據您的 Visual Studio 版本，Visual Studio 中的 [ **輸出** ] 視窗應該會有類似下列的範例：

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

恭喜，您已建立可在 DLL 中呼叫函式的應用程式。 現在，執行您的應用程式以查看其功能。 在功能表列上，選擇 [ **Debug**  >  **啟動但不進行調試**]。 Visual Studio 會開啟命令視窗，供程式執行。 輸出的最後一部分看起來應該如下所示：

![啟動用戶端應用程式而不進行偵錯工具](media/mathclient-run-without-debugging.png "啟動用戶端應用程式而不進行偵錯工具")

按任意鍵以關閉命令視窗。

您已建立 DLL 和用戶端應用程式，現在您可以進行實驗。 請嘗試在用戶端應用程式的程式碼中設定中斷點，並在偵錯工具中執行應用程式。 查看當您逐步執行程式庫呼叫時會發生什麼事。 將其他函式新增至程式庫，或撰寫可使用您 DLL 的另一個用戶端應用程式。

部署您的應用程式時，您也必須部署其使用的 DLL。 若要讓您建立的 Dll 或從協力廠商包含的 Dll，最簡單的方式就是將它們放在與應用程式相同的目錄中。 這就是所謂的 *應用程式本機部署*。 如需部署的詳細資訊，請參閱 [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[從 Visual Basic 應用程式呼叫 DLL 函式](calling-dll-functions-from-visual-basic-applications.md)
