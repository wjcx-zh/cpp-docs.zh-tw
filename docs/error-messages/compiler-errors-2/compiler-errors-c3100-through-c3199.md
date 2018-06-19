---
title: 編譯器錯誤 C3100 透過 C3199 |Microsoft 文件
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
helpviewer_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
dev_langs:
- C++
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 062ab968a51c38e9418a96b0df07eec3ae399ac3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283890"
---
# <a name="compiler-errors-c3100-through-c3199"></a>編譯器錯誤 C3100 透過 C3199

文件的本節文章說明編譯器所產生的錯誤訊息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>錯誤訊息

|錯誤|訊息|
|-----------|-------------|
|[編譯器錯誤 C3100](compiler-error-c3100.md)|'*識別碼*': 未知的屬性限定詞|
|[編譯器錯誤 C3101](compiler-error-c3101.md)|具名的屬性引數不合法的運算式 '*識別碼*'|
|編譯器錯誤 C3102|已過時。|
|[編譯器錯誤 C3103](compiler-error-c3103.md)|'*識別碼*': 重複的具名引數|
|[編譯器錯誤 C3104](compiler-error-c3104.md)|不合法的屬性引數|
|編譯器錯誤 C3105|'*符號*': 不能用做為屬性|
|[編譯器錯誤 C3106](compiler-error-c3106.md)|'*屬性*': 未具名引數必須在具名引數之前|
|編譯器錯誤 C3107|'*屬性*': 無法定義原生屬性的成員函式|
|編譯器錯誤 C3108|無法在初始設定式清單不是運算式，推算的類型|
|編譯器錯誤 C3109|'*識別碼*': 介面方法必須使用 '__stdcall' 或 '__cdecl' 呼叫慣例|
|[編譯器錯誤 C3110](compiler-error-c3110.md)|'*函式*': 無法多載 COM 介面方法|
|編譯器錯誤 C3111|初始設定式清單不可為樣板參數的預設引數|
|編譯器錯誤 C3112|'*介面*': 介面只可以宣告在全域或命名空間範圍|
|[編譯器錯誤 C3113](compiler-error-c3113.md)|'介面/enum' 不可為範本/泛型|
|[編譯器錯誤 C3114](compiler-error-c3114.md)|'*識別碼*': 不是有效的具名屬性引數|
|[編譯器錯誤 C3115](compiler-error-c3115.md)|'*屬性*': 這個屬性不允許'*建構*'|
|[編譯器錯誤 C3116](compiler-error-c3116.md)|'*規範*': 介面方法的儲存類別無效|
|[編譯器錯誤 C3117](compiler-error-c3117.md)|'*介面*': 介面只可以有一個基底類別|
|[編譯器錯誤 C3118](compiler-error-c3118.md)|'*介面*': 介面不支援虛擬繼承|
|編譯器錯誤 C3119|不允許 alignas(void)|
|[編譯器錯誤 C3120](compiler-error-c3120.md)|'*識別碼*': 介面方法無法使用變數引數清單|
|[編譯器錯誤 C3121](compiler-error-c3121.md)|無法變更類別的 GUID*類別*'|
|編譯器錯誤 C3122|'*介面*': WinRT 泛型介面不能有 GUID|
|編譯器錯誤 C3123|WinRT 泛型介面不能有條件約束|
|編譯器錯誤 C3124|'signed char' 不是有效的 WinRT 資料類型。 請使用 'unsigned 的 char'、 'wchar_t' signed 的 short' 代替。|
|編譯器錯誤 C3125|'*類型*': 類型不能直接或間接衍生自 'Platform:: exception'|
|[編譯器錯誤 C3126](compiler-error-c3126.md)|無法定義等位 '*union*'內部 managed/WinRT 類型'*類型*'|
|編譯器錯誤 C3127|'*類型*':'*特性*' 特性只能用於 WinRT ref 類別上|
|編譯器錯誤 C3128|'*類型*'沒有由引入的 vtable'*類型*'|
|編譯器錯誤 C3129|'*類型*': __default_vptr_for_base 只能在本機定義的多型型別和基底|
|[編譯器錯誤 C3130](compiler-error-c3130.md)|編譯器內部錯誤： 無法寫入插入程式碼區塊至 PDB|
|[編譯器錯誤 C3131](compiler-error-c3131.md)|專案必須要有 'name' 屬性為 'module' 屬性|
|[編譯器錯誤 C3132](compiler-error-c3132.md)|'*參數*': 參數陣列只能套用至型別 'WinRT 受管理的一維陣列' 的型式引數|
|[編譯器錯誤 C3133](compiler-error-c3133.md)|無法將屬性套用至 c + + varargs|
|[編譯器錯誤 C3134](compiler-error-c3134.md)|'*值*': 屬性引數的值'*引數*'不是有效的類型'*類型*'|
|[編譯器錯誤 C3135](compiler-error-c3135.md)|'*識別碼*': 屬性不能有 'const' 或 'volatile' 類型|
|[編譯器錯誤 C3136](compiler-error-c3136.md)|'*介面*': COM 介面只可以繼承自其他 COM 介面，'*介面*' 不是 COM 介面|
|[編譯器錯誤 C3137](compiler-error-c3137.md)|'*識別碼*': 無法初始化屬性|
|[編譯器錯誤 C3138](compiler-error-c3138.md)|'*識別碼*':'*屬性*' 介面必須繼承自 IDispatch，或是從 IDispatch 繼承的介面|
|[編譯器錯誤 C3139](compiler-error-c3139.md)|'*類型*': 無法匯出 UDT 沒有成員|
|[編譯器錯誤 C3140](compiler-error-c3140.md)|在相同編譯單位中不能有多個 'module' 屬性|
|[編譯器錯誤 C3141](compiler-error-c3141.md)|'*介面*': 介面只支援公用繼承|
|[編譯器錯誤 C3142](compiler-error-c3142.md)|'*屬性*': 您無法取得屬性的位址|
|編譯器錯誤 C3143|'*引數*': 屬性引數不能有多個值|
|編譯器錯誤 C3144|'*屬性*': 屬性需要明確的引數'*引數*' 未命名|
|[編譯器錯誤 C3145](compiler-error-c3145.md)|'*識別碼*': 全域或靜態變數不能有 managed/WinRT 類型'*類型*'|
|編譯器錯誤 C3146|已過時。|
|編譯器錯誤 C3147|已過時。|
|編譯器錯誤 C3148|已過時。|
|[編譯器錯誤 C3149](compiler-error-c3149.md)|'*類型*': 不能使用這個型別此處卻沒有最上層'*語彙基元*'|
|[編譯器錯誤 C3150](compiler-error-c3150.md)|'*建構*':'*屬性*' 只可以套用至類別、 結構、 介面、 陣列或指標|
|編譯器錯誤 C3151|已過時。|
|[編譯器錯誤 C3152](compiler-error-c3152.md)|'*函式*':'*關鍵字*' 只可以套用至類別、 結構或虛擬成員函式|
|[編譯器錯誤 C3153](compiler-error-c3153.md)|'*介面*': 您無法建立介面的執行個體|
|[編譯器錯誤 C3154](compiler-error-c3154.md)|必須是 '、' 之前省略符號。 非逗號分隔的省略符號參數陣列函式上不支援。|
|[編譯器錯誤 C3155](compiler-error-c3155.md)|屬性索引子中不允許屬性|
|[編譯器錯誤 C3156](compiler-error-c3156.md)|'*類別*': 不能有區域定義的 managed/WinRT 類型|
|[編譯器錯誤 C3157](compiler-error-c3157.md)|ParamArray 屬性只能套用至最後一個參數|
|編譯器錯誤 C3158|'*函式*':'*關鍵字*' 只可以套用至虛擬成員函式|
|[編譯器錯誤 C3159](compiler-error-c3159.md)|'*識別碼*': 實值型別指標的陣列不可以宣告|
|[編譯器錯誤 C3160](compiler-error-c3160.md)|'*類型*': managed WinRT 類別的資料成員不能有這種類型|
|[編譯器錯誤 C3161](compiler-error-c3161.md)|'*介面*': 巢狀類別、 結構或介面中的介面是不合法; 巢狀介面類別或結構中的是不合法|
|[編譯器錯誤 C3162](compiler-error-c3162.md)|'*類型*': 具有解構函式的參考型別不能為靜態資料成員的型別'*成員*'|
|[編譯器錯誤 C3163](compiler-error-c3163.md)|'*類別*': 屬性與上一個宣告不一致|
|編譯器錯誤 C3164|已過時。|
|編譯器錯誤 C3165|'*值*': 無法轉換為整數或浮點數的值|
|[編譯器錯誤 C3166](compiler-error-c3166.md)|已過時。 '*類型*': managed WinRT 類別的資料成員不能有類型'*pointer_type*為內部*managed_pointer_type*'|
|[編譯器錯誤 C3167](compiler-error-c3167.md)|無法初始化.NET Framework： 請確定它已安裝|
|[編譯器錯誤 C3168](compiler-error-c3168.md)|'*類型*': 不合法的基礎類型列舉|
|編譯器錯誤 C3169|'*類型*': 無法推算 'auto' 的類型從'*類型*'|
|[編譯器錯誤 C3170](compiler-error-c3170.md)|無法在專案中有不同的模組識別項|
|[編譯器錯誤 C3171](compiler-error-c3171.md)|'*模組*': 無法在專案中指定不同的模組屬性|
|[編譯器錯誤 C3172](compiler-error-c3172.md)|'*識別碼*': 無法在專案中指定不同的 idl_module 屬性|
|[編譯器錯誤 C3173](compiler-error-c3173.md)|在 idl 合併中版本不符|
|[編譯器錯誤 C3174](compiler-error-c3174.md)|未指定模組屬性|
|[編譯器錯誤 C3175](compiler-error-c3175.md)|'*函式*': 無法從 unmanaged 函式呼叫 managed 類型的方法'*函式*'|
|[編譯器錯誤 C3176](compiler-error-c3176.md)|'*類型*': 無法宣告區域實值類型|
|編譯器錯誤 C3177|您不能包含的類型轉換函式 '*類型*'|
|編譯器錯誤 C3178|'*類型*': 無法在具有預設引數的函式中使用參數陣列|
|[編譯器錯誤 C3179](compiler-error-c3179.md)|不允許未命名的 managed/WinRT 類型|
|[編譯器錯誤 C3180](compiler-error-c3180.md)|'*類型*': 名稱超過中繼資料的限制'*數目*' 字元|
|[編譯器錯誤 C3181](compiler-error-c3181.md)|'*類型*': 無效的運算元*運算子*|
|[編譯器錯誤 C3182](compiler-error-c3182.md)|'*類型*': using 宣告或存取宣告的成員是不合法的 managed/WinRT 類型|
|[編譯器錯誤 C3183](compiler-error-c3183.md)|無法定義未命名的類別、 結構或等位內受管理/WinRT 類型 '*類別*'|
|編譯器錯誤 C3184|已過時。|
|[編譯器錯誤 C3185](compiler-error-c3185.md)|'typeid': managed/WinRT 類型上使用 '*類型*'，使用'*運算子*' 改為|
|編譯器錯誤 C3186|已過時。|
|[編譯器錯誤 C3187](compiler-error-c3187.md)|'*識別碼*': 才可用在函式主體內|
|編譯器錯誤 C3188|已過時。|
|[編譯器錯誤 C3189](compiler-error-c3189.md)|' typeid <*宣告子*>': 這個語法已不再支援，typeid< 代替|
|[編譯器錯誤 C3190](compiler-error-c3190.md)|'*宣告子*'提供的範本引數不是任何成員函式的明確具現化'*類型*'|
|編譯器錯誤 C3191|已過時。|
|[編譯器錯誤 C3192](compiler-error-c3192.md)|語法錯誤: '^' 不是前置運算子 (您是否是指' *'？)|
|編譯器錯誤 C3193|'*建構*': 需要' / clr' 或 ' / ZW' 命令列選項|
|[編譯器錯誤 C3194](compiler-error-c3194.md)|'*類型*': 實值類型不能有指派運算子|
|[編譯器錯誤 C3195](compiler-error-c3195.md)|'*關鍵字*': 已保留，不能當做 ref 類別或實值類型的成員。 您必須使用 'operator' 關鍵字定義 CLR/WinRT 運算子|
|[編譯器錯誤 C3196](compiler-error-c3196.md)|'*識別碼*': 使用超過一次|
|[編譯器錯誤 C3197](compiler-error-c3197.md)|'*關鍵字*': 只能用於定義|
|[編譯器錯誤 C3198](compiler-error-c3198.md)|無效的浮點 pragma 使用方式： fenv_access pragma 只能在精確模式的運作|
|[編譯器錯誤 C3199](compiler-error-c3199.md)|無效的浮點 pragma 使用方式： 非精確模式不支援例外狀況|
