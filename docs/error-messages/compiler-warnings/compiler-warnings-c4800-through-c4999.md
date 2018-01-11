---
title: "編譯器警告 C4800 透過 C5999 |Microsoft 文件"
ms.date: 11/17/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C4806
- C4807
- C4808
- C4809
- C4810
- C4811
- C4812
- C4813
- C4816
- C4817
- C4822
- C4825
- C4827
- C4837
- C4840
- C4841
- C4842
- C4872
- C4880
- C4881
- C4882
- C4900
- C4910
- C4912
- C4913
- C4916
- C4918
- C4920
- C4921
- C4925
- C4926
- C4932
- C4934
- C4935
- C4936
- C4937
- C4938
- C4939
- C4944
- C4947
- C4950
- C4951
- C4952
- C4953
- C4954
- C4955
- C4956
- C4957
- C4958
- C4959
- C4960
- C4961
- C4962
- C4963
- C4966
- C4970
- C4971
- C4972
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4997
- C4998
- C4999
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5038
dev_langs: C++
ms.assetid: c3182430-8b3b-4ab2-a532-5cd436707dc8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6f3c9a15c61a859564bb5613a3b8059cb011ca80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warnings-c4800-through-c5999"></a>編譯器警告 C4800 透過 C5999

文件的本節文章說明編譯器所產生的警告訊息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告訊息

|警告|訊息|
|-------------|-------------|
|[編譯器警告 (層級 3) C4800](compiler-warning-level-3-c4800.md)|'type': 值強制設 bool 'true' 或 'false' （效能警告）|
|[編譯器警告 (層級 1) C4803](compiler-warning-level-1-c4803.md)|'method': 產生的方法具有不同的儲存類別不同的事件 'event'|
|[編譯器警告 (層級 1) C4804](compiler-warning-level-1-c4804.md)|'operation': 不安全的類型 'bool' 作業中使用|
|[編譯器警告 (層級 1) C4805](compiler-warning-level-1-c4805.md)|'operation': 不安全的混用類型 'type' 和類型 'type' 中的作業|
|編譯器警告 （層級 1） C4806|'operation': 不安全的作業： 類型 'type' 升級為類型 'type' 沒有值可以等於所給的常數|
|編譯器警告 （層級 1） C4807|'operation': 不安全混用類型 'type' 和類型 'type' 的帶正負號的位元欄位|
|編譯器警告 （層級 1） C4808|case 'value' 不是類型的有效 'bool' 切換條件的值|
|編譯器警告 （層級 1） C4809|switch 陳述式有重複的 'default' 標籤。提供所有可能的 'case' 標籤|
|編譯器警告 （層級 1） C4810|pragma pack(show) 的值 == n|
|編譯器警告 （層級 1） C4811|pragma conform(forScope, show) 的值 == value|
|編譯器警告 （層級 1） C4812|過時的宣告樣式：請用 'new_syntax' 代替|
|編譯器警告 （層級 1） C4813|'function': 區域類別的 friend 函式必須先前已宣告|
|編譯器警告 （層級 4） C4816|'param': 參數具有大小為零的陣列 （除非物件傳址方式傳遞） 將被截斷的|
|編譯器警告 （層級 1） C4817|'member': 不合法使用 '。 ' 存取這個成員。編譯器 '->' 取代|
|[編譯器警告 (層級 1) C4819](compiler-warning-level-1-c4819.md)|檔案包含無法在目前字碼頁 (數字) 中表示的字元。 若要避免資料遺失 Unicode 格式儲存檔案|
|[編譯器警告 (層級 4) C4820](compiler-warning-level-4-c4820.md)|在成員建構 'member_name' 之後加入 'bytes' 位元組填補|
|[編譯器警告 (層級 1) C4821](compiler-warning-level-1-c4821.md)|無法判斷 Unicode 編碼類型，請使用簽章 (BOM) 儲存檔案|
|編譯器警告 （層級 1） C4822|'member function': 區域類別成員函式沒有主體|
|[編譯器警告 (層級 3) C4823](compiler-warning-level-3-c4823.md)|'function': 使用 pin 指標但回溯語意不會啟用。 請考慮使用 /EHa|
|編譯器警告 （層級 2） C4826|從轉換 '*type1*'to'*type2*' 是帶正負號擴充。 這可能導致意外發生執行階段行為。|
|編譯器警告 （層級 3） C4827|具有 0 個參數的公用 'ToString' 方法應該標記為 virtual，並覆寫|
|[編譯器警告 (層級 1) C4829](compiler-warning-level-1-c4829.md)|函式 main 的參數可能不正確。 請考慮 ' int main (platform:: array\<platform:: string ^ > ^ argv)'|
|[編譯器警告 (層級 1) C4835](compiler-warning-level-1-c4835.md)|'variable': 匯出資料的初始設定式將不會執行，直到主機組件中第一次執行受管理的程式碼|
|編譯器警告 （層級 4） C4837|偵測到的三併詞: '？*字元*'取代'*字元*'|
|[編譯器警告 (層級 1) C4838](compiler-warning-level-1-c4838.md)|從 'type_1' 轉換為 'type_2' 必須是縮小轉換|
|[編譯器警告 （層級 3） C4839](compiler-warning-level-3-c4839.md)|類別使用非標準*類型*' 當做 variadic 函式的引數|
|編譯器警告 （層級 4） C4840|類別不可移植使用*類型*' 當做 variadic 函式的引數|
|編譯器警告 （層級 4） C4841|使用非標準擴充： 複合成員指示項用於 offsetof|
|編譯器警告 （層級 4） C4842|'offsetof' 套用至使用多重繼承類型的結果不保證編譯器版本之間保持一致|
|[編譯器警告 （錯誤） C4867](compiler-warning-c4867.md)|'function': 函式呼叫遺漏引數清單。使用 '呼叫' 建立成員的指標|
|[編譯器警告 （層級 4） C4868](compiler-warning-c4868.md)|'_檔案_(*line_number*)' 編譯器不會強制執行括號初始設定清單中的左到右評估順序|
|編譯器警告 （層級 2） C4872|浮點除數為零編譯呼叫圖表 parallel_for_each 時偵測到: '*位置*'|
|編譯器警告 （層級 1） C4880|從 'const type_1' 轉換成 'type_2': 轉型常數性的指標或參考可能會導致未定義的行為在 amp 限制函式|
|編譯器警告 （層級 4） C4881|建構函式和 （或） 解構函式將不會叫用 tile_static 變數 'variable'|
|編譯器警告 （層級 1） C4882|將具有非常數呼叫運算子函式傳遞給 concurrency:: parallel_for_each 已被取代|
|編譯器警告 C4900|'Tool1' 版本 'version1' 和 'tool2' 版本 'version2' 之間的 Il 不符|
|[編譯器警告 (層級 1) C4905](compiler-warning-level-1-c4905.md)|寬字串常值轉換成 'LPSTR'|
|[編譯器警告 (層級 1) C4906](compiler-warning-level-1-c4906.md)|字串常值轉換成 'LPWSTR'|
|編譯器警告 （層級 1） C4910|'\<識別碼 >: '__declspec （dllexport）' 和 'extern' 不相容的明確具現化|
|編譯器警告 （層級 1） C4912|'attribute': 屬性在巢狀 UDT 上有未定義的行為，可能受到忽略|
|編譯器警告 （層級 4） C4913|使用者定義的二進位運算子 ',' 存在，但沒有多載可以轉換所有的運算元，使用預設的內建二進位運算子 ','|
|編譯器警告 （層級 1） C4916|為了有 dispid，'*描述*': 必須由介面引入|
|[編譯器警告 (層級 1) C4917](compiler-warning-level-1-c4917.md)|'declarator': GUID 僅能與類別、 介面或命名空間相關聯|
|編譯器警告 （層級 4） C4918|'character': 在 pragma 最佳化清單中有無效的字元|
|編譯器警告 （層級 1） C4920|enum 列舉成員 member_1 = value_1 已經出現在 enum 列舉為 member_2 = value_2|
|編譯器警告 （層級 3） C4921|'*描述*': 屬性值'*屬性*' 不應多次指定|
|編譯器警告 （層級 1） C4925|'method': 不可以從指令碼呼叫 dispinterface 方法|
|編譯器警告 （層級 1） C4926|'identifier': 已定義符號：忽略屬性|
|[編譯器警告 (層級 1) C4927](compiler-warning-level-1-c4927.md)|不合法的轉換。已經隱含套用一個以上的使用者定義轉換|
|[編譯器警告 (層級 1) C4928](compiler-warning-level-1-c4928.md)|不合法的 copy-initialization; 已經隱含套用一個以上的使用者定義的轉換|
|[編譯器警告 (層級 1) C4929](compiler-warning-level-1-c4929.md)|'file': 類型程式庫包含聯集。忽略 'embedded_idl' 限定詞|
|[編譯器警告 (層級 1) C4930](compiler-warning-level-1-c4930.md)|'原型': 未呼叫原型函式 （是變數定義？）|
|[編譯器警告 (層級 4) C4931](compiler-warning-level-4-c4931.md)|我們假設已針對 number 位元指標建置類型程式庫|
|編譯器警告 （層級 4） C4932|__identifier (*識別碼*) 和\__identifier (*識別碼*) 無法分辨|
|編譯器警告 （層級 1） C4934|'__delegate(multicast)' 已被取代，請使用 '\__delegate' 改為|
|編譯器警告 （層級 1） C4935|使用 'access' 修改組件的存取規範|
|編譯器警告 （層級 1，錯誤） C4936|以 /clr 或 /clr:pure 編譯時才支援這個 __declspec|
|編譯器警告 （層級 4） C4937|難以辨別 'text1' 和 'text2' 是否為 'directive' 的引數|
|編譯器警告 （層級 4） C4938|'var': 浮點削減變數可能會造成不一致的結果，在 /fp: strict 或 #pragma fenv_access 之下|
|編譯器警告 C4939|#pragma vtordisp 已被取代，在未來的 Visual C++ 發行版本中將會移除|
|編譯器警告 （層級 1） C4944|'symbol': 無法匯入從 'assembly1' 的符號： 因為在目前範圍中已經有 'symbol'|
|[編譯器警告 (層級 1) C4945](compiler-warning-level-1-c4945.md)|'symbol': 無法匯入從 'assembly1' 的符號： 因為 'symbol' 已匯入從另一個組件 'assembly2'|
|[編譯器警告 (層級 1) C4946](compiler-warning-level-1-c4946.md)|在關聯的類別之間使用的 reinterpret_cast：'class1' 和 'class2'|
|編譯器警告 （層級 1） C4947|'type_or_member': 標記為過時|
|[編譯器警告 (層級 2) C4948](compiler-warning-level-2-c4948.md)|'accessor' 的傳回型別不符合對應 setter 的最後一個參數類型|
|[編譯器警告 (層級 1 和層級 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|pragma 'managed' 和 'unmanaged' 時才有意義的編譯 ' / /clr [: 選項]'|
|編譯器警告 （層級 1，錯誤） C4950|'type_or_member': 標記為過時|
|編譯器警告 （層級 1） C4951|由於已收集設定檔資料，因此 'function' 已編輯，但未使用函式設定檔資料|
|編譯器警告 （層級 1） C4952|'function': 在程式資料庫 'pgd_file' 中找到任何分析資料|
|編譯器警告 （層級 1） C4953|已經編輯內嵌項 'function'，因為已收集分析資料，未使用分析資料|
|編譯器警告 C4954|'function': 未分析 （包含 __int64 switch 運算式）|
|編譯器警告 C4955|'import2': 忽略; 匯入已從 'import1' 匯入|
|編譯器警告 （層級 1，錯誤） C4956|'type': 這個類型不是可驗證|
|編譯器警告 （層級 1，錯誤） C4957|'cast': 從 '從 '轉換成運算 'cast_to' 的明確轉換不是可驗證|
|編譯器警告 （層級 1，錯誤） C4958|'operation': 指標算術不是可驗證|
|編譯器警告 （層級 1，錯誤） C4959|無法在 /clr: safe 中定義 unmanaged 的類型 'type'，因為存取它的成員會產生無法驗證程式碼|
|編譯器警告 （層級 4） C4960|'function' 太大而無法分析|
|編譯器警告 （層級 1） C4961|沒有任何分析資料合併到 '.pgd 檔' 中，特性指引最佳化已停用|
|編譯器警告 （層級 4） C4962|'function': 特性指引最佳化已停用，因為最佳化導致分析資料變成不一致|
|編譯器警告 （層級 1） C4963|'*描述*': 找不到分析資料; 檢測建置中使用了不同的編譯器選項|
|[編譯器警告 (層級 1) C4964](compiler-warning-level-1-c4964.md)|不指定任何最佳化選項;將不會收集設定檔資訊|
|[編譯器警告 (層級 1) C4965](compiler-warning-level-1-c4965.md)|隱含 box 的整數 0;請使用 nullptr 或明確轉換|
|編譯器警告 （層級 1） C4966|'*函式*' 有 __code_seg 註釋不支援的區段名稱、 註釋已忽略|
|編譯器警告 C4970|委派建構函式： 目標物件會忽略，因為 '*類型*' 是靜態的|
|編譯器警告 （層級 1） C4971|引數的順序：\<目標物件 >，\<目標函式 > 委派建構函式已被取代，請使用\<目標函式 >，\<目標物件 ="">|
|編譯器警告 （層級 1，錯誤） C4972|直接修改或將 Unbox 作業的結果視為左值，將無法驗證|
|編譯器警告 （層級 1） C4973|'*符號*': 標記為已被取代|
|編譯器警告 （層級 1） C4974|'*符號*': 標記為已被取代|
|編譯器警告 （層級 3） C4981|Warbird： 函式 '*函式*' 標記為 __forceinline 無法內嵌，因為它包含例外狀況語意|
|編譯器警告 （層級 3） C4985|符號名稱 ': 屬性不存在先前的宣告。|
|[編譯器警告 C4986](compiler-warning-c4986.md)|'*宣告*': 例外狀況規格與上一個宣告不符|
|編譯器警告 （層級 4） C4987|使用非標準的擴充：'throw (...)'|
|編譯器警告 （層級 4） C4988|'*變數*': 變數宣告為類別/函式範圍外|
|編譯器警告 （層級 4） C4989|'*類型*': 類型含有衝突的定義。|
|編譯器警告 （層級 3） C4990|Warbird:*訊息*|
|編譯器警告 （層級 3） C4991|Warbird： 函式 '*函式*' 標記為 __forceinline 無法內嵌，因為被內嵌者的保護層級大於父代|
|編譯器警告 （層級 3） C4992|Warbird： 函式 '*函式*' 標記為 __forceinline 無法內嵌，因為它包含內嵌組譯碼無法保護|
|[編譯器警告 (層級 3) C4995](compiler-warning-level-3-c4995.md)|'function': 名稱被標示為已被取代的 #pragma|
|[編譯器警告 (層級 3) C4996](compiler-warning-level-3-c4996.md)|'*描述*':*訊息*|
|編譯器警告 （層級 1） C4997|'class': coclass 未實作 COM 介面或虛擬介面|
|編譯器警告 （層級 1） C4998|預期失敗：*期望*(*值*)|
|編譯器警告 C4999|未知警告，請選擇 Visual c + + 說明 功能表上的技術支援 命令或開啟技術支援說明檔，如需詳細資訊|
|編譯器警告 C5022|'*類型*': 多個移動建構函式指定|
|編譯器警告 C5023|'*類型*': 指定多個 move 指派運算子|
|編譯器警告 （層級 4） C5024|'*類型*': move 建構函式已隱含定義為已刪除|
|編譯器警告 （層級 4） C5025|'*類型*': move 指派運算子已隱含定義為已刪除|
|編譯器警告 （層級 1 和層級 4） C5026|'*類型*': move 建構函式已隱含定義為已刪除|
|編譯器警告 （層級 1 和層級 4） C5027|'*類型*': move 指派運算子已隱含定義為已刪除|
|編譯器警告 （層級 1） C5028|'*名稱*': 在先前的宣告中指定的對齊方式 (*數目*) 定義中未指定|
|編譯器警告 （層級 4） C5029|使用非標準擴充： c + + 中的對齊屬性的變數、 資料成員及標記類型只適用於|
|編譯器警告 （層級 3） C5030|屬性 '*屬性*' 無法辨識|
|編譯器警告 （層級 4） C5031|#pragma warning （pop): 可能不相符，快顯警告狀態推入不同的檔案|
|編譯器警告 （層級 4） C5032|偵測到任何對應 「 #pragma warning （pop 的) #pragma warning|
|編譯器警告 （層級 1） C5033|'*儲存類別*' 不再支援的存放裝置類別|
|編譯器警告 C5034|使用內建函式 '*內建*' 函式會導致*函式*編譯為客體程式碼|
|編譯器警告 C5035|使用功能 '*功能*' 函式會導致*函式*編譯為客體程式碼|
|編譯器警告 （層級 1） C5036|varargs 函式的指標轉換時使用 /hybrid:x86arm64 編譯 '*type1*'to'*type2*'|
|編譯器警告 （錯誤） C5037|'*成員函式*': 類別樣板的成員的行外定義不能有預設引數|
