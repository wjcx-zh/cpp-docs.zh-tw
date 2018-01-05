---
title: "逐步解說： 建立和使用您自己動態連結程式庫 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
caps.latest.revision: "36"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdcc02cf7c86b85684df0e8d8b7a1f0049ff7e25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>逐步解說： 建立和使用您自己動態連結程式庫 （c + +）

此逐步解說示範如何使用 Visual Studio IDE 來建立以 c + +，撰寫您自己動態連結程式庫 (DLL)，並使用它從另一個 c + + 應用程式。 Dll 是其中一個最有用的一種 Windows 元件。 您可以使用它們來共用程式碼和資源，應用程式的大小縮減到，並使其更容易服務和擴充您的應用程式。 在本逐步解說中，您會建立實作某些數學函式，呼叫的 DLL，然後再建立主控台應用程式會使用從 DLL 函式。 過程中，您可以取得一些程式設計技術和 Windows Dll 中使用慣例的簡介。

這份逐步解說涵蓋下列工作：

- Visual Studio 中建立 DLL 專案。

- 加入 DLL 的匯出函式和變數。

- Visual Studio 中建立主控台應用程式專案。

- 使用的函式和從主控台應用程式中的 DLL 匯入的變數。

- 執行已完成的應用程式。

要以靜態方式連結程式庫 DLL_匯出_變數、 函數和資源的名稱和您的應用程式_匯入_這些名稱，以使用這些變數、 函數和資源。 不同於以靜態方式連結的程式庫中，Windows 會連線到在載入時間，或在執行階段，而不是在連結階段來連接這些 DLL 中匯出的匯入您的應用程式中。 Windows 需要不屬於標準的 c + + 編譯模型，讓這些連線的額外資訊。 Visual c + + 編譯器實作某些 c + + 提供這項額外資訊的 Microsoft 專有擴充功能。 因為我們，我們會說明這些擴充功能。

這個逐步解說會建立兩個 Visual Studio 方案。建置 DLL 的其中一個，建置用戶端應用程式的另一個。 DLL 會使用 C 呼叫慣例，因此它可以從建置使用其他語言，只要符合的平台和呼叫和連結慣例的應用程式呼叫。 用戶端應用程式會使用_隱含連結_、 Windows 用來連結於載入時 DLL 應用程式。 這可讓應用程式中以靜態方式連結的程式庫呼叫 DLL 提供的函式，就像函式一樣。

本逐步解說並不涵蓋一些常見的情況。 它不會顯示所使用的 c + + Dll 的其他程式設計語言。 它不會顯示如何建立資源專用 DLL。 它也不會顯示在執行階段，而不是在載入時間載入 Dll 的明確連結的使用。 請放心，您可以使用 Visual c + + 來執行所有這些作業。 連結 Dll 的詳細資訊，請參閱[Visual c + + 中的 Dll](../build/dlls-in-visual-cpp.md)。 如需設定連結的隱含和明確連結的詳細資訊，請參閱[判斷哪一個連結方法使用](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。 如需建立用於程式設計語言使用 C 語言連結慣例的 c + + Dll 的資訊，請參閱[匯出 c + + 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)。 如需如何使用與.NET 程式設計語言建立 Dll，請參閱[從 Visual Basic 應用程式呼叫 DLL 函式](../build/calling-dll-functions-from-visual-basic-applications.md)。

本逐步解說使用 Visual Studio 2017，但該程式碼和大部分的指示適用於舊版。 如何建置新專案的步驟變更啟動 Visual Studio 2017 15.3 版本中。 本逐步解說描述如何建立較新和舊版本的專案。 尋找符合您的 Visual Studio 版本的步驟。

## <a name="prerequisites"></a>必要條件

- 執行 Microsoft Windows 7 或更新版本的電腦。 我們建議最佳的開發經驗 Windows 10。

- Visual Studio 2017 的複本。 如需如何下載並安裝 Visual Studio，請參閱[安裝 Visual Studio 2017](/visualstudio/install/install-visual-studio)。 當您執行安裝程式時，請確定**的 c + + 桌面應用程式開發**會檢查工作負載。 如果您未安裝此工作負載，當您安裝 Visual Studio 不要擔心。 您可以再次執行安裝程式，並立即安裝。

   ![使用 c + + 桌面開發](media/desktop-development-with-cpp.png "的 c + + 桌面應用程式開發")

- 了解使用 Visual Studio IDE 的基本概念。 如果您使用 Windows 桌面應用程式之前，您可能可以跟上。 如需簡介，請參閱[Visual Studio IDE 功能導覽](/visualstudio/ide/visual-studio-ide)。

- 足夠要遵循的 c + + 語言基本知識的了解。 別擔心，我們通常不太複雜的任何項目。

## <a name="create-the-dll-project"></a>建立 DLL 專案

在這組工作中，您可以建立您的 DLL 的專案、 加入程式碼，並建置。 若要開始，請啟動 Visual Studio IDE，並登入，如果您需要。 Visual Studio 2017 版本 15.3 的指示來自第一個項目。 較早版本的指示稍後，跳因此如果您需要。

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>在 Visual Studio 2017 版本中建立 DLL 專案，15.3 或更新版本

1. 在功能表列上選擇 [**檔案**，**新增**，**專案**開啟**新專案**] 對話方塊。

1. 在左窗格中**新專案**對話方塊方塊中，展開 **已安裝**和**Visual c + +**如果需要，然後選擇  **Windows 桌面**。 在中央窗格中，選取**Windows 桌面精靈**。 輸入`MathLibrary`中**名稱**方塊來指定專案的名稱。

   ![MathLibrary 專案的名稱，](media/mathlibrary-new-project-name-153.png "MathLibrary 專案的名稱")

1. 選擇**確定**按鈕以關閉**新專案**對話方塊，並開始**Windows 桌面專案**精靈。

1. 在**Windows 桌面專案**精靈下**應用程式類型**，選取**動態連結程式庫 (.dll)**。

   ![在 Windows 桌面專案精靈 建立 DLL](media/mathlibrary-desktop-project-wizard-dll.png "建立 Windows 桌面專案精靈 中的 DLL")

1. 選擇 [確定] 按鈕以建立專案。

> [!NOTE]
> 若要在 Visual Studio 2017 15.3 版本中修正問題，不需要其他步驟。 請遵循這些指示來檢查是否需要進行這項變更。
>
>1. 在**方案總管 中**，如果尚未選取，請選取**MathLibrary**底下**方案 'MathLibrary'**。
>
>1. 在功能表列上，依序選擇 [專案] 和 [屬性]。
>
>1. 在左窗格中**屬性頁**對話方塊中，選取**前置處理器**下**組態屬性**， **C/c + +**。 請檢查的內容**前置處理器定義**屬性。<br/><br/>![請檢查前置處理器定義屬性](media/mathlibrary-153bug-preprocessor-definitions-check.png "檢查前置處理器定義屬性")<br/><br/>如果您看到**MATHLIBRARY &#95;匯出**中**前置處理器定義**清單，則您不需要變更任何項目。 如果您看到**MathLibrary &#95;匯出**相反地，然後繼續遵循這些步驟。
>
>1. 在頂端**屬性頁** 對話方塊中，變更**組態**下拉式清單可**所有組態**。
>
>1. 在 屬性 窗格中，選取 編輯方塊旁邊的下拉式清單控制項**前置處理器定義**，然後選擇 **編輯**。<br/><br/>![編輯 [前置處理器定義] 屬性](media/mathlibrary-153bug-preprocessor-definitions-property.png "編輯前置處理器定義屬性")
>
>1. 在上方窗格**前置處理器定義** 對話方塊中，加入新的符號， `MATHLIBRARY_EXPORTS`。<br/><br/>![新增 MATHLIBRARY_EXPORTS 符號](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "新增 MATHLIBRARY_EXPORTS 符號")
>
>1. 選擇**[確定]**解除**前置處理器定義**] 對話方塊中，然後選擇 [ **[確定]**儲存在專案屬性的變更。

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>在舊版的 Visual Studio 中建立 DLL 專案

1. 在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。

1. 在左窗格中**新專案**對話方塊方塊中，展開 **已安裝**，**範本**，然後選取**Visual c + +**，然後在中央窗格中，選取**Win32 主控台應用程式**。 輸入`MathLibrary`中**名稱**編輯方塊，以指定專案的名稱。

   ![MathLibrary 專案的名稱，](media/mathlibrary-project-name.png "MathLibrary 專案的名稱")

1. 選擇**確定**按鈕以關閉**新專案**對話方塊，並開始**Win32 應用程式精靈**。

   ![Win32 應用程式精靈概觀](media/mathlibrary-project-wizard-1.png "Win32 應用程式精靈概觀")

1. 選擇 [下一步] 按鈕。 在**應用程式設定**頁面的 **應用程式類型**，選取**DLL**。

   ![在 Win32 應用程式精靈建立 DLL](media/mathlibrary-project-wizard-2.png "Win32 應用程式精靈中建立 DLL")

1. 選擇 [完成]  按鈕以建立專案。

當精靈完成方案時，您可以看到產生的專案和來源檔案中**方案總管 中**Visual Studio 中的視窗。

![在 Visual Studio 中產生方案](media/mathlibrary-solution-explorer-153.png "產生 Visual Studio 中的方案")

右現在，這個 DLL 不太大。 接下來，您會建立標頭檔，以宣告您的 DLL 函式會匯出，，然後將函式定義加入至 DLL 以使其更加實用。

### <a name="to-add-a-header-file-to-the-dll"></a>若要加入 dll 的標頭檔

1. 若要建立您的函式的標頭檔，在功能表列上，選擇**專案**，**加入新項目**。

1. 在**加入新項目**對話方塊的左窗格中，選取**Visual c + +**。 在中間窗格中，選取 [標頭檔 (.h)] 。 指定`MathLibrary.h`做為標頭檔的名稱。

   ![新增標頭中加入新項目對話方塊](media/mathlibrary-add-new-item-header-file.png "新增標頭檔中加入新項目對話方塊")

1. 選擇**新增**按鈕以產生空白標頭檔，它會顯示在新的編輯器視窗。

   ![在編輯器中的空白 MathLibrary.h 檔案](media/edit-empty-mathlibrary-header.png "編輯器中的空白 MathLibrary.h 檔案")

1. 標頭檔的內容取代此程式碼：

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

此標頭檔宣告以產生一般化費式數列順序，指定兩個的起始值的某些函式。 呼叫`fibonacci_init(1, 1)`產生熟悉 Fibonacci 數字序列。

請注意，前置處理器陳述式，在檔案頂端。 根據預設，加入 DLL 的新專案範本 ***PROJECTNAME*&#95;匯出**DLL 專案定義的前置處理器巨集。 在此範例中，Visual Studio 會定義**MATHLIBRARY &#95;匯出**建置 MathLibrary DLL 專案的時。 （在 Visual Studio 2017 版本 15.3 精靈不會強制為大寫的這個符號定義。 如果您專案的名稱，您 「 MathLibrary"定義的符號則 MathLibrary &#95;匯出，而不是 MATHLIBRARY &#95;將匯出。 That's 為何有上述加入這個符號的額外步驟。)

當**MATHLIBRARY &#95;匯出**巨集定義， **MATHLIBRARY &#95;應用程式開發介面**巨集將`__declspec(dllexport)`函式宣告修飾詞。 此修飾詞會告訴編譯器和連結器函式或變數從 DLL 匯出，以便供其他應用程式。 當**MATHLIBRARY &#95;匯出**未定義，例如，當用戶端應用程式包含標頭檔時**MATHLIBRARY &#95;應用程式開發介面**適用於`__declspec(dllimport)`修飾詞來宣告。 此修飾詞會最佳化的函式或變數的應用程式中匯入。 如需詳細資訊，請參閱[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。

### <a name="to-add-an-implementation-to-the-dll"></a>若要將實作新增至 DLL

1. 在編輯器視窗中，選取的索引標籤**MathLibrary.cpp**如果已經開啟。 如果不是，在**方案總管 中**，開啟**MathLibrary.cpp**中**原始程式檔**資料夾**MathLibrary**專案。

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

若要確認一切運作為止，編譯動態連結程式庫。 若要編譯時，選擇 **建置**，**建置方案**功能表列上。 輸出看起來應該像這樣：

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

恭喜，您已建立使用 Visual c + + DLL ！ 接下來，您會建立由 DLL 匯出的函式會使用用戶端應用程式。

## <a name="create-a-client-app-that-uses-the-dll"></a>建立用戶端應用程式使用 DLL

當您建立 DLL 時，您必須思考如何使用您的 DLL。 若要編譯程式碼呼叫 dll 匯出函式，宣告必須包含在用戶端程式碼中。 在連結時，當這些呼叫 DLL 函式會解析，必須具有連結器*匯入程式庫*，一種特殊的程式庫檔案，其中包含有關如何尋找此函式，而非實際的程式碼適用於 Windows 的資訊。 和執行階段 DLL 必須可供用戶端作業系統可以找到的位置中使用。

若要使用 DLL，是否您擁有或協力廠商 DLL，用戶端應用程式專案必須是找不到匯出宣告 DLL 的標頭，連結器和 DLL 本身的匯入程式庫。 若要這樣做的方法之一是，將所有這些檔案複製到用戶端專案。 適用於協力廠商 Dll 不太可能會變更您的用戶端在開發時，這可能是最佳的方式來使用它們。 不過，當您也會建立 DLL，最好避免重複。 如果您正在開發過程中的 DLL 檔案的複本，您可能不小心變更標頭中的檔案複本，但是，或使用過期的程式庫。 若要避免這個問題，我們建議您在用戶端專案包含 DLL 的標頭檔從 DLL 專案中設定 include 路徑。 此外，包含從 DLL 專案的 DLL 匯入程式庫的用戶端專案中設定的程式庫路徑。 最後，將從 DLL 專案的建置的 DLL 複製到組建輸出目錄。 這可確保您的用戶端應用程式會使用相同您建置的 DLL 程式碼。

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>在 Visual Studio 2017 版本中建立用戶端應用程式，15.3 或更新版本

1. 若要建立使用您剛剛建立，在功能表列的 DLL 的 c + + 應用程式選擇**檔案**，**新增**，**專案**。

1. 在左窗格中**新專案**對話方塊中，選取**Windows 桌面**下**已安裝**， **Visual c + +**。 在中央窗格中，選取**Windows 桌面精靈**。 指定專案的名稱`MathClient`，請在**名稱**編輯方塊。

   ![用戶端專案的名稱，](media/mathclient-new-project-name-153.png "用戶端專案的名稱")

1. 選擇**確定**啟動**Windows 桌面專案**精靈。 在精靈中，選擇 **確定**建立用戶端應用程式專案。

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>在舊版 Visual Studio 2017 建立用戶端應用程式

1. 若要建立使用您剛剛建立，在功能表列的 DLL 的 c + + 應用程式選擇**檔案**，**新增**，**專案**。

1. 在左窗格中**新專案**對話方塊中，選取**Win32**下**已安裝**，**範本**， **Visual c + +**. 在中央窗格中，選取 [Win32 主控台應用程式] 。 指定專案的名稱`MathClient`，請在**名稱**編輯方塊。

   ![用戶端專案的名稱，](media/mathclient-project-name.png "用戶端專案的名稱")

1. 選擇**確定**按鈕以關閉**新專案**對話方塊，並開始**Win32 應用程式精靈**。 在 [Win32 應用程式精靈]  對話方塊的 [概觀]  頁面上，選擇 [下一步]  按鈕。

1. 在**應用程式設定**頁面的 **應用程式類型**，選取**主控台應用程式**如果未選取。

1. 選擇 [完成]  按鈕以建立專案。

當精靈完成時，則會為您建立的最小的主控台應用程式專案。 主要原始程式檔的名稱是您先前輸入專案名稱相同。 在此範例中，它會命名為**MathClient.cpp**。 您可以建置它，但它不會使用您的 DLL。

接下來，若要在您的程式碼中呼叫 MathLibrary 函式，您的專案必須包含 MathLibrary.h 檔案。 您可以將此標頭檔複製到用戶端應用程式專案，然後將它加入至專案做為現有的項目。 這可以是協力廠商程式庫的理想選擇。 不過，如果您正在的程式碼上為您的 DLL 在相同的時間做為您的用戶端，，可能會導致不會反映在另一個標頭檔中的變更。 若要避免這個問題，您可以變更**其他 Include 目錄**原始的標頭路徑包括在內的專案中的路徑。

### <a name="to-add-the-dll-header-to-your-include-path"></a>若要加入至 DLL 標頭您 include 路徑

1. 開啟**屬性頁**對話方塊的  **MathClient**專案。

1. 在**組態**下拉式清單方塊中，選取**所有組態**如果未選取。

1. 在左窗格中，選取**一般**下**組態屬性**， **C/c + +**。

1. 在 [屬性] 窗格中，選取下拉式清單控制項旁**其他 Include 目錄**編輯方塊中，然後選擇**編輯**。

   ![編輯其他 Include 目錄屬性](media/mathclient-additional-include-directories-property.png "編輯其他 Include 目錄屬性")

1. 在上方窗格中按兩下**其他 Include 目錄**對話方塊，讓編輯控制項。

1. 在編輯控制項中，指定的位置路徑**MathLibrary.h**標頭檔。 在此情況下，您可以使用相對路徑：

   `..\..\MathLibrary\MathLibrary`

   ![加入 [其他 Include 目錄] 屬性中的標頭位置](media/mathclient-additional-include-directories.png "將標頭位置加入至 [其他 Include 目錄] 屬性")

1. 一旦您輸入的路徑中的標頭檔**其他 Include 目錄**對話方塊方塊中，選擇**確定**按鈕回到**屬性頁**對話方塊中，和然後選擇 **確定**按鈕以儲存您的變更。

您現在可以包含**MathLibrary.h**檔，並以它在用戶端應用程式中宣告的函式。 取代內容**MathClient.cpp**使用這個程式碼：

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "stdafx.h"
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

此程式碼可以編譯，但沒有連結，因為連結器找不到尚未建置應用程式所需的匯入程式庫。 連結器必須能夠找到 MathLibrary.lib 檔案已成功連結。 您必須藉由設定 MathLibrary.lib 檔案將加入至組建**其他相依性**屬性。 同樣地，您可以將程式庫檔案複製到用戶端應用程式專案，但程式庫和用戶端應用程式正在開發過程中，如果，可能會導致不會反映在另一個複本中的變更。 若要避免這個問題，您可以變更**其他程式庫目錄**包含原始程式庫的路徑，當您將連結的專案中的路徑。

### <a name="to-add-the-dll-import-library-to-your-project"></a>DLL 匯入程式庫加入您的專案

1. 開啟**屬性頁**對話方塊的  **MathClient**專案。

1. 在**組態**下拉式清單方塊中，選取**所有組態**如果未選取。

1. 在左窗格中，選取**輸入**下**組態屬性**，**連結器**。 在 [屬性] 窗格中，選取下拉式清單控制項旁**其他相依性**編輯方塊中，然後選擇**編輯**。

   ![編輯其他相依性屬性](media/mathclient-additional-dependencies-property.png "編輯其他相依性屬性")

1. 在**其他相依性** 對話方塊中，加入`MathLibrary.lib`中最上方的清單中，編輯控制項。

   ![新增程式庫相依性](media/mathclient-additional-dependencies.png "新增程式庫相依性")

1. 選擇**確定**回到**屬性頁** 對話方塊。

1. 在左窗格中，選取**一般**下**組態屬性**，**連結器**。 在 [屬性] 窗格中，選取下拉式清單控制項旁**其他程式庫目錄**編輯方塊中，然後選擇**編輯**。

   ![編輯其他程式庫目錄屬性](media/mathclient-additional-library-directories-property.png "編輯其他程式庫目錄屬性")

1. 在上方窗格中按兩下**其他程式庫目錄**對話方塊，讓編輯控制項。 在編輯控制項中，指定的位置路徑**MathLibrary.lib**檔案。 輸入此值，以使用適用於偵錯和發行組建的巨集：

   `..\..\MathLibrary\$(IntDir)`

   ![新增程式庫目錄](media/mathclient-additional-library-directories.png "新增程式庫目錄")

1. 一旦您輸入的路徑中的程式庫檔案**其他程式庫目錄**對話方塊方塊中，選擇 **確定**按鈕以返回至 **屬性頁**對話方塊。

您的用戶端應用程式現在可以編譯並連結成功，但它仍沒有執行所需要的所有項目。 當作業系統載入您的應用程式時，它會尋找 MathLibrary DLL。 如果它在某些系統目錄、 環境路徑或本機應用程式目錄中找不到 DLL，載入就會失敗。 若要避免這個問題的方法之一是將 DLL 複製到目錄，其中包含用戶端可執行檔建置程序的一部分。 若要複製 DLL，您可以加入**建置後事件**至您的專案，來加入命令，將 DLL 複製到組建輸出目錄。 只有當它遺漏或已變更，且使用巨集與您的設定正確的偵錯或其他位置，複製將 DLL 複製此處指定的命令。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>將 DLL 複製在建置後事件

1. 開啟**屬性頁**對話方塊的  **MathClient**如果尚未開啟專案。

1. 在 [組態] 下拉式清單方塊中，選取**所有組態**如果未選取。

1. 在左窗格中，選取**建置後事件**下**組態屬性**，**建置事件**。

1. 在 屬性 窗格中，選取 編輯控制項中的**命令列**欄位，並接著輸入下列命令：

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![加入建置後命令](media/mathclient-post-build-command-line.png "加入建置後命令")

1. 選擇**確定**按鈕可以將您的變更儲存在專案屬性。

現在您的用戶端應用程式已經做好建置並執行。 建置應用程式，選擇**建置**，**建置方案**功能表列上。 **輸出**Visual Studio 中的視窗應該包含像下面這樣：

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

恭喜，您已建立的應用程式，在 DLL 中呼叫函式。 現在執行應用程式，請參閱其用途。 在功能表列上選擇 **偵錯**，**啟動但不偵錯**。 Visual Studio 會開啟命令視窗執行程式。 輸出的最後一個部分應該看起來像這樣：

![啟動用戶端應用程式，但不偵錯](media/mathclient-run-without-debugging.png "啟動用戶端應用程式，但不偵錯")

按任意鍵關閉命令視窗。

既然您已建立 DLL 和用戶端應用程式，您可以試驗。 請嘗試在用戶端應用程式的程式碼中設定中斷點，偵錯工具中執行應用程式。 當您逐步執行程式庫呼叫，會發生什麼事，請參閱。 其他函式加入至程式庫，或撰寫您的 DLL 會使用另一個用戶端應用程式。

當您部署您的應用程式時，您也必須部署的 Dll，它會使用。 最簡單的方式，可讓您建立或包含的 Dll 來自第三方使用您的應用程式也就是將它們放在與您的應用程式相同的目錄是*應用程式本機部署*。 如需有關部署的詳細資訊，請參閱[部署 Visual c + +](..\ide\deployment-in-visual-cpp.md)。

## <a name="see-also"></a>請參閱

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)  
[部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)  
[逐步解說：部署程式 (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
[從 Visual Basic 應用程式呼叫 DLL 函式](../build/calling-dll-functions-from-visual-basic-applications.md)