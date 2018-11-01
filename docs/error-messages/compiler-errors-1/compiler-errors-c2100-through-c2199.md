---
title: 編譯器錯誤s C2100 through C2199
ms.date: 11/17/2017
f1_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
helpviewer_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
ms.openlocfilehash: 98e804b7c53eddf239e752f120854439cc3a0b01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546548"
---
# <a name="compiler-errors-c2100-through-c2199"></a>編譯器錯誤s C2100 through C2199

文件的本節文章會說明編譯器所產生的錯誤訊息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>錯誤訊息

|錯誤|訊息|
|-----------|-------------|
|[編譯器錯誤 C2100](compiler-error-c2100.md)|不合法的間接取值|
|[編譯器錯誤 C2101](compiler-error-c2101.md)|不可在常數上使用 '&'|
|[編譯器錯誤 C2102](compiler-error-c2102.md)|'&' 需要左值 (l-value)|
|[編譯器錯誤 C2103](compiler-error-c2103.md)|不可在暫存器變數上使用 '&'|
|[編譯器錯誤 C2104](compiler-error-c2104.md)|在位元欄位上使用 '&' 將被忽略|
|[編譯器錯誤 C2105](compiler-error-c2105.md)|'*運算子*' 需要左值|
|[編譯器錯誤 C2106](compiler-error-c2106.md)|'*運算子*': 左的運算元必須是左值|
|[編譯器錯誤 C2107](compiler-error-c2107.md)|不合法的索引，不允許間接取值|
|[編譯器錯誤 C2108](compiler-error-c2108.md)|註標不是整數類資料類型|
|[編譯器錯誤 C2109](compiler-error-c2109.md)|註標需要陣列或指標類型|
|[編譯器錯誤 C2110](compiler-error-c2110.md)|'+': 無法新增兩個指標|
|[編譯器錯誤 C2111](compiler-error-c2111.md)|'+': 指標的加法必須要使用整數運算元|
|[編譯器錯誤 C2112](compiler-error-c2112.md)|'-': 指標減法必須要使用整數或指標運算元|
|[編譯器錯誤 C2113](compiler-error-c2113.md)|'-': 指標只能和另一個指標相減|
|[編譯器錯誤 C2114](compiler-error-c2114.md)|'*運算子*': 指標在左邊; 右邊需要整數值|
|[編譯器錯誤 C2115](compiler-error-c2115.md)|'*運算子*': 不相容的類型|
|[編譯器錯誤 C2116](compiler-error-c2116.md)|函式參數清單相異|
|[編譯器錯誤 C2117](compiler-error-c2117.md)|'*識別碼*': 陣列界限溢位|
|[編譯器錯誤 C2118](compiler-error-c2118.md)|負註標|
|編譯器錯誤 C2119|'*識別碼*': 類型'*型別*' 無法從空的初始設定式推算|
|[編譯器錯誤 C2120](compiler-error-c2120.md)|所有的類型 'void' 不合法|
|[編譯器錯誤 C2121](compiler-error-c2121.md)|'#': 無效的字元： 可能是巨集展開的結果|
|[編譯器錯誤 C2122](compiler-error-c2122.md)|'*識別碼*': 不合法的名稱清單中的原型參數|
|編譯器錯誤 C2123|'*識別碼*': 別名範本無法明確或部分特製化|
|[編譯器錯誤 C2124](compiler-error-c2124.md)|除以 0 或取除以 0 的餘數|
|編譯器錯誤 C2125|'constexpr' 與不相容 '*語彙基元*'|
|編譯器錯誤 C2126|'*識別碼*' 不能以 'constexpr' 規範宣告|
|編譯器錯誤 C2127|'*識別碼*': 'constexpr' 實體使用非常數運算式的不合法的初始化|
|[編譯器錯誤 C2128](compiler-error-c2128.md)|'*函式*': alloc_text/same_seg 僅適用使用 C 連結的函式|
|[編譯器錯誤 C2129](compiler-error-c2129.md)|靜態函式 '*識別碼*' 宣告但未定義|
|[編譯器錯誤 C2130](compiler-error-c2130.md)|#line 必須有包含檔名，找到字串 '*語彙基元*'|
|編譯器錯誤 C2131|運算式未評估為常數|
|[編譯器錯誤 C2132](compiler-error-c2132.md)|語法錯誤： 未預期的識別項|
|[編譯器錯誤 C2133](compiler-error-c2133.md)|'*識別碼*': 未知的大小|
|[編譯器錯誤 C2134](compiler-error-c2134.md)|'*函式*': 呼叫不會產生常數運算式|
|[編譯器錯誤 C2135](compiler-error-c2135.md)|'*運算子*': 不合法的位元欄位運算|
|編譯器錯誤 C2136|不允許撰寫 API 合約|
|[編譯器錯誤 C2137](compiler-error-c2137.md)|空白的字元常數|
|[編譯器錯誤 C2138](compiler-error-c2138.md)|若要定義列舉型別沒有任何成員不合法|
|[編譯器錯誤 C2139](compiler-error-c2139.md)|'*類別*': 未定義的類別不允許做為引數為編譯器內建類型特性'*特性*'|
|[編譯器錯誤 C2140](compiler-error-c2140.md)|'*型別*': 相依於泛型類型參數的類型不允許做為引數為編譯器內建類型特性'*特性*'|
|[編譯器錯誤 C2141](compiler-error-c2141.md)|陣列大小溢位|
|[編譯器錯誤 C2142](compiler-error-c2142.md)|函式宣告不同，只能在其中一個指定的變數參數|
|[編譯器錯誤 C2143](compiler-error-c2143.md)|語法錯誤： 遺漏 '*token1*'before'*token2*'|
|[編譯器錯誤 C2144](compiler-error-c2144.md)|語法錯誤: '*型別*'必須在'*token2*'|
|[編譯器錯誤 C2145](compiler-error-c2145.md)|語法錯誤： 遺漏 '*語彙基元*' 識別項之前|
|[編譯器錯誤 C2146](compiler-error-c2146.md)|語法錯誤： 遺漏 '*語彙基元*'before '的識別項*識別項*'|
|[編譯器錯誤 C2147](compiler-error-c2147.md)|語法錯誤: '*語彙基元*' 是新的關鍵字|
|[編譯器錯誤 C2148](compiler-error-c2148.md)|陣列的大小總計不得超過 0x*值*位元組|
|[編譯器錯誤 C2149](compiler-error-c2149.md)|'*識別碼*': 具名的位元欄位寬度不可為零|
|[編譯器錯誤 C2150](compiler-error-c2150.md)|'*識別碼*': 位元欄位必須有類型 'int'、 'signed 的 int' unsigned 的 int'|
|[編譯器錯誤 C2151](compiler-error-c2151.md)|一個以上的語言屬性|
|[編譯器錯誤 C2152](compiler-error-c2152.md)|'*識別碼*': 具有不同屬性的函式的指標|
|[編譯器錯誤 C2153](compiler-error-c2153.md)|整數常值必須包含至少一個數字|
|[編譯器錯誤 C2154](compiler-error-c2154.md)|'*型別*': 只能列舉型別可做為引數為編譯器內建類型特性'*特性*'|
|[編譯器錯誤 C2155](compiler-error-c2155.md)|'？ ': 無效的左運算元，必須是算術或指標類型|
|[編譯器錯誤 C2156](compiler-error-c2156.md)|Pragma 必須定義在函式之外|
|[編譯器錯誤 C2157](compiler-error-c2157.md)|'*識別碼*': 在 pragma 清單中使用之前必須先宣告|
|[編譯器錯誤 C2158](compiler-error-c2158.md)|'*型別*': 原生非樣板類型只目前支援 #pragma make_public 指示詞|
|[編譯器錯誤 C2159](compiler-error-c2159.md)|已經指定一個以上的儲存類別|
|[編譯器錯誤 C2160](compiler-error-c2160.md)|'##' 不可以出現在巨集定義開頭|
|[編譯器錯誤 C2161](compiler-error-c2161.md)|'##' 不可以出現在巨集定義結尾|
|[編譯器錯誤 C2162](compiler-error-c2162.md)|必須是巨集型式參數|
|[編譯器錯誤 C2163](compiler-error-c2163.md)|'*函式*': 無法當做內建函式的函式|
|[編譯器錯誤 C2164](compiler-error-c2164.md)|'*函式*': 未宣告的內建函式|
|[編譯器錯誤 C2165](compiler-error-c2165.md)|'*修飾詞*': 無法修飾指向資料指標|
|[編譯器錯誤 C2166](compiler-error-c2166.md)|左值 (l-value) 指定 const 物件|
|[編譯器錯誤 C2167](compiler-error-c2167.md)|'*函式*': 內建函式的實質參數太多|
|[編譯器錯誤 C2168](compiler-error-c2168.md)|'*函式*': 內建函式的實質參數太少|
|[編譯器錯誤 C2169](compiler-error-c2169.md)|'*函式*': 內建函式，不能定義|
|[編譯器錯誤 C2170](compiler-error-c2170.md)|'*識別碼*': 未宣告為函式，不可為內建函式|
|[編譯器錯誤 C2171](compiler-error-c2171.md)|'*運算子*': 不合法類型的運算元'*型別*'|
|[編譯器錯誤 C2172](compiler-error-c2172.md)|'*函式*': 實質參數不是指標： 參數*數目*|
|[編譯器錯誤 C2173](compiler-error-c2173.md)|'*函式*': 實質參數不是指標： 參數*數目*，參數清單*數目*|
|[編譯器錯誤 C2174](compiler-error-c2174.md)|'*函式*': 實質參數具有類型 'void': 參數*數目*，參數清單*數目*|
|[編譯器錯誤 C2175](compiler-error-c2175.md)|'*地區設定*': 無效的地區設定|
|編譯器錯誤 C2176|return 陳述式不能出現在函式的 try 區塊相關聯的建構函式的處理常式|
|[編譯器錯誤 C2177](compiler-error-c2177.md)|常數太大|
|[編譯器錯誤 C2178](compiler-error-c2178.md)|'*識別碼*'不可以宣告使用'*規範*' 規範|
|[編譯器錯誤 C2179](compiler-error-c2179.md)|'*型別*': 屬性引數不可使用類型參數|
|[編譯器錯誤 C2180](compiler-error-c2180.md)|控制運算式具有類型 '*型別*'|
|[編譯器錯誤 C2181](compiler-error-c2181.md)|不合法的 else (沒有相符的 if)|
|[編譯器錯誤 C2182](compiler-error-c2182.md)|'*識別碼*': 類型 'void' 的使用不正確|
|[編譯器錯誤 C2183](compiler-error-c2183.md)|語法錯誤： 轉譯單位是空白|
|[編譯器錯誤 C2184](compiler-error-c2184.md)|'*型別*': __except 運算式不合法的類型|
|[編譯器錯誤 C2185](compiler-error-c2185.md)|'*識別碼*': 不合法的 based 配置|
|[編譯器錯誤 C2186](compiler-error-c2186.md)|'*運算子*': 類型 'void' 的運算元不合法|
|編譯器錯誤 C2187|語法錯誤: '*語彙基元*' 這裡不應有|
|[編譯器錯誤 C2188](compiler-error-c2188.md)|'*數字*': 對於寬字元而言太大|
|編譯器錯誤 C2189|'alignas' 屬性不能套用至位元欄位、 函式參數、 例外狀況宣告或宣告的變數 'register' 儲存類別|
|[編譯器錯誤 C2190](compiler-error-c2190.md)|第一個參數清單比第二個長|
|[編譯器錯誤 C2191](compiler-error-c2191.md)|第二個參數清單比第一個長|
|[編譯器錯誤 C2192](compiler-error-c2192.md)|參數 '*數字*' 宣告不同|
|[編譯器錯誤 C2193](compiler-error-c2193.md)|'*識別碼*': 已經在區段|
|[編譯器錯誤 C2194](compiler-error-c2194.md)|'*識別碼*': 是文字區段|
|[編譯器錯誤 C2195](compiler-error-c2195.md)|'*識別碼*': 是資料區段|
|[編譯器錯誤 C2196](compiler-error-c2196.md)|case 值 '*值*' 已在使用中|
|[編譯器錯誤 C2197](compiler-error-c2197.md)|'*函式*': 呼叫的引數太多|
|[編譯器錯誤 C2198](compiler-error-c2198.md)|'*函式*': 呼叫的引數太少|
|[編譯器錯誤 C2199](compiler-error-c2199.md)|語法錯誤： 找到 '*識別碼*(' 在全域範圍 （預定是宣告嗎？）|