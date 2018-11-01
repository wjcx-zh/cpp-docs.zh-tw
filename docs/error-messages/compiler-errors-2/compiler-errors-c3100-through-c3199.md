---
title: 編譯器錯誤 C3100 到 C3199
ms.date: 11/17/2017
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
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
ms.openlocfilehash: 72228be503cee9b080ae667f36b042af88161894
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481870"
---
# <a name="compiler-errors-c3100-through-c3199"></a>編譯器錯誤 C3100 到 C3199

文件的本節文章會說明編譯器所產生的錯誤訊息的子集。

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
|[編譯器錯誤 C3106](compiler-error-c3106.md)|'*屬性*': 未具名引數必須在具名引數的前面|
|編譯器錯誤 C3107|'*屬性*': 無法定義原生屬性的成員函式|
|編譯器錯誤 C3108|無法推算類型，因為不是運算式的初始設定式清單。|
|編譯器錯誤 C3109|'*識別碼*': 介面方法必須使用 '__stdcall' 或 '__cdecl' 呼叫慣例|
|[編譯器錯誤 C3110](compiler-error-c3110.md)|'*函式*': 無法多載 COM 介面方法|
|編譯器錯誤 C3111|初始設定式清單不能做為範本參數的預設引數|
|編譯器錯誤 C3112|'*介面*': 介面只可以宣告在全域或命名空間範圍|
|[編譯器錯誤 C3113](compiler-error-c3113.md)|'介面/enum' 不可為範本/泛型|
|[編譯器錯誤 C3114](compiler-error-c3114.md)|'*識別碼*': 不是有效的具名屬性引數|
|[編譯器錯誤 C3115](compiler-error-c3115.md)|'*屬性*': 這個屬性不允許'*建構*'|
|[編譯器錯誤 C3116](compiler-error-c3116.md)|'*規範*': 介面方法的無效儲存類別|
|[編譯器錯誤 C3117](compiler-error-c3117.md)|'*介面*': 介面只可以有一個基底類別|
|[編譯器錯誤 C3118](compiler-error-c3118.md)|'*介面*': 介面不支援虛擬繼承|
|編譯器錯誤 C3119|不允許 alignas(void)|
|[編譯器錯誤 C3120](compiler-error-c3120.md)|'*識別碼*': 介面方法無法取得變數引數清單|
|[編譯器錯誤 C3121](compiler-error-c3121.md)|無法變更類別的 GUID*類別*'|
|編譯器錯誤 C3122|'*介面*': WinRT 泛型介面不能有 GUID|
|編譯器錯誤 C3123|WinRT 泛型介面不能有條件約束|
|編譯器錯誤 C3124|'signed char' 不是有效的 WinRT 資料類型。 請使用 'unsigned 的 char'、 'wchar_t' signed 的 short' 代替。|
|編譯器錯誤 C3125|'*型別*': 類型不能直接或間接衍生自 'Platform:: exception'|
|[編譯器錯誤 C3126](compiler-error-c3126.md)|無法定義等位 '*union*'內管理/WinRT 類型'*型別*'|
|編譯器錯誤 C3127|'*型別*':'*特性*' 特性只能用於 WinRT ref 類別上|
|編譯器錯誤 C3128|'*型別*'並沒有由引入的 vtable'*型別*'|
|編譯器錯誤 C3129|'*型別*': __default_vptr_for_base 只能在本機定義的多型型別和基底|
|[編譯器錯誤 C3130](compiler-error-c3130.md)|編譯器內部錯誤： 無法寫入插入程式碼區塊至 PDB|
|[編譯器錯誤 C3131](compiler-error-c3131.md)|專案必須要有 'name' 屬性 'module' 屬性|
|[編譯器錯誤 C3132](compiler-error-c3132.md)|'*參數*': 參數陣列只可以套用至類型 '維 managed/WinRT array' 的型式引數|
|[編譯器錯誤 C3133](compiler-error-c3133.md)|無法將屬性套用至 c + + varargs|
|[編譯器錯誤 C3134](compiler-error-c3134.md)|'*值*': 屬性引數的值'*引數*'沒有有效的型別'*型別*'|
|[編譯器錯誤 C3135](compiler-error-c3135.md)|'*識別碼*': 屬性不能有 'const' 或 'volatile' 類型|
|[編譯器錯誤 C3136](compiler-error-c3136.md)|'*介面*': COM 介面只可以繼承自其他 COM 介面，'*介面*' 不是 COM 介面|
|[編譯器錯誤 C3137](compiler-error-c3137.md)|'*識別碼*': 無法初始化屬性|
|[編譯器錯誤 C3138](compiler-error-c3138.md)|'*識別碼*':'*屬性*' 介面必須繼承自 IDispatch，或從介面繼承自 IDispatch|
|[編譯器錯誤 C3139](compiler-error-c3139.md)|'*型別*': 無法匯出 UDT 沒有成員|
|[編譯器錯誤 C3140](compiler-error-c3140.md)|在相同編譯單位中不可有多個 'module' 屬性|
|[編譯器錯誤 C3141](compiler-error-c3141.md)|'*介面*': 介面只支援公用繼承|
|[編譯器錯誤 C3142](compiler-error-c3142.md)|'*屬性*': 您無法取得屬性的位址|
|編譯器錯誤 C3143|'*引數*': 屬性引數不能有多個值|
|編譯器錯誤 C3144|'*屬性*': 屬性需要明確的引數，'*引數*' 未命名|
|[編譯器錯誤 C3145](compiler-error-c3145.md)|'*識別碼*': 全域或靜態變數可能不會有管理/WinRT 類型'*型別*'|
|編譯器錯誤 C3146|已過時。|
|編譯器錯誤 C3147|已過時。|
|編譯器錯誤 C3148|已過時。|
|[編譯器錯誤 C3149](compiler-error-c3149.md)|'*型別*': 無法使用此類型此處，而不是最上層'*語彙基元*'|
|[編譯器錯誤 C3150](compiler-error-c3150.md)|'*建構*':'*屬性*' 只能套用至類別、 結構、 介面、 陣列或指標|
|編譯器錯誤 C3151|已過時。|
|[編譯器錯誤 C3152](compiler-error-c3152.md)|'*函式*':'*關鍵字*' 只能套用至類別、 結構或虛擬成員函式|
|[編譯器錯誤 C3153](compiler-error-c3153.md)|'*介面*': 您無法建立介面的執行個體|
|[編譯器錯誤 C3154](compiler-error-c3154.md)|必須是 '、' 省略符號之前。 非逗號分隔的省略符號參數陣列函式不支援。|
|[編譯器錯誤 C3155](compiler-error-c3155.md)|屬性索引子中不允許屬性|
|[編譯器錯誤 C3156](compiler-error-c3156.md)|'*類別*': 不能有受管理/WinRT 類型的區域定義|
|[編譯器錯誤 C3157](compiler-error-c3157.md)|ParamArray 屬性只能套用至最後一個參數|
|編譯器錯誤 C3158|'*函式*':'*關鍵字*' 只能套用至虛擬成員函式|
|[編譯器錯誤 C3159](compiler-error-c3159.md)|'*識別碼*': 不可宣告為陣列的實值類型的指標|
|[編譯器錯誤 C3160](compiler-error-c3160.md)|'*型別*': WinRT managed 類別的資料成員不能有這種類型|
|[編譯器錯誤 C3161](compiler-error-c3161.md)|'*介面*': 巢狀類別、 結構或介面中的介面是不合法; 巢狀類別或結構中的介面是不合法|
|[編譯器錯誤 C3162](compiler-error-c3162.md)|'*型別*': 具有解構函式的參考型別不能做為靜態資料成員的類型'*成員*'|
|[編譯器錯誤 C3163](compiler-error-c3163.md)|'*類別*': 屬性與先前的宣告不一致|
|編譯器錯誤 C3164|已過時。|
|編譯器錯誤 C3165|'*值*': 無法轉換為整數或浮點數的值|
|[編譯器錯誤 C3166](compiler-error-c3166.md)|已過時。 '*型別*': WinRT managed 類別的資料成員不能有類型'*pointer_type*為內部*managed_pointer_type*'|
|[編譯器錯誤 C3167](compiler-error-c3167.md)|無法初始化.NET Framework： 請確定它已安裝|
|[編譯器錯誤 C3168](compiler-error-c3168.md)|'*型別*': 不合法的基礎類型列舉|
|編譯器錯誤 C3169|'*型別*': 無法推算 'auto' 的類型從'*型別*'|
|[編譯器錯誤 C3170](compiler-error-c3170.md)|不能在專案中有不同的模組識別碼|
|[編譯器錯誤 C3171](compiler-error-c3171.md)|'*模組*': 無法在專案中指定不同的模組屬性|
|[編譯器錯誤 C3172](compiler-error-c3172.md)|'*識別碼*': 無法在專案中指定不同的 idl_module 屬性|
|[編譯器錯誤 C3173](compiler-error-c3173.md)|在 idl 合併中版本不符|
|[編譯器錯誤 C3174](compiler-error-c3174.md)|未指定模組屬性|
|[編譯器錯誤 C3175](compiler-error-c3175.md)|'*函式*': 無法從 unmanaged 函式呼叫 managed 類型的方法'*函式*'|
|[編譯器錯誤 C3176](compiler-error-c3176.md)|'*型別*': 無法宣告區域實值類型|
|編譯器錯誤 C3177|您不能包含的類型轉換函式 '*型別*'|
|編譯器錯誤 C3178|'*型別*': 無法在具有預設引數的函式中使用 ParamArray|
|[編譯器錯誤 C3179](compiler-error-c3179.md)|不允許未命名的受管理/WinRT 類型|
|[編譯器錯誤 C3180](compiler-error-c3180.md)|'*型別*': 名稱超過中繼資料的限制'*數目*' 字元|
|[編譯器錯誤 C3181](compiler-error-c3181.md)|'*型別*': 無效的運算元*運算子*|
|[編譯器錯誤 C3182](compiler-error-c3182.md)|'*型別*': using 宣告或存取宣告的成員是管理/WinRT 類型不合法|
|[編譯器錯誤 C3183](compiler-error-c3183.md)|無法定義未命名的類別、 結構或等位內管理/WinRT 類型 '*類別*'|
|編譯器錯誤 C3184|已過時。|
|[編譯器錯誤 C3185](compiler-error-c3185.md)|'typeid': WinRT managed 類型上使用 '*型別*'，使用'*運算子*' 改為|
|編譯器錯誤 C3186|已過時。|
|[編譯器錯誤 C3187](compiler-error-c3187.md)|'*識別碼*': 僅用於函式主體中|
|編譯器錯誤 C3188|已過時。|
|[編譯器錯誤 C3189](compiler-error-c3189.md)|' typeid <*宣告子*>': 此語法已不再支援，typeid< 改為|
|[編譯器錯誤 C3190](compiler-error-c3190.md)|'*declarator*'提供的範本引數不是任何成員函式的明確具現化'*型別*'|
|編譯器錯誤 C3191|已過時。|
|[編譯器錯誤 C3192](compiler-error-c3192.md)|語法錯誤: '^' 不是前置運算子 (這表示您' *'？)|
|編譯器錯誤 C3193|'*建構*': 需要' / clr' 或 ' / ZW' 命令列選項|
|[編譯器錯誤 C3194](compiler-error-c3194.md)|'*型別*': 實值類型不能有指派運算子|
|[編譯器錯誤 C3195](compiler-error-c3195.md)|'*關鍵字*': 已保留，無法用為 ref 類別或實值類型的成員。 您必須使用 'operator' 關鍵字定義 CLR/WinRT 運算子|
|[編譯器錯誤 C3196](compiler-error-c3196.md)|'*識別碼*': 使用一次以上|
|[編譯器錯誤 C3197](compiler-error-c3197.md)|'*關鍵字*': 只能用於定義|
|[編譯器錯誤 C3198](compiler-error-c3198.md)|無效的浮點 pragma 使用方式： fenv_access pragma 只能在精確模式的運作|
|[編譯器錯誤 C3199](compiler-error-c3199.md)|無效的浮點 pragma 使用方式： 非精確模式不支援例外狀況|
