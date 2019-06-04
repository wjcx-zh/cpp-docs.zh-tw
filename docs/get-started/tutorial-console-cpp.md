---
title: 建立 C++ 主控台應用程式專案
description: 在 Visual C++ 中建立 Hello World 主控台應用程式及計算機應用程式
ms.custom: mvc
ms.date: 05/28/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 9fc5508b68c8e206e76ead08ddb8015dd5133256
ms.sourcegitcommit: 18f535a6c4cfe58362ed56599b1a875ee71ff6aa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66410766"
---
# <a name="create-a-c-console-app-project"></a>建立 C++ 主控台應用程式專案

::: moniker range=">=vs-2019"

通常 C++ 程式設計師的起點都是 "Hello, world!" 應用程式 (在命令列上執行)。 這就是您將在本文中利用 Visual Studio 建立的項目，然後我們會再挑戰更進階的項目：計算機應用程式。

## <a name="prerequisites"></a>必要條件

- 安裝 Visual Studio 和 [使用 C++ 開發傳統型應用程式]  工作負載，並在您的電腦上執行。 若尚未安裝，請參閱 [Install C++ support in Visual Studio](../build/vscpp-step-0-installation.md) (在 Visual Studio 中安裝 C++ 支援)。

## <a name="create-your-app-project"></a>建立您的應用程式專案

Visual Studio 會使用「專案」  來組織應用程式的程式碼，並使用「解決方案」  來組織專案。 專案包含用來建置您應用程式的所有選項、組態和規則。 它也會管理所有專案之檔案與任何外部檔案間的關聯性。 若要建立您的應用程式，首先，您會建立新的專案及解決方案。

1. 如果您剛開始使用 Visual Studio，會看到 [Visual Studio 2019] 對話方塊。 選擇 [建立新專案]  以開始使用。

   ![[Visual Studio 2019] 初始對話方塊](./media/calc-vs2019-initial-dialog.png "[Visual Studio 2019] 初始對話方塊")

   否則，在 Visual Studio 的功能表列上，選擇 [檔案]   > [新增]   > [專案]  。 [建立新專案]  視窗會隨即開啟。

1. 在專案範本清單中，選擇 [主控台應用程式]  ，然後選擇 [下一步]  。

   ![選擇 [主控台應用程式] 範本](./media/calc-vs2019-choose-console-app.png "選擇 [主控台應用程式] 範本")

   > [!Important]
   > 請務必選擇 C++ 版本的**主控台應用程式**範本。 它有 **C++** 、**Windows** 和 **Console** 標籤，角落有 "++" 圖示。

1. 在 [設定新專案]  對話方塊中，選取 [專案名稱]  編輯方塊中，將您的新專案命名為 *CalculatorTutorial*，然後選擇 [建立]  .

   ![在 [設定新專案] 對話方塊中命名專案](./media/calc-vs2019-name-your-project.png "在 [設定新專案] 對話方塊中命名專案")

   會建立空白的 C++ Windows 主控台應用程式。 主控台應用程式會使用 Windows 主控台視窗來顯示輸出並接受使用者輸入。 在 Visual Studio 中，一個編輯器視窗隨即開啟，並顯示產生的程式碼：

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>驗證您新的應用程式可以建置及執行

新 Windows 主控台應用程式範本會建立簡易的 C++ "Hello World" 應用程式。 此時，您會看到 Visual Studio 如何直接從 IDE 建置及執行您建立的應用程式。

1. 若要建置您的專案，請從 [建置]  功能表中選擇 [建置方案]  。 [輸出]  視窗會顯示建置過程的結果。

   ![建置專案](./media/calc-vs2019-build-your-project.png "建置專案")

1. 若要執行程式碼，請在功能表列上，選擇 [偵錯]  、[啟動但不偵錯]  。

   ![啟動專案](./media/calc-vs2019-hello-world-console.png "啟動專案")

   主控台視窗會隨即開啟並執行您的應用程式。 當您在 Visual Studio 中啟動主控台應用程式時，它會執行您的程式碼，然後印出「按任意鍵即可關閉此視窗」。 。 。」。 讓您可以有機會查看輸出。 恭喜您！ 您已在 Visual Studio 中建立了您的第一個 "Hello, world!" 主控台應用程式！

1. 請按任意鍵關閉主控台視窗並返回 Visual Studio。

您現在已具備了在每一項變更之後建置及執行您應用程式的工具，可驗證程式碼仍依照您預期的方式運作。 稍後，我們將示範如何在無法正常運作時進行偵錯。

## <a name="edit-the-code"></a>編輯程式碼

現在，讓我們將此範本中的程式碼轉換成計算機應用程式。

1. 在 *CalculatorTutorial.cpp* 檔案中，編輯程式碼，使其與此範例相符：

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > 了解程式碼：
   >
   > - `#include` 陳述式可讓您參考位於其他檔案中的程式碼。 有時候，您可能會看到檔案名稱以角括弧 ( **\<\>** ) 括住；其他時候，則會以引號 ( **" "** ) 括住。 一般情況下，角括弧會在參考 C++ 標準程式庫時使用，引號則用於其他檔案。
   > - `using namespace std;` 這一行則會告知編譯器，預期在此檔案中使用來自 C++ 標準程式庫的功能。 若沒有這一行，每個來自程式庫的關鍵字都必須在開頭加上 `std::` 以表示其範圍。 例如，若沒有該行，每個對 `cout` 的參考都必須寫成 `std::cout`。 新增 `using` 陳述式的目的是為了讓程式碼看起來更乾淨。
   > - `cout` 關鍵字則用於印出至 C++ 中的標準輸出。 **\<\<** 運算子則會告知編譯器，將此運算子右側的任何事物傳送至標準輸出。
   > - **endl** 關鍵字則像是 Enter 鍵，它會結束這一行並將游標移到下一行。 將 `\n` 放在字串內部 (即包含在 "" 中) 以進行相同操作是較佳的做法，因為 `endl` 會排清緩衝區而可能影響程式的效能，但由於這個應用程式很小，所以我們在此處使用 `endl` 來改善可讀性。
   > - 所有 C++ 陳述式都必須以分號結尾，且所有的 C++ 應用程式都必須包含一個 `main()` 函式。 此函式是程式在開始時執行的部分。 所有程式碼都必須要能夠從 `main()` 存取，才能使用。

1. 若要儲存檔案，請按下 **Ctrl+S**，或選擇靠近 IDE 頂端的**儲存**圖示，即功能表列下方工具列中的磁碟片圖示。

1. 若要執行應用程式，請按下 **Ctrl+F5**，或前往 [偵錯]  功能表，然後選擇 [啟動但不偵錯]  。 您應該會看到一個主控台視窗出現，它顯示程式碼中指定的文字。

1. 當您完成時，請關閉主控台視窗。

## <a name="add-code-to-do-some-math"></a>新增程式碼來執行數學運算

是時候新增一些數學邏輯了。

### <a name="to-add-a-calculator-class"></a>新增 Calculator 類別

1. 前往 [專案]  功能表，然後選擇 [新增類別]  。 在 [類別名稱]  編輯方塊中，輸入 *Calculator*。 選擇 [確定]  。 會將兩個新檔案新增到您的專案。 若要一次儲存您所有變更的檔案，請按 **Ctrl+Shift+S**。 它是 [檔案]   > [全部儲存]  的鍵盤快速鍵。 [全部儲存]  也有一個工具列按鈕，即兩個磁碟片的圖示，您可在 [儲存]  按鈕的旁邊找到。 一般情況下，頻繁地進行 [全部儲存]  是良好的做法，因為這樣可避免您在儲存時遺漏任何檔案。

   ![建立 Calculator 類別](./media/calc-vs2019-create-calculator-class.png "建立 Calculator 類別")

   類別就像是物件的藍圖，可進行某些操作。 在此案例中，我們會定義一個計算機及其運作的方式。 您在上方使用的 [新增類別精靈]  會建立 .h 及 .cpp 檔案，且其名稱和類別皆相同。 您可以在 IDE 側邊可看到的 [方案總管]  視窗中，看見您專案檔案的完整清單。 若您沒有看到視窗，您可以從功能表列開啟它：選擇 [檢視]   > [方案總管]  。

   ![方案總管](./media/calc-vs2019-solution-explorer.png "方案總管")

   您現在應該會在編輯器中擁有三個開啟的索引標籤：*CalculatorTutorial.cpp*、*Calculator.h*，以及 *Calculator.cpp*。 若您不小心關閉了其中一個，您可以在 [方案總管]  視窗中按兩下它來重新開啟。

1. 在 **Calculator.h** 中，移除所產生的 `Calculator();` 和 `~Calculator();` 這兩行，因為您在此處不需要它們。 接下來，請新增下列這行程式碼，使其看起來與下列內容相似：

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > 了解程式碼
   >
   > - 您新增的這一行會宣告一個稱為 `Calculate` 的新函式，我們會使用此函式來進行數學運算，包含加、減、乘及除。
   > - C++ 程式碼會整理成「標頭」  (.h) 檔案及「來源」  (.cpp) 檔案。 各種編譯器還支援數種其他副檔名，但這些是您需了解的主要項目。 函式和變數通常會經過「宣告」  ，即在標頭檔中提供名稱和型別，然後在來源檔案中「實作」  (或提供定義)。 若要存取另一個檔案中定義的程式碼，您可以使用 `#include "filename.h"`，其中 'filename.h' 是宣告您欲使用變數或函式的檔案名稱。
   > - 您刪除之兩行會宣告類別的「建構函式」  及「解構函式」  。 針對如此範例的簡單類別，編譯器會為您建立它們，且其使用用途也不在本教學課程的範圍內。
   > - 將您的程式碼根據其用途整理成不同檔案是一種良好做法，因為這可讓您在稍後需要的時候輕易地尋找它們。 在我們的案例中，我們將 `Calculator` 類別與包含 `main()` 函式的檔案分開來定義，但我們計劃在 `main()` 中參考 `Calculator` 類別。

1. 您會在 `Calculate` 的下方看到綠色的彎曲箭號。 這是因為我們尚未在 .cpp 檔案中定義 `Calculate` 函式。 暫留在文字上，按一下彈出的燈泡 (在此例中是螺絲起子)，然後選擇 [在 Calculator.cpp 中建立 'Calculate' 的定義]  。

   ![建立 Calculate 的定義](./media/calc-vs2019-create-definition.png "建立 Calculate 的定義")

   快顯視窗隨即出現，可讓您預覽在其他檔案中進行的程式碼變更。 程式碼已新增至 *Calculator.cpp*。

   ![具有 Calculate 定義的快顯功能表](./media/calc-vs2019-pop-up-definition.png "具有 Calculate 定義的快顯功能表")

   目前，它只會傳回 0.0。 讓我們進行變更。 按 **Esc** 來關閉快顯視窗。

1. 在編輯器視窗中切換至 *Calculator.cpp* 檔案。 移除 `Calculator()` 和 `~Calculator()` 這兩個區段 (如同您在 .h 檔案中所進行的操作)，並將下列程式碼新增至 `Calculate()`：

    ```cpp
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > 了解程式碼
   >
   > - `Calculate` 函式會取用一個數字、一個運算子及第二個數字，然後在數字上執行所要求的運算。
   > - Switch 陳述式會檢查提供的運算子為何，並只執行對應至該運算的案例。 default: 案例是一種後援案例，若使用者鍵入不接受的運算子，即會使用此案例以避免中斷程式。 一般情況下，使用更簡潔的方式處理無效使用者輸入會是最佳做法，但這不在本教學課程的範圍內。
   > - `double` 關鍵字表示支援小數點的一種數字類型。 如此一來，計算機便能夠同時處理小數點及整數的數學運算。 `Calculate` 函式必須一律傳回這種數字，因為程式碼開頭的 `double` (表示函式的傳回型別) 如此要求，而這也是為什麼即使在預設案例中，我們也傳回 0.0。
   > - .h 檔案會宣告函式的「原型」  ，預先告知編譯器其需要的參數，以及該預期的傳回型別為何。 .cpp 檔案則包含函式所有的實作詳細資料。

如果您此時再次建置並執行程式碼，其仍會在詢問要執行哪項作業後結束。 接下來，您會修改 `main` 函式來進行一些運算。

### <a name="to-call-the-calculator-class-member-functions"></a>呼叫 Calculator 類別成員函式

1. 現在讓我們來更新 *CalculatorTutorial.cpp* 中的 `main` 函式：

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > 了解程式碼
   >
   > - 由於 C++ 程式一律會從 `main()` 函式開始，而我們需要從該處呼叫我們的其他程式碼，因此需要 `#include` 陳述式。
   > - 我們宣告了某些初始變數 `x`、`y`、`oper` 和 `result`，分別用來儲存第一個數字、第二個數字、運算子及最終結果。 提供它們某些初始值以避免未定義的行為是一種良好做法，而我們也在此處進行了這項操作。
   > - `Calculator c;` 這一行會宣告一個名為 'c' 的物件，作為 `Calculator` 類別的執行個體。 類別本身只是計算機運作的藍圖；物件則是進行數學運算的特定計算機。
   > - `while (true)` 陳述式是一種迴圈。 只要 `()` 內的條件為 True，迴圈內的程式碼就會繼續重複執行。 由於此處條件直接列為 `true`，代表條件一律為 True，因此這個迴圈會永遠執行下去。 若要關閉程式，使用者必須手動關閉主控台視窗。 否則，程式一律都會等待新的輸入。
   > - `cin` 關鍵字則用於接受使用者的輸入。 假設使用者輸入符合必要規格，輸入串流便能處理在主控台視窗中輸入的文字行，並依序將它放在每個列出的變數內。 您可以修改此行來接受不同類型的輸入 (例如兩個以上的數字)，雖然 `Calculate()` 函式也需要更新才能進行處理。
   > - `c.Calculate(x, oper, y);` 運算式會呼叫先前定義的 `Calculate` 函式，並提供輸入的輸入值。 函式接著會傳回儲存在 `result` 中的數字。
   > - 最後，`result` 會印出到主控台，讓使用者看見運算的結果。

### <a name="build-and-test-the-code-again"></a>再次建置並測試程式碼

現在，是時候再次測試程式以確認所有功能皆正常運作了。

1. 請按 **Ctrl+F5** 來重新建置並啟動應用程式。

1. 輸入 `5 + 5`，然後按 **Enter**。 驗證結果為 10。

   ![5 + 5 的結果](./media/calc-vs2019-five-plus-five.png "5 + 5 的結果")

## <a name="debug-the-app"></a>偵錯應用程式

因為使用者可以在主控台視窗中鍵入任何內容，讓我們確認計算機能依照預期的方式處理某些輸入。 相較於執行程式，我們可以改為針對它進行偵錯，讓我們可以詳細地逐步檢查其進行的作業。

### <a name="to-run-the-app-in-the-debugger"></a>在偵錯工具中執行應用程式

1. 在 `result = c.Calculate(x, oper, y);` 這一行設定中斷點，即在向使用者要求輸入之後。 若要設定中斷點，請按一下編輯器視窗左邊緣灰色垂直列中的行。 會出現紅色的點。

   ![設定中斷點](./media/calc-vs2019-set-breakpoint.png "設定中斷點")

   現在，當我們偵錯程式時，它會一律在該行暫停執行。 我們已初步了解程式適用於簡單案例。 因為我們不想要每次都暫停執行，讓我們把中斷點設定為選擇性。

1. 請在代表中斷點的紅點上按一下滑鼠右鍵，然後選擇 [條件]  。 在條件的編輯方塊中，輸入 `(y == 0) && (oper == '/')`。 當您完成時，請選擇 [關閉]  按鈕。 條件會自動儲存。

   ![設定條件式中斷點](./media/calc-vs2019-conditional-breakpoint.png "設定條件式中斷點")

   現在我們會在使用者嘗試除以 0 時在中斷點上暫停執行。

1. 若要偵錯程式，請按 **F5**，或選擇 [本機 Windows 偵錯工具]  工具列按鈕 (有綠色箭頭圖示)。 在您的主控台應用程式中，若您輸入像是 "5 - 0" 的內容，程式會正常運作並繼續執行。 但是，若您鍵入 "10 / 0"，它便會在中斷點暫停。 您甚至可以在運算子及數字間輸入任意數量的空格，因為 `cin` 能夠適當地剖析輸入。

   ![在條件式中斷點暫停](./media/calc-vs2019-debug-breakpoint.png "在條件式中斷點暫停")

### <a name="useful-windows-in-the-debugger"></a>偵錯工具中有用的視窗

在您偵錯程式碼時，您可能會注意到其出現了某些新視窗。 這些視窗可協助您的偵錯體驗。 讓我們看看 [自動變數]  視窗。 [自動變數]  視窗會顯示從至少 3 行以前到目前這一行為止，所使用變數目前的值。 若要查看來自該函式的所有變數，請切換到 [區域變數]  視窗。 您實際上可以在偵錯時直接憑空修改這些變數的值，查看其對程式造成的影響。 在此案例中，我們不會修改它們的值。

   ![[區域變數] 視窗](./media/calc-vs2019-debug-locals.png "[區域變數] 視窗")

您也可以暫留在程式碼本身的變數上，查看它們在目前暫停執行位置上的目前值。 請按一下編輯器視窗，確認該視窗仍擁有焦點。

   ![暫留以檢視目前的變數值](./media/calc-vs2019-hover-tooltip.png "暫留以檢視目前的變數值")

### <a name="to-continue-debugging"></a>繼續偵錯

1. 左側黃線會顯示目前的執行點。 目前的行會呼叫 `Calculate`，因此請按 **F11** 來 [逐步執行]  函式。 您會看到您進入了 `Calculate` 函式的主體。 使用 [逐步執行]  時請謹慎，若執行太多次，可能會浪費許多時間。 它會進入您在所在行中使用的所有程式碼，包括標準程式庫函式。

1. 現在當執行點位於 `Calculate` 函式的開頭時，請按 **F10** 來移動到程式執行的下一行。 **F10** 又稱為 [不進入函式]  。 您可以使用 [不進入函式]  來從一行移動到下一行，而無須了解該行每個部分所發生的事件。 一般情況下，建議您使用 [不進入函式]  而非 [逐步執行]  ，除非您想要更深入地了解從其他位置呼叫的程式碼 (如同您為了觸達 `Calculate` 主體所進行的操作)。

1. 繼續使用 **F10** 以**不進入**每一行函式，直到您回到另一個檔案的 `main()`，並在 `cout` 行上停止。

   看起來程式正如預期般運作：它會接收第一個數字，然後除以第二個數字。 在 `cout` 行上，在 `result` 變數上暫留或在 [自動變數]  視窗中查看 `result`。 您將會看到其值列出為 "inf"，這看起來不正確，因此讓我們修正它吧。 `cout` 行只會輸出任何儲存在 `result` 中的值，因此當您使用 **F10** 前往下一行時，會顯示主控台視窗：

   ![除以零的結果](./media/calc-vs2019-divide-by-zero-fail.png "除以零的結果")

   此結果是因為除以零的結果未定義，因此程式針對所要求運算沒有數值答案。

### <a name="to-fix-the-divide-by-zero-error"></a>修正「除以零」錯誤

讓我們以更好的方式來處理「除以零」，讓使用者能了解問題。

1. 請在 *CalculatorTutorial.cpp* 中進行下列變更。 (歸功於稱為 [編輯後繼續]  的功能，您可以在編輯的時候讓程式繼續執行)：

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. 現在，請按 **F5**一次。 程式會繼續執行，直到需要暫停要求使用者輸入為止。 再次輸入 `10 / 0`。 現在會印出更有幫助的訊息。 程式會向使用者要求更多輸入，且程式會繼續正常執行。

   ![變更後的最終結果](./media/calc-vs2019-final-verification.png "變更後的最終結果")

   > [!Note]
   > 當您在處於偵錯模式的期間編輯程式碼時，可能會有程式碼過時的風險。 這會在偵錯工具仍在執行您的舊版程式碼，且尚未使用您的變更進行更新時發生。 偵錯工具會在發生此情況時彈出一個對話方塊提醒您。 有時候，您可能需要按 **F5** 來重新整理正在執行的程式碼。 特別是當執行點正位於函式中，而您在該函式的內部進行變更時，您將需要跳出函式，然後再次進入該函式來取得更新後的程式碼。 若因為某些原因仍無法正常運作，且您看到了錯誤訊息，您可以按一下 IDE 頂端功能表下方工具列中的紅色方塊來停止偵錯，然後按 **F5** 來再次啟動偵錯，或選擇工具列上停止按鈕旁邊的綠色 [執行] 箭頭來進行。

   > 了解執行和偵錯快速鍵
   >
   > - **F5** (或 [偵錯]   > [開始偵錯]  ) 會啟動偵錯工作階段 (若沒有正在使用中的工作階段) 並執行程式，直到到達中斷點或程式需要使用者進行輸入。 若不需要使用者輸入且沒有可到達的中斷點，程式會在完成執行時終止並關閉主控台視窗本身。 若您有類似 "Hello World" 的程式要執行，請使用 **Ctrl+F5** 或設定中斷點，然後按 **F5** 來將視窗維持在開啟狀態。
   > - **Ctrl+F5** (或 [偵錯]   > [啟動但不偵錯]  ) 會執行應用程式，而不會進入偵錯模式。 這比偵錯稍快，且主控台視窗會在程式完成執行時維持在開啟狀態。
   > - **F10** (又稱為 [不進入函式]  ) 可讓您逐一且逐行查看程式碼，並視覺化程式碼執行方式及每個執行步驟中的變數值為何。
   > - **F11** (又稱為 [逐步執行]  ) 的運作方式與 [不進入函式]  相似，但它會進入任何在執行行上呼叫的函式。 例如，當執行的行呼叫一個函式時，按 **F11** 會將指標移動到函式主體，讓您可以跟隨所執行的函式程式碼，然後回到您開始的那一行。 按 **F10** 可不進入函式，直接移動到下一行；函式仍會獲得呼叫，但程式不會暫停並顯示其正在進行的操作。

### <a name="close-the-app"></a>關閉應用程式

- 若仍在執行中，請關閉計算機應用程式的主控台視窗。

## <a name="the-finished-app"></a>完成的應用程式

恭喜您！ 您已完成計算機應用程式的程式碼，並在 Visual Studio 中建置及偵錯。

## <a name="next-steps"></a>後續步驟

[深入了解適用於 C++ 的 Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end

::: moniker range="<vs-2019"

通常 C++ 程式設計師的起點都是 "Hello, world!" 應用程式 (在命令列上執行)。 這就是您將在本文中利用 Visual Studio 建立的項目，然後我們會再挑戰更進階的項目：計算機應用程式。

## <a name="prerequisites"></a>必要條件

- 安裝 Visual Studio 和 [使用 C++ 開發傳統型應用程式]  工作負載，並在您的電腦上執行。 若尚未安裝，請參閱 [Install C++ support in Visual Studio](../build/vscpp-step-0-installation.md) (在 Visual Studio 中安裝 C++ 支援)。

## <a name="create-your-app-project"></a>建立您的應用程式專案

Visual Studio 會使用「專案」  來組織應用程式的程式碼，並使用「解決方案」  來組織專案。 專案包含用來建置您應用程式的所有選項、組態和規則。 它也會管理所有專案之檔案與任何外部檔案間的關聯性。 若要建立您的應用程式，首先，您會建立新的專案及解決方案。

1. 在 Visual Studio 的功能表列上，選擇 [檔案]   > [新增]   > [專案]  。 [新增專案]  視窗隨即開啟。

2. 在左邊的側邊欄上，確認已選取 [Visual C++]  。 在中央，選擇 [Windows 主控台應用程式]  。

3. 在底部的 [名稱]  編輯方塊中，將新的專案命名為 *CalculatorTutorial*，然後選擇 [確定]  。

   ![[新增專案] 對話方塊](./media/calculator-new-project-dialog.png "[新增專案] 對話方塊")

   會建立空白的 C++ Windows 主控台應用程式。 主控台應用程式會使用 Windows 主控台視窗來顯示輸出並接受使用者輸入。 在 Visual Studio 中，一個編輯器視窗隨即開啟，並顯示產生的程式碼：

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n"; 
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started: 
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>驗證您新的應用程式可以建置及執行

新 Windows 主控台應用程式範本會建立一個簡單的 C++ "Hello World" 應用程式。 此時，您會看到 Visual Studio 如何直接從 IDE 建置及執行您建立的應用程式。

1. 若要建置您的專案，請從 [建置]  功能表中選擇 [建置方案]  。 [輸出]  視窗會顯示建置過程的結果。

   ![建置專案](./media/calculator-initial-build-output.png "建置專案")

1. 若要執行程式碼，請在功能表列上，選擇 [偵錯]  、[啟動但不偵錯]  。

   ![啟動專案](./media/calculator-hello-world-console.png "啟動專案")

   主控台視窗會隨即開啟並執行您的應用程式。 當您在 Visual Studio 中啟動主控台應用程式時，它會執行您的程式碼，然後印出「請按任意鍵繼續 。 。」。 讓您可以有機會查看輸出。 恭喜您！ 您已在 Visual Studio 中建立了您的第一個 "Hello, world!" 主控台應用程式！

1. 請按任意鍵關閉主控台視窗並返回 Visual Studio。

您現在已具備了在每一項變更之後建置及執行您應用程式的工具，可驗證程式碼仍依照您預期的方式運作。 稍後，我們將示範如何在無法正常運作時進行偵錯。

## <a name="edit-the-code"></a>編輯程式碼

現在，讓我們將此範本中的程式碼轉換成計算機應用程式。

1. 在 *CalculatorTutorial.cpp* 檔案中，編輯程式碼，使其與此範例相符：

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > 了解程式碼：
   >
   > - `#include` 陳述式可讓您參考位於其他檔案中的程式碼。 有時候，您可能會看到檔案名稱以角括弧 ( **\<\>** ) 括住；其他時候，則會以引號 ( **" "** ) 括住。 一般情況下，角括弧會在參考 C++ 標準程式庫時使用，引號則用於其他檔案。
   > - `#include "pch.h"` (或較舊版本 Visual Studio 中的 `#include "stdafx.h"`) 這一行則會參考稱為先行編譯標頭檔的檔案。 這通常會由專業程式設計師使用，用來改善編譯時間，但這不在本教學課程的範圍內。
   > - `using namespace std;` 這一行則會告知編譯器，預期在此檔案中使用來自 C++ 標準程式庫的功能。 若沒有這一行，每個來自程式庫的關鍵字都必須在開頭加上 `std::` 以表示其範圍。 例如，若沒有該行，每個對 `cout` 的參考都必須寫成 `std::cout`。 新增 `using` 陳述式的目的是為了讓程式碼看起來更乾淨。
   > - `cout` 關鍵字則用於印出至 C++ 中的標準輸出。 **\<\<** 運算子則會告知編譯器，將此運算子右側的任何事物傳送至標準輸出。
   > - **endl** 關鍵字則像是 Enter 鍵，它會結束這一行並將游標移到下一行。 將 `\n` 放在字串內部 (即包含在 "" 中) 以進行相同操作是較佳的做法，因為 `endl` 會排清緩衝區而可能影響程式的效能，但由於這個應用程式很小，所以我們在此處使用 `endl` 來改善可讀性。
   > - 所有 C++ 陳述式都必須以分號結尾，且所有的 C++ 應用程式都必須包含一個 `main()` 函式。 此函式是程式在開始時執行的部分。 所有程式碼都必須要能夠從 `main()` 存取，才能使用。

1. 若要儲存檔案，請按下 **Ctrl+S**，或選擇靠近 IDE 頂端的**儲存**圖示，即功能表列下方工具列中的磁碟片圖示。

1. 若要執行應用程式，請按下 **Ctrl+F5**，或前往 [偵錯]  功能表，然後選擇 [啟動但不偵錯]  。 若您看到 [此專案已過期]  快顯訊息，您可以選取 [不要再顯示此對話方塊]  ，然後選擇 [是]  來建置您的應用程式。 您應該會看到一個主控台視窗出現，它顯示程式碼中指定的文字。

   ![建置並啟動您的應用程式](./media/calculator-first-launch.gif "建置並啟動您的應用程式")

1. 當您完成時，請關閉主控台視窗。

## <a name="add-code-to-do-some-math"></a>新增程式碼來執行數學運算

是時候新增一些數學邏輯了。

### <a name="to-add-a-calculator-class"></a>新增 Calculator 類別

1. 前往 [專案]  功能表，然後選擇 [新增類別]  。 在 [類別名稱]  編輯方塊中，輸入 *Calculator*。 選擇 [確定]  。 會將兩個新檔案新增到您的專案。 若要一次儲存您所有變更的檔案，請按 **Ctrl+Shift+S**。 它是 [檔案]   > [全部儲存]  的鍵盤快速鍵。 [全部儲存]  也有一個工具列按鈕，即兩個磁碟片的圖示，您可在 [儲存]  按鈕的旁邊找到。 一般情況下，頻繁地進行 [全部儲存]  是良好的做法，因為這樣可避免您在儲存時遺漏任何檔案。

   ![建立 Calculator 類別](./media/calculator-create-class.gif "建立 Calculator 類別")

   類別就像是物件的藍圖，可進行某些操作。 在此案例中，我們會定義一個計算機及其運作的方式。 您在上方使用的 [新增類別精靈]  會建立 .h 及 .cpp 檔案，且其名稱和類別皆相同。 您可以在 IDE 側邊可看到的 [方案總管]  視窗中，看見您專案檔案的完整清單。 若您沒有看到視窗，您可以從功能表列開啟它：選擇 [檢視]   > [方案總管]  。

   ![方案總管](./media/calculator-solution-explorer.png "方案總管")

   您現在應該會在編輯器中擁有三個開啟的索引標籤：*CalculatorTutorial.cpp*、*Calculator.h*，以及 *Calculator.cpp*。 若您不小心關閉了其中一個，您可以在 [方案總管]  視窗中按兩下它來重新開啟。

1. 在 **Calculator.h** 中，移除所產生的 `Calculator();` 和 `~Calculator();` 這兩行，因為您在此處不需要它們。 接下來，請新增下列這行程式碼，使其看起來與下列內容相似：

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > 了解程式碼
   >
   > - 您新增的這一行會宣告一個稱為 `Calculate` 的新函式，我們會使用此函式來進行數學運算，包含加、減、乘及除。
   > - C++ 程式碼會整理成「標頭」  (.h) 檔案及「來源」  (.cpp) 檔案。 各種編譯器還支援數種其他副檔名，但這些是您需了解的主要項目。 函式和變數通常會經過「宣告」  ，即在標頭檔中提供名稱和型別，然後在來源檔案中「實作」  (或提供定義)。 若要存取另一個檔案中定義的程式碼，您可以使用 `#include "filename.h"`，其中 'filename.h' 是宣告您欲使用變數或函式的檔案名稱。
   > - 您刪除之兩行會宣告類別的「建構函式」  及「解構函式」  。 針對如此範例的簡單類別，編譯器會為您建立它們，且其使用用途也不在本教學課程的範圍內。
   > - 將您的程式碼根據其用途整理成不同檔案是一種良好做法，因為這可讓您在稍後需要的時候輕易地尋找它們。 在我們的案例中，我們將 `Calculator` 類別與包含 `main()` 函式的檔案分開來定義，但我們計劃在 `main()` 中參考 `Calculator` 類別。

1. 您會在 `Calculate` 的下方看到綠色的彎曲箭號。 這是因為我們尚未在 .cpp 檔案中定義 `Calculate` 函式。 暫留在文字上，按一下彈出的燈泡，然後選擇 [在 Calculator.cpp 中建立 'Calculate' 的定義]  。 快顯視窗隨即出現，可讓您預覽在其他檔案中進行的程式碼變更。 程式碼已新增至 *Calculator.cpp*。

   ![建立 Calculate 的定義](./media/calculator-create-definition.gif "建立 Calculate 的定義")

   目前，它只會傳回 0.0。 讓我們進行變更。 按 **Esc** 來關閉快顯視窗。

1. 在編輯器視窗中切換至 *Calculator.cpp* 檔案。 移除 `Calculator()` 和 `~Calculator()` 這兩個區段 (如同您在 .h 檔案中所進行的操作)，並將下列程式碼新增至 `Calculate()`：

    ```cpp
    #include "pch.h"
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > 了解程式碼
   >
   > - `Calculate` 函式會取用一個數字、一個運算子及第二個數字，然後在數字上執行所要求的運算。
   > - Switch 陳述式會檢查提供的運算子為何，並只執行對應至該運算的案例。 default: 案例是一種後援案例，若使用者鍵入不接受的運算子，即會使用此案例以避免中斷程式。 一般情況下，使用更簡潔的方式處理無效使用者輸入會是最佳做法，但這不在本教學課程的範圍內。
   > - `double` 關鍵字表示支援小數點的一種數字類型。 如此一來，計算機便能夠同時處理小數點及整數的數學運算。 `Calculate` 函式必須一律傳回這種數字，因為程式碼開頭的 `double` (表示函式的傳回型別) 如此要求，而這也是為什麼即使在預設案例中，我們也傳回 0.0。
   > - .h 檔案會宣告函式的「原型」  ，預先告知編譯器其需要的參數，以及該預期的傳回型別為何。 .cpp 檔案則包含函式所有的實作詳細資料。

如果您此時再次建置並執行程式碼，其仍會在詢問要執行哪項作業後結束。 接下來，您會修改 `main` 函式來進行一些運算。

### <a name="to-call-the-calculator-class-member-functions"></a>呼叫 Calculator 類別成員函式

1. 現在讓我們來更新 *CalculatorTutorial.cpp* 中的 `main` 函式：

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > 了解程式碼
   >
   > - 由於 C++ 程式一律會從 `main()` 函式開始，而我們需要從該處呼叫我們的其他程式碼，因此需要 `#include` 陳述式。
   > - 我們宣告了某些初始變數 `x`、`y`、`oper` 和 `result`，分別用來儲存第一個數字、第二個數字、運算子及最終結果。 提供它們某些初始值以避免未定義的行為是一種良好做法，而我們也在此處進行了這項操作。
   > - `Calculator c;` 這一行會宣告一個名為 'c' 的物件，作為 `Calculator` 類別的執行個體。 類別本身只是計算機運作的藍圖；物件則是進行數學運算的特定計算機。
   > - `while (true)` 陳述式是一種迴圈。 只要 `()` 內的條件為 True，迴圈內的程式碼就會繼續重複執行。 由於此處條件直接列為 `true`，代表條件一律為 True，因此這個迴圈會永遠執行下去。 若要關閉程式，使用者必須手動關閉主控台視窗。 否則，程式一律都會等待新的輸入。
   > - `cin` 關鍵字則用於接受使用者的輸入。 假設使用者輸入符合必要規格，輸入串流便能處理在主控台視窗中輸入的文字行，並依序將它放在每個列出的變數內。 您可以修改此行來接受不同類型的輸入 (例如兩個以上的數字)，雖然 `Calculate()` 函式也需要更新才能進行處理。
   > - `c.Calculate(x, oper, y);` 運算式會呼叫先前定義的 `Calculate` 函式，並提供輸入的輸入值。 函式接著會傳回儲存在 `result` 中的數字。
   > - 最後，`result` 會印出到主控台，讓使用者看見運算的結果。

### <a name="build-and-test-the-code-again"></a>再次建置並測試程式碼

現在，是時候再次測試程式以確認所有功能皆正常運作了。

1. 請按 **Ctrl+F5** 來重新建置並啟動應用程式。

1. 輸入 `5 + 5`，然後按 **Enter**。 驗證結果為 10。

   ![5 + 5 的結果](./media/calculator-five-plus-five.png "5 + 5 的結果")

## <a name="debug-the-app"></a>偵錯應用程式

因為使用者可以在主控台視窗中鍵入任何內容，讓我們確認計算機能依照預期的方式處理某些輸入。 相較於執行程式，我們可以改為針對它進行偵錯，讓我們可以詳細地逐步檢查其進行的作業。

### <a name="to-run-the-app-in-the-debugger"></a>在偵錯工具中執行應用程式

1. 在 `result = c.Calculate(x, oper, y);` 這一行設定中斷點，即在向使用者要求輸入之後。 若要設定中斷點，請按一下編輯器視窗左邊緣灰色垂直列中的行。 會出現紅色的點。

   ![設定中斷點](./media/calculator-set-breakpoint.gif "設定中斷點")

   現在，當我們偵錯程式時，它會一律在該行暫停執行。 我們已初步了解程式適用於簡單案例。 因為我們不想要每次都暫停執行，讓我們把中斷點設定為選擇性。

1. 請在代表中斷點的紅點上按一下滑鼠右鍵，然後選擇 [條件]  。 在條件的編輯方塊中，輸入 `(y == 0) && (oper == '/')`。 當您完成時，請選擇 [關閉]  按鈕。 條件會自動儲存。

   ![設定條件式中斷點](./media/calculator-conditional-breakpoint.gif "設定條件式中斷點")

   現在我們會在使用者嘗試除以 0 時在中斷點上暫停執行。

1. 若要偵錯程式，請按 **F5**，或選擇 [本機 Windows 偵錯工具]  工具列按鈕 (有綠色箭頭圖示)。 在您的主控台應用程式中，若您輸入像是 "5 - 0" 的內容，程式會正常運作並繼續執行。 但是，若您鍵入 "10 / 0"，它便會在中斷點暫停。 您甚至可以在運算子及數字間輸入任意數量的空格，因為 `cin` 能夠適當地剖析輸入。

   ![在條件式中斷點暫停](./media/calculator-debug-conditional.gif "在條件式中斷點暫停")

### <a name="useful-windows-in-the-debugger"></a>偵錯工具中有用的視窗

在您偵錯程式碼時，您可能會注意到其出現了某些新視窗。 這些視窗可協助您的偵錯體驗。 讓我們看看 [自動變數]  視窗。 [自動變數]  視窗會顯示從至少 3 行以前到目前這一行為止，所使用變數目前的值。

   ![[自動變數] 視窗](./media/calculator-autos.png "[自動變數] 視窗")

若要查看來自該函式的所有變數，請切換到 [區域變數]  視窗。 您實際上可以在偵錯時直接憑空修改這些變數的值，查看其對程式造成的影響。 在此案例中，我們不會修改它們的值。

   ![[區域變數] 視窗](./media/calculator-locals.png "[區域變數] 視窗")

您也可以暫留在程式碼本身的變數上，查看它們在目前暫停執行位置上的目前值。 請按一下編輯器視窗，確認該視窗仍擁有焦點。

   ![暫留以檢視目前的變數值](./media/calculator-hover-tooltip.gif "暫留以檢視目前的變數值")

### <a name="to-continue-debugging"></a>繼續偵錯

1. 左側黃線會顯示目前的執行點。 目前的行會呼叫 `Calculate`，因此請按 **F11** 來 [逐步執行]  函式。 您會看到您進入了 `Calculate` 函式的主體。 使用 [逐步執行]  時請謹慎，若執行太多次，可能會浪費許多時間。 它會進入您在所在行中使用的所有程式碼，包括標準程式庫函式。

1. 現在當執行點位於 `Calculate` 函式的開頭時，請按 **F10** 來移動到程式執行的下一行。 **F10** 又稱為 [不進入函式]  。 您可以使用 [不進入函式]  來從一行移動到下一行，而無須了解該行每個部分所發生的事件。 一般情況下，建議您使用 [不進入函式]  而非 [逐步執行]  ，除非您想要更深入地了解從其他位置呼叫的程式碼 (如同您為了觸達 `Calculate` 主體所進行的操作)。

1. 繼續使用 **F10** 以**不進入**每一行函式，直到您回到另一個檔案的 `main()`，並在 `cout` 行上停止。

   ![跳出 Calculate 並檢查結果](./media/calculator-undefined-zero.gif "跳出 Calculate 並檢查結果")

   看起來程式正如預期般運作：它會接收第一個數字，然後除以第二個數字。 在 `cout` 行上，在 `result` 變數上暫留或在 [自動變數]  視窗中查看 `result`。 您將會看到其值列出為 "inf"，這看起來不正確，因此讓我們修正它吧。 `cout` 行只會輸出任何儲存在 `result` 中的值，因此當您使用 **F10** 前往下一行時，會顯示主控台視窗：

   ![除以零的結果](./media/calculator-divide-by-zero-fail.png "除以零的結果")

   此結果是因為除以零的結果未定義，因此程式針對所要求運算沒有數值答案。

### <a name="to-fix-the-divide-by-zero-error"></a>修正「除以零」錯誤

讓我們以更好的方式來處理「除以零」，讓使用者能了解問題。

1. 請在 *CalculatorTutorial.cpp* 中進行下列變更。 (歸功於稱為 [編輯後繼續]  的功能，您可以在編輯的時候讓程式繼續執行)：

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. 現在，請按 **F5**一次。 程式會繼續執行，直到需要暫停要求使用者輸入為止。 再次輸入 `10 / 0`。 現在會印出更有幫助的訊息。 程式會向使用者要求更多輸入，且程式會繼續正常執行。

   ![變更後的最終結果](./media/calculator-final-verification.gif "變更後的最終結果")

   > [!Note]
   > 當您在處於偵錯模式的期間編輯程式碼時，可能會有程式碼過時的風險。 這會在偵錯工具仍在執行您的舊版程式碼，且尚未使用您的變更進行更新時發生。 偵錯工具會在發生此情況時彈出一個對話方塊提醒您。 有時候，您可能需要按 **F5** 來重新整理正在執行的程式碼。 特別是當執行點正位於函式中，而您在該函式的內部進行變更時，您將需要跳出函式，然後再次進入該函式來取得更新後的程式碼。 若因為某些原因仍無法正常運作，且您看到了錯誤訊息，您可以按一下 IDE 頂端功能表下方工具列中的紅色方塊來停止偵錯，然後按 **F5** 來再次啟動偵錯，或選擇工具列上停止按鈕旁邊的綠色 [執行] 箭頭來進行。
   
   > 了解執行和偵錯快速鍵
   >
   > - **F5** (或 [偵錯]   > [開始偵錯]  ) 會啟動偵錯工作階段 (若沒有正在使用中的工作階段) 並執行程式，直到到達中斷點或程式需要使用者進行輸入。 若不需要使用者輸入且沒有可到達的中斷點，程式會在完成執行時終止並關閉主控台視窗本身。 若您有類似 "Hello World" 的程式要執行，請使用 **Ctrl+F5** 或設定中斷點，然後按 **F5** 來將視窗維持在開啟狀態。
   > - **Ctrl+F5** (或 [偵錯]   > [啟動但不偵錯]  ) 會執行應用程式，而不會進入偵錯模式。 這比偵錯稍快，且主控台視窗會在程式完成執行時維持在開啟狀態。
   > - **F10** (又稱為 [不進入函式]  ) 可讓您逐一且逐行查看程式碼，並視覺化程式碼執行方式及每個執行步驟中的變數值為何。
   > - **F11** (又稱為 [逐步執行]  ) 的運作方式與 [不進入函式]  相似，但它會進入任何在執行行上呼叫的函式。 例如，當執行的行呼叫一個函式時，按 **F11** 會將指標移動到函式主體，讓您可以跟隨所執行的函式程式碼，然後回到您開始的那一行。 按 **F10** 可不進入函式，直接移動到下一行；函式仍會獲得呼叫，但程式不會暫停並顯示其正在進行的操作。

### <a name="close-the-app"></a>關閉應用程式

- 若仍在執行中，請關閉計算機應用程式的主控台視窗。

## <a name="the-finished-app"></a>完成的應用程式

恭喜您！ 您已完成計算機應用程式的程式碼，並在 Visual Studio 中建置及偵錯。

## <a name="next-steps"></a>後續步驟

[深入了解適用於 C++ 的 Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end