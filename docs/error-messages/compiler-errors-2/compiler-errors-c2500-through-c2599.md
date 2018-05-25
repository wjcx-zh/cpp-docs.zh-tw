---
title: 編譯器錯誤 C2500 至 C2599 |Microsoft 文件
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
helpviewer_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
dev_langs:
- C++
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 994f29009294e6b49851a817a5872fcaa122b153
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-errors-c2500-through-c2599"></a>編譯器錯誤 C2500 至 C2599

文件的本節文章說明編譯器所產生的錯誤訊息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>錯誤訊息

|錯誤|訊息|
|-----------|-------------|
|[編譯器錯誤 C2500](compiler-error-C2500.md)|'*identifier1*':'*identifier2*' 已經是直接基底類別|
|編譯器錯誤 C2501|'*識別碼*':' __declspec (*規範*)' 只可以套用至結構、 等位、 類別或不帶正負號的位元欄位成員|
|[編譯器錯誤 C2502](compiler-error-C2502.md)|'*識別碼*': 基底類別上的太多存取修飾詞|
|[編譯器錯誤 C2503](compiler-error-C2503.md)|'*類別*': 基底類別不能包含大小為零的陣列|
|[編譯器錯誤 C2504](compiler-error-C2504.md)|'*類別*': 基底類別未定義|
|[編譯器錯誤 C2505](compiler-error-C2505.md)|'*符號*':' __declspec (*規範*)' 只能套用至宣告或定義的全域物件或靜態資料成員|
|[編譯器錯誤 C2506](compiler-error-C2506.md)|'*成員*':' __declspec (*規範*)' 無法套用至這個符號|
|[編譯器錯誤 C2507](compiler-error-C2507.md)|'*識別碼*': 基底類別上的太多虛擬修飾詞|
|編譯器錯誤 C2508|'*識別碼*':' __declspec (*specifier1*)' 無法結合 ' __declspec (*specifier2*)'|
|[編譯器錯誤 C2509](compiler-error-C2509.md)|'*識別碼*': 未宣告成員函式'*類別*'|
|[編譯器錯誤 C2510](compiler-error-C2510.md)|'*識別碼*': 左的 '::' 必須是類別/結構/等位|
|[編譯器錯誤 C2511](compiler-error-C2511.md)|'*識別碼*': 多載成員函式中找不到'*類別*'|
|[編譯器錯誤 C2512](compiler-error-C2512.md)|'*識別碼*': 沒有適當的預設建構函式使用|
|[編譯器錯誤 C2513](compiler-error-C2513.md)|' * 型別 ': '=' 之前沒有宣告變數|
|[編譯器錯誤 C2514](compiler-error-C2514.md)|'*類別*': 類別有任何建構函式|
|編譯器錯誤 C2515|'*識別碼*': 'vtguard' 只能套用至類別宣告或定義|
|[編譯器錯誤 C2516](compiler-error-C2516.md)|'*類別*': 不合法的基底類別|
|[編譯器錯誤 C2517](compiler-error-C2517.md)|'*識別碼*': 右邊 '::' 未定義|
|[編譯器錯誤 C2518](compiler-error-C2518.md)|關鍵字 '*關鍵字*' 在基底類別清單中不合法; 已忽略|
|編譯器錯誤 C2519|'*識別碼*': WinRT 屬性只能包含公用欄位|
|編譯器錯誤 C2520|'*類別*': 適用於隱含轉換沒有非明確建構函式|
|[編譯器錯誤 C2521](compiler-error-C2521.md)|解構函式/完成項不接受任何引數|
|編譯器錯誤 C2522|'*識別碼*': 多載識別項不能在'*identifier1*'as 上已指定'*identifier2*'|
|[編譯器錯誤 C2523](compiler-error-C2523.md)|'*類別*:: ~*識別碼*': 解構函式/完成項標記不相符|
|[編譯器錯誤 C2524](compiler-error-C2524.md)|'*識別碼*': 解構函式/完成項必須有 'void' 參數清單|
|編譯器錯誤 C2525|'*識別碼*': 參數'*identifier1*'名為'*identifier2*' 在基底函式，並已發行實作中必須相符|
|[編譯器錯誤 C2526](compiler-error-C2526.md)|'*identifier1*': C 連結函式無法傳回 c + + 類別*identifier2*'|
|編譯器錯誤 C2527|'*識別碼*': 無法同時指定 DefaultOverload'*function1*'和'*function2*'。 移除一個規格，或在實作期間重新命名函式|
|[編譯器錯誤 C2528](compiler-error-C2528.md)|'*識別碼*': 參考的指標不合法|
|[編譯器錯誤 C2529](compiler-error-C2529.md)|'*識別碼*': 參考的參考不合法|
|[編譯器錯誤 C2530](compiler-error-C2530.md)|'*識別碼*': 必須初始化參考|
|[編譯器錯誤 C2531](compiler-error-C2531.md)|'*識別碼*': 位元欄位不合法的參考|
|[編譯器錯誤 C2532](compiler-error-C2532.md)|'*識別碼*': 參考的修飾詞不合法|
|[編譯器錯誤 C2533](compiler-error-C2533.md)|'*識別碼*': 不允許傳回類型的建構函式|
|[編譯器錯誤 C2534](compiler-error-C2534.md)|'*識別碼*': 建構函式無法傳回值|
|[編譯器錯誤 C2535](compiler-error-C2535.md)|'*識別碼*': 已經定義或宣告的成員函式|
|編譯器錯誤 C2536|已過時。|
|[編譯器錯誤 C2537](compiler-error-C2537.md)|'*規範*': 不合法的連結規格|
|編譯器錯誤 C2538|已過時。|
|編譯器錯誤 C2539|已過時。|
|[編譯器錯誤 C2540](compiler-error-C2540.md)|非常數運算式當做陣列界限|
|[編譯器錯誤 C2541](compiler-error-C2541.md)|'*識別碼*': 無法刪除不是指標的物件|
|[編譯器錯誤 C2542](compiler-error-C2542.md)|'*識別碼*': 類別物件已初始化沒有建構函式|
|[編譯器錯誤 C2543](compiler-error-C2543.md)|必須是 ']' 的運算子 '[]'|
|[編譯器錯誤 C2544](compiler-error-C2544.md)|必須是 ')' 的運算子 '（）'|
|[編譯器錯誤 C2545](compiler-error-C2545.md)|'*運算子*': 找不到多載運算子|
|編譯器錯誤 C2546|'*識別碼*': 當 PIA 和非 PIA 必須先參考 PIA 中定義的類型|
|編譯器錯誤 C2547|'*識別碼*': 已發行方法的所有參數必須明確都命名的宣告上|
|[編譯器錯誤 C2548](compiler-error-C2548.md)|'*函式*': 遺漏參數的預設參數*參數*|
|[編譯器錯誤 C2549](compiler-error-C2549.md)|使用者定義的轉換不能指定傳回型別|
|[編譯器錯誤 C2550](compiler-error-C2550.md)|'*識別碼*': 建構函式初始設定式清單只允許在建構函式定義|
|[編譯器錯誤 C2551](compiler-error-C2551.md)|'void *' 類型需要明確轉換|
|[編譯器錯誤 C2552](compiler-error-C2552.md)|'*識別碼*': 無法以初始設定式清單初始化非彙總|
|[編譯器錯誤 C2553](compiler-error-C2553.md)|'*類型* *derived_class*::*函式*': 覆寫虛擬函式傳回型別不同於'*類型* *base_類別*::*函式*'|
|[編譯器錯誤 C2555](compiler-error-C2555.md)|'*derived_class*::*函式*': 覆寫虛擬函式傳回類型不同，而且不是從 covariant'*base_class*::*函式*'|
|[編譯器錯誤 C2556](compiler-error-C2556.md)|'*type1* *類別*::*函式*': 多載函式只有不同傳回類型從'*type2* *類別*::*函式*'|
|[編譯器錯誤 C2557](compiler-error-C2557.md)|'*識別碼*': 沒有建構函式無法初始化 private 和 protected 成員|
|[編譯器錯誤 C2558](compiler-error-C2558.md)|類別*類別*': 沒有可用的複製建構或複製建構函式宣告為 'explicit'|
|編譯器錯誤 C2559|'*識別碼*': 無法多載成員函式不含 ref 限定詞 ref-qualifier 的成員函式|
|編譯器錯誤 C2560|'*識別碼*': 無法多載成員函式具有 ref 限定詞 ref-qualifier 的成員函式|
|[編譯器錯誤 C2561](compiler-error-C2561.md)|'*函式*': 函式必須傳回值|
|[編譯器錯誤 C2562](compiler-error-C2562.md)|'*函式*': 'void' 傳回值的函式|
|[編譯器錯誤 C2563](compiler-error-C2563.md)|型式參數清單中的不符|
|編譯器錯誤 C2564|已過時。|
|編譯器錯誤 C2565|'*識別碼*': ref 限定詞不合法的建構函式/解構函式|
|[編譯器錯誤 C2566](compiler-error-C2566.md)|條件運算式中的多載函式|
|[編譯器錯誤 C2567](compiler-error-C2567.md)|無法開啟中繼資料中的 '*filename*'， *possible_reason*|
|[編譯器錯誤 C2568](compiler-error-C2568.md)|'*識別碼*': 無法解析函式多載|
|[編譯器錯誤 C2569](compiler-error-C2569.md)|'*識別碼*': 列舉/等位不能當做基底類別|
|[編譯器錯誤 C2570](compiler-error-C2570.md)|'*識別碼*': 等位不能有基底類別|
|[編譯器錯誤 C2571](compiler-error-C2571.md)|'*識別碼*': 虛擬函式不能在等位中'*union*'|
|[編譯器錯誤 C2572](compiler-error-C2572.md)|'*函式*': 重複定義的預設引數： 參數*數目*|
|[編譯器錯誤 C2573](compiler-error-C2573.md)|'*類別*': 無法刪除指向此類型物件的指標類別具有 'operator delete' 沒有任何未定位多載。 使用:: 刪除或加入類別中的 '運算子(void\*) delete'|
|[編譯器錯誤 C2574](compiler-error-C2574.md)|'*解構函式*': 無法宣告為 static|
|[編譯器錯誤 C2575](compiler-error-C2575.md)|'*識別碼*': 只有成員函式和基底可以是虛擬|
|編譯器錯誤 C2576|'*識別碼*': 不能引入新的虛擬方法，以 'public'。 請考慮將方法非虛擬的或變更的範圍為 'internal' protected private'|
|[編譯器錯誤 C2577](compiler-error-C2577.md)|'*識別碼*': 解構函式/完成項不能有傳回型別|
|編譯器錯誤 C2578|'*類別*': 類型不能有 'protected' protected public' 建構函式|
|[編譯器錯誤 C2579](compiler-error-C2579.md)|無法解析類型*類型*(*位移*)。 它必須在*檔名*|
|編譯器錯誤 C2580|'*識別碼*': 不允許多個版本的預設特殊成員函式|
|[編譯器錯誤 C2581](compiler-error-C2581.md)|'*類型*': 靜態' 運算子 =' 函式不合法|
|[編譯器錯誤 C2582](compiler-error-C2582.md)|' 運算子*運算子*'函式已無法在'*類型*'|
|[編譯器錯誤 C2583](compiler-error-C2583.md)|'*識別碼*':' const/volatile ' 'this' 指標不合法的建構函式/解構函式|
|[編譯器錯誤 C2584](compiler-error-C2584.md)|'*類別*': 直接基底'*base_class2*'無法存取; 的基底'*base_class1*'|
|[編譯器錯誤 C2585](compiler-error-C2585.md)|明確轉換成 '*類型*' 模稜兩可|
|[編譯器錯誤 C2586](compiler-error-C2586.md)|不正確的使用者定義轉換語法： 間接取值不合法|
|[編譯器錯誤 C2587](compiler-error-C2587.md)|'*識別碼*': 不合法使用的區域變數當做預設參數|
|[編譯器錯誤 C2588](compiler-error-C2588.md)|':: ~*識別碼*': 不合法的全域解構函式/完成|
|[編譯器錯誤 C2589](compiler-error-C2589.md)|'*識別碼*': 不合法的語彙基元，在右邊 ':: '|
|編譯器錯誤 C2590|'*識別碼*': 只有建構函式可以有基底/成員初始設定式清單|
|編譯器錯誤 C2591|Exclusiveto 不能使用 '*類型*' 做為引數。 只有 'ref class' 是有效的引數|
|[編譯器錯誤 C2592](compiler-error-C2592.md)|'*類別*':'*base_class2*'繼承自'*base_class1*' 而且無法重新指定|
|[編譯器錯誤 C2593](compiler-error-C2593.md)|'運算子*識別碼*' 模稜兩可|
|[編譯器錯誤 C2594](compiler-error-C2594.md)|'*運算子*': 模稜兩可的轉換，從'*type1*'to'*type2*'|
|編譯器錯誤 C2595|'*識別碼*' WinRT 屬性類型必須密封|
|編譯器錯誤 C2596|'*識別碼*' WinRT 屬性欄位只能是 'public enum class'、 'int'、 'unsigned 的 int'、 'bool'、 'Platform:: type'、 'Platform:: string' 或 ' Windows:: Foundation:: HResult'|
|[編譯器錯誤 C2597](compiler-error-C2597.md)|參考非靜態成員不合法 '*識別碼*'|
|[編譯器錯誤 C2598](compiler-error-C2598.md)|連結規格必須在全域範圍|
|[編譯器錯誤 C2599](compiler-error-C2599.md)|'*識別碼*': 不允許的 managed/WinRT 列舉的向前宣告|  