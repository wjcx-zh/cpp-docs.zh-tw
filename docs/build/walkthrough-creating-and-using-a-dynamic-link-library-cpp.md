---
title: 逐步解說： 建立和使用您自己動態連結程式庫 （c + +） |Microsoft Docs
ms.custom: conceptual
ms.date: 09/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9806a17bfb603ff54609f2d509c50d0a5d91e15d
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821244"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>逐步解說： 建立和使用您自己動態連結程式庫 （c + +）

此逐步解說示範如何使用 Visual Studio IDE 來建立以 c + +，撰寫您自己的動態連結程式庫 (DLL)，並使用它從另一個 c + + 應用程式。 Dll 是其中一個最有用的一種 Windows 元件。 您可以使用它們來共用程式碼和資源，把您的應用程式的大小，並讓服務，並擴充您的應用程式變得更加容易。 在本逐步解說中，您會建立 DLL 實作一些數學函式，，然後再建立使用從 DLL 函式的主控台應用程式。 過程中，您會取得一些程式設計技術和 Windows Dll 中使用慣例的簡介。

這份逐步解說涵蓋下列工作：

- 在 Visual Studio 中建立 DLL 專案。

- 加入 DLL 的匯出函式和變數。

- Visual Studio 中建立主控台應用程式專案。

- 使用函式和從主控台應用程式中的 DLL 匯入的變數。

- 執行已完成的應用程式。

像靜態連結程式庫 DLL_匯出_變數、 函數以及依名稱和您的應用程式的資源_匯入_這些名稱，以使用這些變數、 函式和資源。 與靜態連結程式庫中，Windows 會在載入時或在執行階段，而不是在連結階段來連接它們在 DLL 中匯出連接應用程式中的匯入。 Windows 需要不屬於標準的 c + + 編譯模型，讓這些連線的額外資訊。 Visual c + + 編譯器實作 c + + 提供此額外資訊的一些 Microsoft 專有擴充功能。 我們，我們會說明這些擴充功能。

此逐步解說會建立兩個 Visual Studio 方案;建置 DLL，以及建置用戶端應用程式。 DLL 會使用 C 呼叫慣例，因此它可以從 平台及呼叫和連結慣例相符時，使用其他語言，建置的應用程式呼叫。 用戶端應用程式會使用_隱含連結_、 Windows 用來連結於載入時 DLL 應用程式。 此連結可讓應用程式以靜態方式連結的文件庫中呼叫 DLL 提供的函式，就像函式。

本逐步解說並不涵蓋一些常見的情況。 它不會顯示所使用的 c + + Dll 的其他程式設計語言。 它不會顯示如何建立僅含資源的 DLL。 它也不會顯示在執行階段，而不是在載入時，載入 Dll 的明確連結的使用。 接下來請放心，您可以使用 Visual c + + 來執行這些工作。 如需連結 Dll 的詳細資訊，請參閱[Visual c + + Dll](../build/dlls-in-visual-cpp.md)。 如需有關設定連結的隱含和明確連結的詳細資訊，請參閱 <<c0> [ 判斷哪一個連結方法來使用](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。 如需建立用於程式設計語言使用 C 語言連結慣例的 c + + Dll 的資訊，請參閱[匯出 c + + 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)。 如需如何建立 Dll 以與.NET 程式設計語言的使用資訊，請參閱[從 Visual Basic 應用程式呼叫 DLL 函式](../build/calling-dll-functions-from-visual-basic-applications.md)。

本逐步解說使用 Visual Studio 2017 中，但是程式碼和大部分的指示也適用於舊版。 若要建置新專案的步驟變更啟動 Visual Studio 2017 15.3 版中。 本逐步解說描述如何建立較新和舊版本的專案。 尋找符合您的 Visual Studio 版本的步驟。

## <a name="prerequisites"></a>必要條件

- 執行 Microsoft Windows 7 或更新版本的電腦。 我們建議的最佳開發體驗的 Windows 10。

- Visual Studio 2017 的複本。 如需如何下載並安裝 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio 2017](/visualstudio/install/install-visual-studio)。 當您執行安裝程式時，請確定**使用 c + + 的桌面開發**會檢查工作負載。 別擔心，如果您在安裝 Visual Studio 時，未安裝此工作負載。 您可以再次執行安裝程式，並立即安裝。

   ![使用 c + + 的桌面開發](media/desktop-development-with-cpp.png "使用 c + + 的桌面開發")

- 使用 Visual Studio IDE 的基本概念了解。 如果您已使用之前的 Windows 傳統型應用程式，您可能可以保留。 如需簡介，請參閱[Visual Studio IDE 功能導覽](/visualstudio/ide/visual-studio-ide)。

- C + + 語言，若要跟著做的基本概念的了解。 別擔心，我們不會有太過複雜。

## <a name="create-the-dll-project"></a>建立 DLL 專案

在這組工作中，您可以建立您的 DLL 的專案、 加入程式碼，並建置。 若要開始，請啟動 Visual Studio IDE 中，並登入，如果您需要。 Visual Studio 2017 15.3 版中的指示來自第一個項目。 對於較早版本的指示稍後，跳因此如果您需要。

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>DLL 中建立專案 Visual Studio 2017 版本 15.3 或更新版本

1. 在功能表列上選擇 [**檔案** > **新增** > **專案**開啟**新專案**] 對話方塊。

1. 在左窗格中**新的專案**對話方塊方塊中，展開**已安裝**並**Visual c + +** 如有必要，，然後選擇  **Windows 桌面**. 在中央窗格中，選取**Windows Desktop 精靈**。 請輸入`MathLibrary`中**名稱**方塊，以指定專案的名稱。

   ![將專案命名為 MathLibrary](media/mathlibrary-new-project-name-153.png "MathLibrary 專案的名稱")

1. 選擇 **[確定]** 按鈕以關閉**新增專案**對話方塊，並開始**Windows 桌面專案**精靈。

1. 在  **Windows 桌面專案**精靈，在**應用程式類型**，選取**動態連結程式庫 (.dll)**。

   ![在 Windows 桌面專案精靈中建立 DLL](media/mathlibrary-desktop-project-wizard-dll.png "建立 Windows 桌面專案精靈 中的 DLL")

1. 選擇 [確定] 按鈕以建立專案。

> [!NOTE]
> 額外的步驟，才能在 Visual Studio 2017 15.3 版中修正的問題。 請遵循下列指示來看看是否需要進行這項變更。
>
>1. 在 [**方案總管] 中**，如果尚未選取，請選取**MathLibrary**底下**解決方案 'MathLibrary'**。
>
>1. 在功能表列上，依序選擇 [專案] > [屬性]。
>
>1. 在左窗格中**屬性頁**對話方塊中，選取**前置處理器**之下**組態屬性** > **C/c + +**. 請檢查的內容**前置處理器定義**屬性。<br/><br/>![檢查前置處理器定義屬性](media/mathlibrary-153bug-preprocessor-definitions-check.png "檢查前置處理器定義屬性")<br/><br/>如果您看到**MATHLIBRARY&#95;匯出**中**前置處理器定義**清單中，您就不需要變更任何項目。 如果您看到**MathLibrary&#95;匯出**相反的然後繼續進行下列步驟。
>
>1. 在頂端**屬性頁** 對話方塊中，變更**Configuration**下拉式清單可**所有組態**。
>
>1. 在 屬性 窗格中，選取 下拉式清單控制項的編輯方塊旁邊**前置處理器定義**，然後選擇**編輯**。<br/><br/>![編輯 [前置處理器定義] 屬性](media/mathlibrary-153bug-preprocessor-definitions-property.png "編輯前置處理器定義 屬性")
>
>1. 在上方窗格**前置處理器定義** 對話方塊中，新增新的符號， `MATHLIBRARY_EXPORTS`。<br/><br/>![新增 MATHLIBRARY_EXPORTS 符號](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "新增 MATHLIBRARY_EXPORTS 符號")
>
>1. 選擇**確定**以關閉**前置處理器定義** 對話方塊中，然後選擇**確定**若要將變更儲存至專案屬性。

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>若要在較舊版本的 Visual Studio 建立 DLL 專案

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

1. 在左窗格中**新的專案**對話方塊方塊中，展開**已安裝** > **範本**，然後選取**Visual c + +**，和然後在中央窗格中，選取**Win32 主控台應用程式**。 請輸入`MathLibrary`中**名稱**編輯方塊，以指定專案的名稱。

   ![將專案命名為 MathLibrary](media/mathlibrary-project-name.png "MathLibrary 專案的名稱")

1. 選擇 **[確定]** 按鈕以關閉**新增專案**對話方塊，並開始**Win32 應用程式精靈**。

   ![Win32 應用程式精靈概觀](media/mathlibrary-project-wizard-1.png "Win32 應用程式精靈概觀")

1. 選擇 [下一步] 按鈕。 在 **應用程式設定**頁面的 **應用程式類型**，選取**DLL**。

   ![在 Win32 應用程式精靈中建立 DLL](media/mathlibrary-project-wizard-2.png "建立 Win32 應用程式精靈中的 DLL")

1. 選擇 [完成]  按鈕以建立專案。

當精靈完成解決方案時，您可以看到產生的專案和原始程式檔中**方案總管 中**Visual Studio 中的視窗。

![在 Visual Studio 中產生的解決方案](media/mathlibrary-solution-explorer-153.png "Visual Studio 中產生解決方案")

權限，此 DLL 不會執行太多。 接下來，您會建立標頭檔宣告的函式的 DLL 會匯出，然後再將函式定義新增 DLL 以使其更加實用。

### <a name="to-add-a-header-file-to-the-dll"></a>若要加入至 DLL 的標頭檔

1. 若要建立您的函式的標頭檔的功能表列上，選擇**專案** > **加入新項目**。

1. 在 **加入新項目**對話方塊的左窗格中，選取**Visual c + +**。 在中間窗格中，選取 [標頭檔 (.h)] 。 指定`MathLibrary.h`做為標頭檔的名稱。

   ![在加入新項目 對話方塊中新增標頭](media/mathlibrary-add-new-item-header-file.png "新增標頭檔中加入新項目對話方塊")

1. 選擇**新增**按鈕，以產生空白標頭檔，這會顯示在新的 [編輯器] 視窗。

   ![在編輯器中的空白 MathLibrary.h 檔案](media/edit-empty-mathlibrary-header.png "編輯器中的空白 MathLibrary.h 檔案")

1. 取代此程式碼中的標頭檔的內容：

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

此標頭檔宣告一些函式來產生一般化的 Fibonacci 序列，指定兩個的初始值。 呼叫`fibonacci_init(1, 1)`產生熟悉 Fibonacci 數字序列。

請注意，在檔案頂端的前置處理器陳述式。 根據預設，加入 DLL 的新專案範本 **<em>PROJECTNAME</em>&#95;匯出**DLL 專案定義的前置處理器巨集。 在此範例中，Visual Studio 會定義**MATHLIBRARY&#95;匯出**MathLibrary DLL 專案建置時。 （Visual Studio 2017 15.3 版中的精靈不會強制為大寫的這個符號定義。 如果您專案的名稱，您 「 MathLibrary"，則定義的符號是 MathLibrary&#95;而不是 MATHLIBRARY 匯出&#95;匯出。 That's 為什麼會有額外的步驟上方新增這個符號。)

當**MATHLIBRARY&#95;匯出**定義巨集，則**MATHLIBRARY&#95;API**巨集`__declspec(dllexport)`函式宣告修飾詞。 此修飾詞會告訴編譯器和連結器函式或變數匯出從 DLL，以便供其他應用程式。 當**MATHLIBRARY&#95;匯出**未定義，比方說，當用戶端應用程式包含標頭檔時**MATHLIBRARY&#95;API**適用於`__declspec(dllimport)`修飾詞宣告。 此修飾詞會最佳化的函式或變數的應用程式中匯入。 如需詳細資訊，請參閱 < [dllexport、 dllimport](../cpp/dllexport-dllimport.md)。

### <a name="to-add-an-implementation-to-the-dll"></a>若要將實作新增至 DLL

1. 在 編輯器 視窗中，選取  索引標籤**MathLibrary.cpp**如果已經開啟。 如果沒有，在**方案總管**，開啟**MathLibrary.cpp**中**原始程式檔**資料夾**MathLibrary**專案。

1. 在編輯器中，請以下列程式碼取代 MathLibrary.cpp 檔案的內容：

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h"
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

若要確認一切運作到目前為止，編譯動態連結程式庫。 若要編譯，請選擇**建置** > **建置方案**功能表列上。 輸出應該看起來像：

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

恭喜，您已使用 Visual c + + DLL ！ 接下來，您將建立會使用由 DLL 匯出的函式用戶端應用程式。

## <a name="create-a-client-app-that-uses-the-dll"></a>建立會使用 DLL 的用戶端應用程式

當您建立 DLL 時，您必須思考如何使用您的 DLL。 若要編譯程式碼呼叫由 DLL 匯出函式，宣告必須包含在用戶端原始程式碼。 在連結時，這些呼叫 DLL 函式時解析，連結器必須有*匯入程式庫*，包含有關如何尋找的函式，而不是實際的程式碼的 Windows 資訊的特殊程式庫檔案。 而且在執行階段，DLL 必須提供給用戶端，在作業系統可以找到的位置。

若要使用的 dll，是否您擁有或協力廠商 DLL，用戶端應用程式專案必須尋找宣告 DLL 的標頭將匯出的匯入程式庫，連結器，與該 DLL 本身。 一種方法，是將所有這些檔案複製到您的用戶端專案。 適用於協力廠商 Dll 不太可能會變更開發您的用戶端時，這個方法可能會使用它們的最佳方式。 不過，當您也會建置 DLL，最好避免重複。 如果您正在開發的 DLL 檔案的複本，您可能不小心變更標頭中的檔案複本，但不是另一個，或使用過時的程式庫。 若要避免這個問題，我們建議您設定在您的用戶端專案，以包含 DLL 的標頭檔從 DLL 專案的 include 路徑。 此外，在您的用戶端專案，以包含從 DLL 專案的 DLL 匯入程式庫中設定的程式庫路徑。 最後，將從 DLL 專案的建置的 DLL 複製到組建輸出目錄。 這個步驟可讓您的用戶端應用程式，以使用您所建立之相同 DLL 程式碼。

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>若要建立用戶端應用程式 Visual Studio 2017 版本 15.3 或更新版本

1. 若要建立會使用您在功能表列建立，DLL 的 c + + 應用程式選擇**檔案** > **新增** > **專案**。

1. 在左窗格中**新的專案**對話方塊中，選取**Windows 桌面**之下**已安裝** > **Visual c + +**。 在中央窗格中，選取**Windows Desktop 精靈**。 指定專案的名稱`MathClient`，請在**名稱**編輯方塊。

   ![將專案命名為用戶端](media/mathclient-new-project-name-153.png "用戶端專案的名稱")

1. 選擇 **[確定]** 來啟動**Windows 桌面專案**精靈。 在精靈中，選擇**確定**建立用戶端應用程式專案。

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>在舊版 Visual Studio 2017 中建立用戶端應用程式

1. 若要建立會使用您在功能表列建立，DLL 的 c + + 應用程式選擇**檔案** > **新增** > **專案**。

1. 在左窗格中**新的專案**對話方塊中，選取**Win32**之下**已安裝** > **範本** > **Visual c + +**。 在中央窗格中，選取 [Win32 主控台應用程式] 。 指定專案的名稱`MathClient`，請在**名稱**編輯方塊。

   ![將專案命名為用戶端](media/mathclient-project-name.png "用戶端專案的名稱")

1. 選擇 **[確定]** 按鈕以關閉**新增專案**對話方塊，並開始**Win32 應用程式精靈**。 在 [Win32 應用程式精靈]  對話方塊的 [概觀]  頁面上，選擇 [下一步]  按鈕。

1. 在 **應用程式設定**頁面的 **應用程式類型**，選取**主控台應用程式**如果已選取。

1. 選擇 [完成]  按鈕以建立專案。

當精靈完成時，則會為您建立最基本的主控台應用程式專案。 主要的原始程式檔的名稱是您先前輸入專案名稱相同。 在此範例中，它會命名為**MathClient.cpp**。 您可以建置它，但它不會還使用您的 DLL。

接下來，若要在您的程式碼中呼叫 MathLibrary 函式，您的專案必須包含 MathLibrary.h 檔案。 您可以將此標頭檔複製到用戶端應用程式專案，然後將它新增至專案做為現有的項目。 這個方法可以是協力廠商程式庫的理想選擇。 不過，如果您正在操作的程式碼針對您的 DLL 同時為您的用戶端，所可能會導致不會顯示在另一個標頭檔中的變更。 若要避免這個問題，您可以變更**其他 Include 目錄**專案包含原始的標頭的路徑中的路徑。

### <a name="to-add-the-dll-header-to-your-include-path"></a>若要加入此 DLL 標頭，以您 include 路徑

1. 開啟**屬性頁** 對話方塊**MathClient**專案。

1. 在 **組態**下拉式清單方塊中，選取**所有組態**如果已選取。

1. 在左窗格中，選取**一般**下方**組態屬性** > **C/c + +**。

1. 在 [屬性] 窗格中，選取下拉式清單控制項旁**其他 Include 目錄**編輯方塊中，然後選擇**編輯**。

   ![編輯 [其他 Include 目錄] 屬性](media/mathclient-additional-include-directories-property.png "編輯 [其他 Include 目錄] 屬性")

1. 在上方窗格中按兩下**其他 Include 目錄**對話方塊，讓編輯控制項。

1. 在編輯控制項中，指定的位置路徑**MathLibrary.h**標頭檔。 在此情況下，您可以使用相對路徑：

   `..\..\MathLibrary\MathLibrary`

   ![加入 [其他 Include 目錄] 屬性中的標頭位置](media/mathclient-additional-include-directories.png "將標頭位置新增至 [其他 Include 目錄] 屬性")

1. 一旦您輸入的路徑中的標頭檔**其他 Include 目錄**對話方塊方塊中，選擇**確定**按鈕來返回**屬性頁** 對話方塊中，並然後選擇**確定**按鈕以儲存您的變更。

您現在可以包含**MathLibrary.h**檔案，並使用它在用戶端應用程式中宣告的函式。 內容取代**MathClient.cpp**藉由使用下列程式碼：

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "pch.h"
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

此程式碼可以編譯，但未連結，因為連結器找不到尚未建置應用程式所需的匯入程式庫。 連結器必須尋找 MathLibrary.lib 檔案已成功連結。 設定將 MathLibrary.lib 檔案加入至組建**其他相依性**屬性。 同樣地，您可以將程式庫檔案複製到用戶端應用程式專案，但是，如果程式庫和用戶端應用程式是在開發期間，可能導致不會顯示在另一個複本中的變更。 若要避免這個問題，您可以變更**其他程式庫目錄**包含原始程式庫的路徑，當您連結的專案中的路徑。

### <a name="to-add-the-dll-import-library-to-your-project"></a>將 DLL 匯入程式庫新增至您的專案

1. 開啟**屬性頁** 對話方塊**MathClient**專案。

1. 在 **組態**下拉式清單方塊中，選取**所有組態**如果已選取。

1. 在左窗格中，選取**輸入**下方**組態屬性** > **連結器**。 在 [屬性] 窗格中，選取下拉式清單控制項旁**其他相依性**編輯方塊中，然後選擇**編輯**。

   ![編輯其他相依性屬性](media/mathclient-additional-dependencies-property.png "編輯其他相依性屬性")

1. 在 [**其他相依性**] 對話方塊中，新增`MathLibrary.lib`中最上方的清單中，編輯控制項。

   ![新增程式庫相依性](media/mathclient-additional-dependencies.png "新增程式庫相依性")

1. 選擇**確定**回到**屬性頁** 對話方塊。

1. 在左窗格中，選取**一般**下方**組態屬性** > **連結器**。 在 [屬性] 窗格中，選取下拉式清單控制項旁**其他程式庫目錄**編輯方塊中，然後選擇**編輯**。

   ![編輯其他程式庫目錄屬性](media/mathclient-additional-library-directories-property.png "編輯其他程式庫目錄屬性")

1. 在上方窗格中按兩下**其他程式庫目錄**對話方塊，讓編輯控制項。 在編輯控制項中，指定的位置路徑**MathLibrary.lib**檔案。 輸入此值，以使用適用於偵錯和發行組建的巨集：

   `..\..\MathLibrary\$(IntDir)`

   ![新增程式庫目錄](media/mathclient-additional-library-directories.png "新增程式庫目錄")

1. 一旦您輸入的路徑中的程式庫檔案**其他程式庫目錄**對話方塊方塊中，選擇**確定**按鈕來返回**屬性頁** 對話方塊。

您的用戶端應用程式現在可以編譯並連結成功，但它仍沒有執行所需要的所有項目。 當作業系統載入您的應用程式時，它會尋找 MathLibrary DLL。 如果特定系統目錄、 環境路徑或本機應用程式目錄中找不到 DLL，載入將會失敗。 若要避免此問題的一個方式是將 DLL 複製到目錄，其中包含用戶端可執行檔建置程序的一部分。 若要複製的 DLL，您可以加入**建置後事件**至您的專案，來加入命令，將 DLL 複製至組建輸出目錄。 只有當它遺漏或已變更，並使用巨集，以從您的設定正確的偵錯或其他位置來回複製時，才將 DLL 複製此處指定的命令。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>若要在建置後事件中複製 DLL

1. 開啟**屬性頁** 對話方塊**MathClient**專案如果尚未開啟。

1. 在 [組態] 下拉式清單方塊中，選取**所有組態**如果已選取。

1. 在左窗格中，選取**Post-build Event**下方**組態屬性** > **建置事件**。

1. 在 屬性 窗格中，選取 編輯控制項中的**命令列**欄位，然後再輸入下列命令：

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![新增建置後命令](media/mathclient-post-build-command-line.png "新增建置後命令")

1. 選擇**確定**按鈕，以將變更儲存至專案屬性。

現在您的用戶端應用程式已經做好建置並執行。 建置應用程式選擇**建置** > **建置方案**功能表列上。 **輸出**Visual Studio 中的視窗應該會看見：

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

恭喜，您已建立一個在 DLL 中呼叫函式應用程式。 現在，執行您的應用程式，以查看其用途。 在功能表列上選擇 **偵錯** > **啟動但不偵錯**。 Visual Studio 會開啟命令視窗中執行程式。 輸出的最後一個部分應該看起來像：

![啟動用戶端應用程式，但不偵錯](media/mathclient-run-without-debugging.png "啟動用戶端應用程式，但不偵錯")

按任意鍵關閉命令視窗。

既然您已建立的 DLL 和用戶端應用程式，您可以實驗。 請嘗試在用戶端應用程式的程式碼中設定中斷點和偵錯工具中執行應用程式。 請參閱 < 當您逐步執行程式庫呼叫，會發生什麼事。 將其他函式新增至程式庫，或撰寫您的 DLL 會使用的另一個用戶端應用程式。

當您部署您的應用程式時，您也必須部署它所使用的 Dll。 最簡單的方式，可讓您建置或您所包含的 Dll 協力廠商使用您的應用程式是將它們置於您的應用程式相同的目錄也稱為*應用程式本機部署*。 如需有關部署的詳細資訊，請參閱 < [Visual c + + 中的部署](..\ide\deployment-in-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)<br/>
[部署傳統型應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)<br/>
[逐步解說：部署程式 (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>
[從 Visual Basic 應用程式呼叫 DLL 函式](../build/calling-dll-functions-from-visual-basic-applications.md)