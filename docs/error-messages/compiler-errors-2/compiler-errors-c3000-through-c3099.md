---
title: "編譯器錯誤 C3000 透過 C3099 |Microsoft 文件"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
dev_langs:
- C++
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aae3a2b5ceaf84fbb1e4a964eac82ec86ce033fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c3000-through-c3099"></a>編譯器錯誤 C3000 透過 C3099

文件的本節文章說明編譯器所產生的錯誤訊息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>錯誤訊息

|錯誤|訊息|
|-----------|-------------|
|編譯器錯誤 C3000|已過時。|
|[編譯器錯誤 C3001](compiler-error-c3001.md)|'*訊息*': 需要 OpenMP 指示詞名稱|
|[編譯器錯誤 C3002](compiler-error-c3002.md)|'*name1* *name2*': 多重 OpenMP 指示詞名稱|
|[編譯器錯誤 C3003](compiler-error-c3003.md)|'*指示詞*': 不允許指示詞子句之後的 OpenMP 指示詞名稱|
|[編譯器錯誤 C3004](compiler-error-c3004.md)|'*子句*': 子句在 OpenMP 無效'*指示詞*' 指示詞|
|[編譯器錯誤 C3005](compiler-error-c3005.md)|'*訊息*': 非預期的語彙基元在 OpenMP'*指示詞*' 指示詞|
|[編譯器錯誤 C3006](compiler-error-c3006.md)|'*子句*': 子句在 OpenMP'*指示詞*' 指示詞缺少必要的引數|
|[編譯器錯誤 C3007](compiler-error-c3007.md)|'*子句*': 子句在 OpenMP'*指示詞*' 指示詞不接受引數|
|[編譯器錯誤 C3008](compiler-error-c3008.md)|*引數*': 引數遺漏右 ')' 在 OpenMP '*指示詞*' 指示詞|
|[編譯器錯誤 C3009](compiler-error-c3009.md)|'*標籤*': 跳入 OpenMP 結構化區塊不允許|
|[編譯器錯誤 C3010](compiler-error-c3010.md)|'*標籤*': 跳出 OpenMP 結構化區塊不允許|
|[編譯器錯誤 C3011](compiler-error-c3011.md)|內嵌組譯碼不允許直接放在平行區域內|
|[編譯器錯誤 C3012](compiler-error-c3012.md)|'*函式*': 不允許直接放在平行區域內的內建函式|
|[編譯器錯誤 C3013](compiler-error-c3013.md)|'*子句*': 子句只能一次出現在 OpenMP'*指示詞*' 指示詞|
|[編譯器錯誤 C3014](compiler-error-c3014.md)|預期 for 迴圈遵循 OpenMP '*指示詞*' 指示詞|
|[編譯器錯誤 C3015](compiler-error-c3015.md)|OpenMP 'for' 陳述式中的初始設定格式不當|
|[編譯器錯誤 C3016](compiler-error-c3016.md)|'*識別碼*': 在 OpenMP 'for' 陳述式的索引變數必須具有帶正負號整數類資料類型|
|[編譯器錯誤 C3017](compiler-error-c3017.md)|OpenMP 'for' 陳述式中的終止測試格式不當|
|[編譯器錯誤 C3018](compiler-error-c3018.md)|'*識別碼*': OpenMP 'for' 測試或增量必須使用索引變數'*變數*'|
|[編譯器錯誤 C3019](compiler-error-c3019.md)|在 OpenMP 'for' 陳述式的遞增值具有格式不正確|
|[編譯器錯誤 C3020](compiler-error-c3020.md)|'*變數*': OpenMP 'for' 迴圈索引變數不可修改迴圈主體中|
|[編譯器錯誤 C3021](compiler-error-c3021.md)|'*引數*': 引數是空的 OpenMP'*指示詞*' 指示詞|
|[編譯器錯誤 C3022](compiler-error-c3022.md)|'*指示詞*': 無效的排程類型的'*指示詞*'在 OpenMP'*指示詞*' 指示詞|
|[編譯器錯誤 C3023](compiler-error-c3023.md)|'*引數*': OpenMP 引數中發生未預期的 token'*指示詞*' 子句|
|[編譯器錯誤 C3024](compiler-error-c3024.md)|'schedule （runtime)': 不允許 chunk_size 運算式|
|[編譯器錯誤 C3025](compiler-error-c3025.md)|'*子句*': 需要整數運算式|
|[編譯器錯誤 C3026](compiler-error-c3026.md)|'*子句*': 常數運算式必須是正數|
|[編譯器錯誤 C3027](compiler-error-c3027.md)|'*子句*': 需要算術或指標運算式|
|[編譯器錯誤 C3028](compiler-error-c3028.md)|'*成員*': 變數或靜態資料成員可以使用的資料共用子句中|
|[編譯器錯誤 C3029](compiler-error-c3029.md)|'*符號*': 只能出現一次在資料共用子句在 OpenMP 指示詞|
|[編譯器錯誤 C3030](compiler-error-c3030.md)|'*識別碼*': 變數'*指示詞*' 子句/指示詞不能有參考類型|
|[編譯器錯誤 C3031](compiler-error-c3031.md)|'*識別碼*': 'reduction' 子句中的變數必須有純量算術類型|
|[編譯器錯誤 C3032](compiler-error-c3032.md)|'*識別碼*': 變數'*子句*'子句不能有不完整類型'*類型*'|
|[編譯器錯誤 C3033](compiler-error-c3033.md)|'*識別碼*': 變數'*子句*' 子句不能有 const 限定的類型|
|[編譯器錯誤 C3034](compiler-error-c3034.md)|OpenMP '*指示詞*'指示詞不能直接巢狀內'*指示詞*' 指示詞|
|[編譯器錯誤 C3035](compiler-error-c3035.md)|OpenMP 'ordered' 指示詞必須與 'ordered' 子句一起直接繫結到 'for' 或 'parallel for' 指示詞|
|[編譯器錯誤 C3036](compiler-error-c3036.md)|'*子句*': OpenMP 'reduction' 子句中無效的運算子語彙基元|
|[編譯器錯誤 C3037](compiler-error-c3037.md)|'*識別碼*': 變數'*子句*' 子句必須共用封入內容中|
|[編譯器錯誤 C3038](compiler-error-c3038.md)|'*識別碼*': 'private' 子句中的變數不可為削減變數在封入內容|
|[編譯器錯誤 C3039](compiler-error-c3039.md)|'*識別碼*': OpenMP 'for' 陳述式的索引變數不可為削減變數|
|[編譯器錯誤 C3040](compiler-error-c3040.md)|'*識別碼*': 'reduction' 子句中的變數類型與削減運算子不相容'*運算子*'|
|[編譯器錯誤 C3041](compiler-error-c3041.md)|'*識別碼*': 'copyprivate' 子句中的變數必須是私用，封入內容中|
|[編譯器錯誤 C3042](compiler-error-c3042.md)|'copyprivate' 和 'nowait' 子句不能同時出現在 OpenMP '*指示詞*' 指示詞|
|[編譯器錯誤 C3043](compiler-error-c3043.md)|OpenMP 'critical' 指示詞不能以巢狀方式置於相同名稱的 'critical' 指示詞中|
|[編譯器錯誤 C3044](compiler-error-c3044.md)|'section': 只允許直接以巢狀在 OpenMP 'sections' 指示詞之下|
|[編譯器錯誤 C3045](compiler-error-c3045.md)|OpenMP 'sections' 指示詞後面必須是複合陳述式。 遺漏 '{'|
|[編譯器錯誤 C3046](compiler-error-c3046.md)|OpenMP '#pragma omp sections' 區域中遺漏結構化區塊|
|[編譯器錯誤 C3047](compiler-error-c3047.md)|OpenMP 'sections' 區域中的結構化區塊，前面必須是 '#pragma omp section'|
|[編譯器錯誤 C3048](compiler-error-c3048.md)|'#pragma omp atomic' 後面的運算式格式指定錯誤|
|[編譯器錯誤 C3049](compiler-error-c3049.md)|'*引數*': OpenMP 'default' 子句中無效的引數|
|[編譯器錯誤 C3050](compiler-error-c3050.md)|'*類別*': ref 類別不可繼承自'*識別碼*'|
|編譯器錯誤 C3051|已過時。|
|[編譯器錯誤 C3052](compiler-error-c3052.md)|'*識別碼*': 變數未出現在 default （none） 子句下的資料共用子句中|
|[編譯器錯誤 C3053](compiler-error-c3053.md)|'*識別碼*': 'threadprivate' 只是對全域或靜態資料項目有效|
|[編譯器錯誤 C3054](compiler-error-c3054.md)|目前在泛型類別或函式中不支援 '#pragma omp parallel'|
|[編譯器錯誤 C3055](compiler-error-c3055.md)|'*識別碼*': 符號必須先使用在 'threadprivate' 指示詞中被參考|
|[編譯器錯誤 C3056](compiler-error-c3056.md)|'*識別碼*': 符號不在相同範圍和 'threadprivate' 指示詞|
|[編譯器錯誤 C3057](compiler-error-c3057.md)|'*識別碼*': 目前不支援 'threadprivate' 符號的動態初始設定|
|[編譯器錯誤 C3058](compiler-error-c3058.md)|'*識別碼*': 符號使用在 'copyin' 子句之前未宣告為 'threadprivate'|
|[編譯器錯誤 C3059](compiler-error-c3059.md)|'*識別碼*': 'threadprivate' 符號不可使用'*子句*' 子句|
|[編譯器錯誤 C3060](compiler-error-c3060.md)|'*識別碼*': 不可使用限定的名稱 （它可能只可以宣告） 在類別中定義 friend 函式|
|編譯器錯誤 C3061|運算子 '*運算子*': 不允許用於列舉型別'*類型*'的基礎型別'*類型*'|
|[編譯器錯誤 C3062](compiler-error-c3062.md)|'*識別碼*': 列舉值需要值，因為基礎類型是'*類型*'|
|[編譯器錯誤 C3063](compiler-error-c3063.md)|運算子 '*運算子*': 所有運算元必須都具有相同的列舉類型|
|編譯器錯誤 C3064|'*識別碼*': 必須是簡單類型，或者可解析|
|[編譯器錯誤 C3065](compiler-error-c3065.md)|在非類別範圍不允許屬性宣告|
|[編譯器錯誤 C3066](compiler-error-c3066.md)|有多種方法，就可以呼叫此類型的物件具備這些引數|
|編譯器錯誤 C3067|初始設定式清單不能與內建運算子]|
|[編譯器錯誤 C3068](compiler-error-c3068.md)|'*識別碼*': 'naked' 函式不能包含需要的物件會回溯發生 c + + 例外狀況|
|[編譯器錯誤 C3069](compiler-error-c3069.md)|運算子 '*運算子*': 不允許列舉類型|
|[編譯器錯誤 C3070](compiler-error-c3070.md)|'*識別碼*': 屬性沒有 'set' 方法|
|[編譯器錯誤 C3071](compiler-error-c3071.md)|運算子 '*運算子*' 只可以套用至 ref 類別或實值類型的執行個體|
|[編譯器錯誤 C3072](compiler-error-c3072.md)|運算子 '*運算子*' 無法套用至 ref 類別使用一元 '%' 運算子將 ref 的執行個體類別控制代碼類型的執行個體|
|[編譯器錯誤 C3073](compiler-error-c3073.md)|'*識別碼*': ref 類別沒有使用者定義的複製建構函式|
|編譯器錯誤 C3074|無法使用括號括住的初始設定式初始化陣列|
|[編譯器錯誤 C3075](compiler-error-c3075.md)|'*識別碼*': 您無法內嵌執行個體的參考類型，'*類型*'，在實值類型|
|[編譯器錯誤 C3076](compiler-error-c3076.md)|'*識別碼*': 您無法內嵌執行個體的參考類型，'*類型*'，原生類型中|
|[編譯器錯誤 C3077](compiler-error-c3077.md)|'*識別碼*': 完成項只能是參考類型的成員|
|編譯器錯誤 C3078|新的運算式中必須指定陣列大小|
|編譯器錯誤 C3079|初始設定式清單不能做為此指派運算子的右運算元|
|[編譯器錯誤 C3080](compiler-error-c3080.md)|'*finalizer*': 完成項不能有儲存類別規範|
|編譯器錯誤 C3081|已過時。|
|編譯器錯誤 C3082|已過時。|
|[編譯器錯誤 C3083](compiler-error-c3083.md)|'*識別碼*': 左邊的符號 '::' 必須是類型|
|[編譯器錯誤 C3084](compiler-error-c3084.md)|'*識別碼*': 解構函式/完成項不可為'*關鍵字*'|
|[編譯器錯誤 C3085](compiler-error-c3085.md)|'*識別碼*': 建構函式不能是'*關鍵字*'|
|編譯器錯誤 C3086|找不到 'std:: initializer_list': 您需要 #include < initializer_list >|
|[編譯器錯誤 C3087](compiler-error-c3087.md)|'*識別碼*': 呼叫的'*宣告*' 已將此成員初始化|
|編譯器錯誤 C3088|'*類別*': 屬性建構函式必須有具名型式引數|
|編譯器錯誤 C3089|'*識別碼*': 參數名稱不符合任何資料成員的名稱|
|編譯器錯誤 C3090|'*類別*': 屬性類別不可做為樣板|
|編譯器錯誤 C3091|'*類別*': 屬性類別不能有基底類別|
|編譯器錯誤 C3092|'*類別*': 屬性類別成員不得為位元欄位、 'static' 或 'const'|
|編譯器錯誤 C3093|'*類型*': 不允許屬性類別成員的型別'*成員*'|
|[編譯器錯誤 C3094](compiler-error-c3094.md)|'*屬性*': 不允許匿名使用|
|[編譯器錯誤 C3095](compiler-error-c3095.md)|'*屬性*': 屬性不能重複。|
|[編譯器錯誤 C3096](compiler-error-c3096.md)|'*屬性*': 只能用於屬性類別的資料成員上允許屬性|
|[編譯器錯誤 C3097](compiler-error-c3097.md)|'*屬性*': 以設定屬性的領域' 組件:' 或 ' 模組:'|
|編譯器錯誤 C3098|'*識別碼*': 屬性有任何使用者定義建構函式|
|[編譯器錯誤 C3099](compiler-error-c3099.md)|'*關鍵字*': 使用 [system:: attributeusageattribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute] 的 managed/WinRT 屬性|
