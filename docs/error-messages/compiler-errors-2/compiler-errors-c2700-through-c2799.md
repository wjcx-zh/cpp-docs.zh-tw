---
title: 編譯器錯誤 C2700 至 C2799
ms.date: 04/21/2019
f1_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
helpviewer_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
ms.openlocfilehash: 174f6a9c8ec9e44deadfca090ba492cb32d53e9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197510"
---
# <a name="compiler-errors-c2700-through-c2799"></a>編譯器錯誤 C2700 至 C2799

本檔的這一節中的文章說明編譯器所產生的錯誤訊息子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>錯誤訊息

|錯誤|訊息|
|-----------|-------------|
|[編譯器錯誤 C2700](compiler-error-c2700.md)|'*type*'：無法擲回（請使用/W4 以取得詳細資訊）|
|[編譯器錯誤 C2701](compiler-error-c2701.md)|'*function*'：函式樣板/泛型不可以是區域類別的 friend|
|[編譯器錯誤 C2702](compiler-error-c2702.md)| __except 可能不會出現在終止區塊中|
|[編譯器錯誤 C2703](compiler-error-c2703.md)|不合法的 __leave 語句|
|[編譯器錯誤 C2704](compiler-error-c2704.md)|'*function*'：僅在 varargs 中允許 __va_start 內建|
|[編譯器錯誤 C2705](compiler-error-c2705.md)|'*label*'：不合法的跳入 '*exception_block*' 範圍|
|[編譯器錯誤 C2706](compiler-error-c2706.md)|沒有相符的 __try （在 __try 區塊中遺漏 '} '）的不合法 __except|
|[編譯器錯誤 C2707](compiler-error-c2707.md)|'*identifier*'：內建函式的錯誤內容|
|[編譯器錯誤 C2708](compiler-error-c2708.md)|'*identifier*'：實際參數長度（以位元組為單位）與先前的呼叫或參考不同|
|[編譯器錯誤 C2709](compiler-error-c2709.md)|'*identifier*'：型式參數長度（以位元組為單位）與先前的宣告不同|
|[編譯器錯誤 C2710](compiler-error-c2710.md)|'*identifier*'： ' __declspec （*修飾*詞） ' 只能套用至傳回指標的函式|
|[編譯器錯誤 C2711](compiler-error-c2711.md)|'*function*'：此函式無法編譯為受控，請考慮使用 #pragma 非受控|
|[編譯器錯誤 C2712](compiler-error-c2712.md)|不能在需要物件回溯的函式中使用 __try|
|[編譯器錯誤 C2713](compiler-error-c2713.md)|每個函式只允許一種例外狀況處理形式|
|[編譯器錯誤 C2714](compiler-error-c2714.md)| `alignof(void)`不允許|
|[編譯器錯誤 C2715](compiler-error-c2715.md)|'*type*'：無法擲回或攔截此類型|
|編譯器錯誤 C2716|已過時。|
|編譯器錯誤 C2717|已過時。|
|[編譯器錯誤 C2718](compiler-error-c2718.md)|'*type*'：要求的*數位*對齊的實際參數不會對齊|
|[編譯器錯誤 C2719](compiler-error-c2719.md)|'*parameter*'：要求的*數位*對齊的型式參數不會對齊|
|[編譯器錯誤 C2720](compiler-error-c2720.md)|'*identifier*'： '*規範*' 儲存類別規範在成員上不合法|
|[編譯器錯誤 C2721](compiler-error-c2721.md)|'*規範*'：運算子關鍵字和類型之間的儲存類別規範不合法|
|[編譯器錯誤 C2722](compiler-error-c2722.md)|'：：*operator*'：下列運算子命令不合法;使用 ' operator *operator*'|
|[編譯器錯誤 C2723](compiler-error-c2723.md)|'*function*'： '*規範*' 規範在函式定義中不合法|
|[編譯器錯誤 C2724](compiler-error-c2724.md)|'*function*'： ' static ' 不應在檔案範圍定義的成員函式上使用|
|[編譯器錯誤 C2725](compiler-error-c2725.md)|'*type*'：無法以值或參考來擲回或攔截 Managed/WinRT 物件|
|[編譯器錯誤 C2726](compiler-error-c2726.md)|' gcnew ' 只能用來建立具有 managed/WinRT 類型的物件|
|編譯器錯誤 C2727|已過時。|
|[編譯器錯誤 C2728](compiler-error-c2728.md)|'*type*'：原生陣列不能包含此類型|
|編譯器錯誤 C2729|已過時。|
|[編譯器錯誤 C2730](compiler-error-c2730.md)|'*class*'：不能是本身的基類|
|[編譯器錯誤 C2731](compiler-error-c2731.md)|'*function*'：無法多載函式|
|[編譯器錯誤 C2732](compiler-error-c2732.md)|連結規格與先前「*函數*」的規格衝突|
|[編譯器錯誤 C2733](compiler-error-c2733.md)|'*function*'：不允許多載函式的第二個 C 連結|
|[編譯器錯誤 C2734](compiler-error-c2734.md)|'*identifier*'： ' const ' 物件若不是 ' extern '，則必須初始化|
|[編譯器錯誤 C2735](compiler-error-c2735.md)|型式參數類型規範中不允許 '*關鍵字*' 關鍵字|
|[編譯器錯誤 C2736](compiler-error-c2736.md)|cast 中不允許 '*關鍵字*' 關鍵字|
|編譯器錯誤 C2737|'*identifier*'： ' constexpr ' 物件必須初始化|
|[編譯器錯誤 C2738](compiler-error-c2738.md)|' operator *type*'：不明確，或不是 '*class*' 的成員|
|[編譯器錯誤 C2739](compiler-error-c2739.md)|'*number*'：明確的 Managed/WinRT 陣列維度必須介於1到32之間|
|編譯器錯誤 C2740|運算元 '*number*' 的值超出範圍 '*lower_bound*  -  *upper_bound*'|
|編譯器錯誤 C2741|框架大小太大|
|編譯器錯誤 C2742|已過時。|
|[編譯器錯誤 C2743](compiler-error-c2743.md)|'*type*'：無法使用 __clrcall 的析構函式或複製模式來攔截原生類型|
|編譯器錯誤 C2744|'*operator*' 不是有效的 CLR/WinRT 運算子|
|[編譯器錯誤 C2745](compiler-error-c2745.md)|'*token*'：此權杖無法轉換成識別碼|
|編譯器錯誤 C2746|已過時。|
|編譯器錯誤 C2747|已過時。|
|[編譯器錯誤 C2748](compiler-error-c2748.md)|managed/WinRT 陣列建立必須有陣列大小或陣列初始化運算式|
|[編譯器錯誤 C2749](compiler-error-c2749.md)|'*type*'：只能使用/clr： safe 來擲回或攔截 managed 類別的控制碼|
|[編譯器錯誤C2750](compiler-error-c2750.md)|'*type*'：不能在參考型別上使用 ' new ';請改用 ' gcnew '|
|[編譯器錯誤 C2751](compiler-error-c2751.md)|'*parameter*'：無法限定函數參數的名稱|
|[編譯器錯誤 C2752](compiler-error-c2752.md)|'*template*'：有一個以上的部分特製化符合範本引數清單|
|[編譯器錯誤 C2753](compiler-error-c2753.md)|'*template*'：部分特製化不能符合主要範本的引數清單|
|[編譯器錯誤 C2754](compiler-error-c2754.md)|'*template*'：部分特製化不能有相依的非類型範本參數|
|[編譯器錯誤 C2755](compiler-error-c2755.md)|'*parameter*'：部分特製化的非類型參數必須是簡單的識別碼|
|[編譯器錯誤 C2756](compiler-error-c2756.md)|'*template*'：部分特製化上不允許預設範本引數|
|[編譯器錯誤 C2757](compiler-error-c2757.md)|'*identifier*'：使用此名稱的符號已經存在，因此無法使用此名稱做為命名空間名稱|
|[編譯器錯誤 C2758](compiler-error-c2758.md)|'*member*'：必須初始化參考型別的成員|
|編譯器錯誤 C2759|內嵌組譯工具報表： *error_message*|
|[編譯器錯誤 C2760](compiler-error-c2760.md)|語法錯誤：必須是 '*token1*' 而不是 '*token2*'|
|[編譯器錯誤 C2761](compiler-error-c2761.md)|'*function*'：不允許成員函式重新宣告|
|[編譯器錯誤 C2762](compiler-error-c2762.md)|'*template*'：不正確運算式做為 '*parameter*' 的樣板引數|
|編譯器錯誤 C2763|'*template*'：使用字串常值做為 '*parameter*' 的樣板引數無效|
|[編譯器錯誤 C2764](compiler-error-c2764.md)|'*parameter*'：未在部分特製化「特製*化*」中使用或 deducible 範本參數|
|[編譯器錯誤 C2765](compiler-error-c2765.md)|'*function*'：函式樣板的明確特製化不能有任何預設引數|
|[編譯器錯誤 C2766](compiler-error-c2766.md)|明確特製化;' 特製*化*' 已經定義過了|
|[編譯器錯誤 C2767](compiler-error-c2767.md)|managed/WinRT 陣列維度不相符：預期的*數位*引數-提供的*數位*|
|[編譯器錯誤 C2768](compiler-error-c2768.md)|'*function*'：明確樣板引數的使用不合法|
|編譯器錯誤 C2769|您不能將基底/成員初始化運算式清單中的 managed/WinRT 陣列以括弧括住|
|[編譯器錯誤 C2770](compiler-error-c2770.md)|'*template*' 的明確範本/泛型引數無效|
|[編譯器錯誤 C2771](compiler-error-c2771.md)|#import 只允許在全域或命名空間範圍中|
|編譯器錯誤 C2772|已過時。|
|[編譯器錯誤 C2773](compiler-error-c2773.md)|#import 和 #using 僅適用于 c + + 編譯器|
|[編譯器錯誤 C2774](compiler-error-c2774.md)|'*identifier*'：沒有與這個屬性相關聯的 ' put ' 方法|
|[編譯器錯誤 C2775](compiler-error-c2775.md)|'*identifier*'：沒有與這個屬性相關聯的 ' get ' 方法|
|[編譯器錯誤 C2776](compiler-error-c2776.md)|每個屬性只能指定一個 ' get ' 方法|
|[編譯器錯誤 C2777](compiler-error-c2777.md)|每個屬性只能指定一個 ' put ' 方法|
|[編譯器錯誤 C2778](compiler-error-c2778.md)|__declspec （uuid （））中格式不正確的 GUID|
|[編譯器錯誤 C2779](compiler-error-c2779.md)|'*宣告 '：* 屬性方法只能與非靜態資料成員相關聯|
|[編譯器錯誤 C2780](compiler-error-c2780.md)|'*宣告*'：預期的*數位*引數-提供的*數位*|
|[編譯器錯誤 C2781](compiler-error-c2781.md)|'*宣告 '：* 應至少提供*數位*引數-*數位*|
|[編譯器錯誤 C2782](compiler-error-c2782.md)|'*宣告 '：* 範本/泛型參數 '*parameter*' 不明確|
|[編譯器錯誤 C2783](compiler-error-c2783.md)|'*宣告 '：* 無法推算 '*identifier*' 的範本/泛型引數|
|[編譯器錯誤 C2784](compiler-error-c2784.md)|'*宣告 '：* 無法從 '*type2*' 推算 '*type1*' 的範本/泛型引數|
|[編譯器錯誤 C2785](compiler-error-c2785.md)|'*宣告 1>*' 和 '*宣告 2>*' 有不同的傳回類型|
|[編譯器錯誤 C2786](compiler-error-c2786.md)|'*type*'： __uuidof 的運算元無效|
|[編譯器錯誤 C2787](compiler-error-c2787.md)|'*identifier*'：沒有與此物件相關聯的 GUID|
|[編譯器錯誤 C2788](compiler-error-c2788.md)|'*identifier*'：一個以上與此物件相關聯的 GUID|
|編譯器錯誤 C2789|'*identifier*'：必須初始化 const 限定類型的物件|
|[編譯器錯誤 C2790](compiler-error-c2790.md)|' super '：這個關鍵字只能用在類別成員函式的主體內|
|[編譯器錯誤 C2791](compiler-error-c2791.md)|' super ' 的使用不合法： '*class*' 沒有任何基類|
|[編譯器錯誤 C2792](compiler-error-c2792.md)|' super '：此關鍵字後面必須加上 '：： '|
|[編譯器錯誤 C2793](compiler-error-c2793.md)|'*token*'：必須是 '：： ' 後面的非預期的標記，必須是識別碼或關鍵字 ' operator '|
|[編譯器錯誤 C2794](compiler-error-c2794.md)|'*identifier*'：不是 '*class*' 任何直接或間接基類的成員|
|[編譯器錯誤 C2795](compiler-error-c2795.md)|' super：：*identifier*' 不是成員函式|
|編譯器錯誤 C2796|' ref new ' 只可用來建立 WinRT 類型的實例|
|[編譯器錯誤 C2797](compiler-error-c2797.md)|過時'*identifier*'：在成員初始化運算式清單或非靜態資料成員初始化運算式內的清單初始化未執行|
|[編譯器錯誤 C2798](compiler-error-c2798.md)|' super：：*identifier*' 是不明確的|
|編譯器錯誤 C2799|'*identifier*'：在沒有使用者提供的預設函式的情況下，必須初始化 const 限定類別類型的物件|

## <a name="see-also"></a>另請參閱

[C/c + + 編譯器和組建工具錯誤和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[編譯器錯誤 C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
