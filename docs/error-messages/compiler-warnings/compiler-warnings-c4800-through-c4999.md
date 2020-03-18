---
title: 編譯器警告 C4800 至 C5999
ms.date: 04/21/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4916
- C4921
- C4934
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
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
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4916
- C4921
- C4934
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
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
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
ms.openlocfilehash: 4d349ba8a51b324b5262e3e38506015ea198d5e3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438271"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>編譯器警告 C4800 至 C5999

本檔的這一節中的文章說明編譯器所產生的警告訊息子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告訊息

|警告|訊息|
|-------------|------------|
|[編譯器警告（層級4） C4800](compiler-warning-level-3-c4800.md)| 從 '*type*' 隱含轉換為 bool。 可能遺失資訊 |
|[編譯器警告（層級1） C4803](compiler-warning-level-1-c4803.md)|'*method*'：引發方法與事件的 '*event*' 具有不同的儲存類別|
|[編譯器警告（層級1） C4804](compiler-warning-level-1-c4804.md)|'*operation*'：作業中不安全使用類型 ' bool '|
|[編譯器警告（層級1） C4805](compiler-warning-level-1-c4805.md)|'*operation*'：作業中類型 '*type1*' 和類型 '*type2*' 的不安全混合|
|[編譯器警告（層級1） C4806](compiler-warning-level-1-c4806.md)|'*operation*'：不安全的作業：沒有類型 '*type1*' 的值升級為類型 '*type2*'，可以等於指定的常數|
|[編譯器警告（層級1） C4807](compiler-warning-level-1-c4807.md)|'*operation*'：類型 '*type1*' 和已簽署的位欄位類型 '*type2*' 的不安全混合|
|編譯器警告（層級1） C4808|case '*value*' 不是類型 ' bool ' 之 switch 條件的有效值|
|編譯器警告（層級1） C4809|switch 語句有多餘的 ' default ' 標籤;提供所有可能的 ' case ' 標籤|
|[編譯器警告（層級1） C4810](compiler-warning-level-1-c4810.md)|pragma pack(show) 的值 == n|
|[編譯器警告（層級1） C4811](compiler-warning-level-1-c4811.md)|pragma conform(forScope, show) 的值 == value|
|[編譯器警告（層級1） C4812](compiler-warning-level-1-c4812.md)|過時的宣告樣式：請改用 '*new_syntax*'|
|[編譯器警告（層級1） C4813](compiler-warning-level-1-c4813.md)|'*function*'：區域類別的 friend 函式必須先前已宣告|
|[編譯器警告（層級4） C4816](compiler-warning-level-4-c4816.md)|'*param*'：參數具有大小為零且將被截斷的陣列（除非物件是以傳址方式傳遞）|
|[編譯器警告（層級1） C4817](compiler-warning-level-1-c4817.md)|'*member*'：不合法使用 '. ' 存取這個成員;編譯器已取代為 '-> '|
|[編譯器警告（層級1） C4819](compiler-warning-level-1-c4819.md)|檔案包含無法在目前字碼頁 (數字) 中表示的字元。 以 Unicode 格式儲存檔案以防止資料遺失|
|[編譯器警告（層級4） C4820](compiler-warning-level-4-c4820.md)|結構 '*member_name*' 之後加入的 '*bytes*' 位元組填補|
|[編譯器警告（層級1） C4821](compiler-warning-level-1-c4821.md)|無法判斷 Unicode 編碼類型，請以簽章（BOM）儲存檔案|
|[編譯器警告（層級1） C4822](compiler-warning-level-1-c4822.md)|' member function '：區域類別成員函式沒有主體|
|[編譯器警告（層級3） C4823](compiler-warning-level-3-c4823.md)|'*function*'：使用釘選指標，但是未啟用回溯語義。 考慮使用/EHa|
|編譯器警告（層級2） C4826|從 '*type1*' 到 '*type2*' 的轉換已進行正負號擴充。 這可能會導致非預期的執行時間行為。|
|編譯器警告（層級3） C4827|具有0個參數的公用 ' ToString ' 方法應該標記為 virtual 並覆寫|
|[編譯器警告（層級1） C4829](compiler-warning-level-1-c4829.md)|函式 main 的參數可能不正確。 請考慮 ' int main （Platform：： Array\<Platform：： String ^ > ^ argv） '|
|[編譯器警告（層級1） C4835](compiler-warning-level-1-c4835.md)|'*variable*'：在主機元件中第一次執行 managed 程式碼之前，將不會執行已匯出資料的初始化運算式|
|編譯器警告（層級4） C4837|偵測到三並詞： '？？*字元*' 已取代成 '*字元*'|
|[編譯器警告（層級1） C4838](compiler-warning-level-1-c4838.md)|從 '*type_1*' 轉換為 '*type_2*' 需要縮小轉換|
|[編譯器警告（層級3） C4839](compiler-warning-level-3-c4839.md)|以非標準方式使用類別 '*type*' 做為 variadic 函數的引數|
|[編譯器警告（層級4） C4840](compiler-warning-level-4-c4840.md)|以不可攜的方式使用類別 '*type*' 做為 variadic 函數的引數|
|編譯器警告（層級4） C4841|使用的非標準擴充： offsetof 中使用的複合成員指示項|
|編譯器警告（層級4） C4842|套用至使用多重繼承之類型的 ' offsetof ' 結果，在編譯器版本之間不保證一致|
|編譯器警告 C4843|'*type1*'：無法連接到陣列或函數類型的例外狀況處理常式，請改用 '*type2*'|
|編譯器警告 C4844|' export module *module_name*; ' 現在是用來宣告模組介面的慣用語法|
| 編譯器警告（層級4） C4845 | 如果未在命令列上指定 '/d1initall\[0\|1\|2\|3] '，則會忽略 '\_\_declspec （不\_init 全部\_） ' |
| 編譯器警告（層級4） C4846 | '*value*' 不是 '/d1initall ' 的有效引數：已忽略命令列旗標 |
| 編譯器警告（層級4） C4847 | '\_\_declspec （不\_init 全部\_） ' 只能套用至函式、類別類型或區域變數：已忽略 |
| 編譯器警告（層級1） C4848 | 在 c + + 17 和更早版本中支援標準屬性「無\_唯一的\_位址」是廠商擴充功能 |
|[編譯器警告（層級4） C4866](c4866.md)| 編譯器可能不會強制執行由左至右的評估順序來呼叫*operator_name*|
|[編譯器警告（錯誤） C4867](compiler-warning-c4867.md)|'*function*'：函式呼叫遺漏引數清單;使用「*呼叫*」來建立成員的指標|
|[編譯器警告（層級4） C4868](compiler-warning-c4868.md)|'_file_（*line_number*） ' 編譯器可能不會在括弧初始化清單中強制執行由左至右的評估順序|
|編譯器警告（層級2） C4872|為 concurrency：:p arallel_for_each 編譯呼叫圖表時，偵測到浮點除法： '*location*'|
|編譯器警告（層級1） C4880|從 ' const *type_1*' 轉換為 '*type_2*'：從指標或參考轉換掉常數性，可能會導致 amp 限制函式中出現未定義的行為|
|編譯器警告（層級4） C4881|將不會針對 tile_static 變數 '*variable*' 叫用此函式和/或函式呼叫程式|
|編譯器警告（層級1） C4882|將具有非 const 呼叫運算子的函子傳遞至平行存取：:p arallel_for_each 已被取代|
|[編譯器警告 C4900](compiler-warning-level-1-c4900.md)|'*Tool1*' 版本 '*version1*' 與 '*tool2*' 版本 '*version2*' 之間的 Il 不相符|
|[編譯器警告（層級1） C4905](compiler-warning-level-1-c4905.md)|寬字串常值轉換成 'LPSTR'|
|[編譯器警告（層級1） C4906](compiler-warning-level-1-c4906.md)|字串常值轉換成 'LPWSTR'|
|[編譯器警告（層級1） C4910](compiler-warning-level-1-c4910.md)|'\<識別碼 >： ' __declspec （dllexport） ' 和 ' extern ' 在明確具現化上不相容|
|[編譯器警告（層級1） C4912](compiler-warning-level-1-c4912.md)|'*attribute*'：屬性在嵌套 UDT 上有未定義的行為|
|[編譯器警告（層級4） C4913](compiler-warning-level-4-c4913.md)|使用者定義的二進位運算子 ',' 存在，但沒有多載可以轉換所有的運算元，使用預設的內建二進位運算子 ','|
|編譯器警告（層級1） C4916|為了擁有 dispid，'*description*'：必須由介面引進|
|[編譯器警告（層級1） C4917](compiler-warning-level-1-c4917.md)|'*宣告子 '：* GUID 只能與類別、介面或命名空間產生關聯|
|[編譯器警告（層級4） C4918](compiler-warning-level-4-c4918.md)|'*character*'：在 pragma 優化清單中的字元無效|
|[編譯器警告（層級1） C4920](compiler-warning-level-1-c4920.md)|列舉列舉成員 member_1 = value_1 已在 enum 列舉中顯示為 member_2 = value_2|
|編譯器警告（層級3） C4921|'*description*'：屬性值 '*attribute*' 不應指定相乘|
|[編譯器警告（層級1） C4925](compiler-warning-level-1-c4925.md)|'*method*'：無法從腳本呼叫分配介面方法|
|[編譯器警告（層級1） C4926](compiler-warning-level-1-c4926.md)|'*identifier*'：已定義符號：忽略屬性|
|[編譯器警告（層級1） C4927](compiler-warning-level-1-c4927.md)|不合法的轉換;已隱含套用一個以上的使用者定義轉換|
|[編譯器警告（層級1） C4928](compiler-warning-level-1-c4928.md)|不合法的 copy-initialization; 已經隱含套用一個以上的使用者定義的轉換|
|[編譯器警告（層級1） C4929](compiler-warning-level-1-c4929.md)|'*file*'：類型程式庫包含 union;忽略 ' embedded_idl ' 限定詞|
|[編譯器警告（層級1） C4930](compiler-warning-level-1-c4930.md)|'*原型*'：未呼叫原型函式（預期是變數定義嗎？）|
|[編譯器警告（層級4） C4931](compiler-warning-level-4-c4931.md)|我們假設已針對 number 位元指標建置類型程式庫|
|[編譯器警告（層級4） C4932](compiler-warning-level-4-c4932.md)|__identifier （*識別碼*）和 \__identifier （*identifier*）無法區分|
|編譯器警告（層級1） C4934|' __delegate （多播） ' 已被取代，請改用 '\__delegate '|
|[編譯器警告（層級1） C4935](compiler-warning-level-1-c4935.md)|已從 '*access*' 修改元件存取規範|
|[編譯器警告（層級1，錯誤） C4936](compiler-warning-c4936.md)|以 /clr 或 /clr:pure 編譯時才支援這個 __declspec|
|[編譯器警告（層級4） C4937](compiler-warning-level-4-c4937.md)|'*text1*'*和 ' & ' 不*能與 ' 指示詞 *' 的自*變數區別|
|[編譯器警告（層級4） C4938](compiler-warning-level-4-c4938.md)|'*var*'：浮點縮減變數在/fp： strict 或 #pragma 下可能會導致不一致的結果 fenv_access|
|[編譯器警告 C4939](compiler-warning-level-1-c4939.md)|#pragma vtordisp 已被取代，在未來的 Visual C++ 發行版本中將會移除|
|[編譯器警告（層級1） C4944](compiler-warning-level-1-c4944.md)|'*symbol*'：無法從 '*assembly1*' 匯入符號：因為 '*symbol*' 已經存在於目前的範圍中|
|[編譯器警告（層級1） C4945](compiler-warning-level-1-c4945.md)|'*symbol*'：無法從 '*assembly1*' 匯入符號：因為 '*symbol*' 已從另一個元件 '*assembly2*' 匯入|
|[編譯器警告（層級1） C4946](compiler-warning-level-1-c4946.md)|在相關類別之間使用 reinterpret_cast： '*class1*' 和 '*class2*'|
|[編譯器警告（層級1） C4947](compiler-warning-level-1-c4947.md)|'*type_or_member*'：標示為過時|
|[編譯器警告（層級2） C4948](compiler-warning-level-2-c4948.md)|'*存取*子的傳回類型不符合對應 setter 的最後一個參數類型|
|[編譯器警告（層級1和層級4） C4949](compiler-warning-level-1-and-level-4-c4949.md)|pragma ' managed ' 和 ' 非受控 ' 只有在以 '/clr [： option] ' 編譯時才有意義|
|[編譯器警告（層級1，錯誤） C4950](compiler-warning-c4950.md)|'*type_or_member*'：標示為過時|
|[編譯器警告（層級1） C4951](compiler-warning-level-1-c4951.md)|'*function*' 已編輯，因為已收集分析資料，未使用函數設定檔資料|
|[編譯器警告（層級1） C4952](compiler-warning-level-1-c4952.md)|'*function*'：在程式資料庫 '*pgd_file*' 中找不到分析資料|
|[編譯器警告（層級1） C4953](compiler-warning-level-1-c4953.md)|內嵌項 '*function*' 已編輯，因為已收集分析資料，未流量分析資料|
|編譯器警告 C4954|'*function*'：未分析（包含 __int64 switch 運算式）|
|編譯器警告 C4955|'*import2*'：已忽略匯入;已從 '*import1*' 匯入|
|[編譯器警告（層級1，錯誤） C4956](compiler-warning-c4956.md)|'*type*'：這個類型無法驗證|
|[編譯器警告（層級1，錯誤） C4957](compiler-warning-c4957.md)|'*cast*'：從 '*cast_from*' 到 '*cast_to*' 的明確轉換無法驗證|
|[編譯器警告（層級1，錯誤） C4958](compiler-warning-c4958.md)|'*operation*'：指標算術無法驗證|
|[編譯器警告（層級1，錯誤） C4959](compiler-warning-c4959.md)|無法在/clr： safe 中定義非受控類型 '*type*'，因為存取它的成員會產生無法驗證的程式碼|
|[編譯器警告（層級4） C4960](compiler-warning-level-4-c4960.md)|'*function*' 太大，無法進行分析|
|[編譯器警告（層級1） C4961](compiler-warning-c4961.md)|沒有任何分析資料合併到 '.pgd 檔' 中，特性指引最佳化已停用|
|[編譯器警告（層級4） C4962](compiler-warning-c4962.md)|'*function*'：特性指引優化已停用，因為優化導致分析資料變成不一致|
|編譯器警告（層級1） C4963|'*description*'：找不到分析資料;已檢測的組建中使用了不同的編譯器選項|
|[編譯器警告（層級1） C4964](compiler-warning-level-1-c4964.md)|未指定優化選項;將不會收集設定檔資訊|
|[編譯器警告（層級1） C4965](compiler-warning-level-1-c4965.md)|整數0的隱含方塊;使用 nullptr 或明確轉換|
|編譯器警告（層級1） C4966|'*function*' 具有具有不支援之區段名稱的 __code_seg 注釋，已忽略注釋|
|編譯器警告 C4970|委派的函式：因為 '*type*' 是靜態的，所以已忽略目標物件|
|編譯器警告（層級1） C4971|引數順序： \<目標物件 >，\<> for 委派的目標函式已被取代，請使用 \<目標函數 >，\<目標物件 = "" >|
|[編譯器警告（層級1，錯誤） C4972](compiler-warning-c4972.md)|直接修改或將 Unbox 作業的結果視為左值，將無法驗證|
|編譯器警告（層級1） C4973|'*symbol*'：標示為已被取代|
|編譯器警告（層級1） C4974|'*symbol*'：標示為已被取代|
|編譯器警告（層級3） C4981|Warbird：標記為 __forceinline 的函式 '*function*' 不是內嵌的，因為它包含例外狀況的語義|
|[編譯器警告 C4984](compiler-warning-c4984.md)|' if constexpr ' 是 c + + 17 語言延伸模組|
|[編譯器警告（層級4） C4985](compiler-warning-level-4-c4985.md)|'*symbol_name*'：屬性不存在先前的宣告中。|
|[編譯器警告 C4986](compiler-warning-c4986.md)|'*宣告 '：* 例外狀況規格與上一個宣告不符|
|編譯器警告（層級4） C4987|使用非標準的擴充：'throw (...)'|
|編譯器警告（層級4） C4988|'*variable*'：變數已在類別/函式範圍外宣告|
|編譯器警告（層級4） C4989|'*type*'：類型具有衝突的定義。|
|編譯器警告（層級3） C4990|Warbird：*訊息*|
|編譯器警告（層級3） C4991|Warbird：標記為 __forceinline 的函式 '*function*' 未內嵌，因為內嵌項的保護層級大於父系|
|編譯器警告（層級3） C4992|Warbird：已將函式 '*function*' 標記為 __forceinline 未內嵌，因為它包含無法保護的內嵌元件|
|[編譯器警告（層級3） C4995](compiler-warning-level-3-c4995.md)|'*function*'：名稱已標記為 #pragma 已被取代|
|[編譯器警告（層級3） C4996](compiler-warning-level-3-c4996.md)|' 已*過時-* 宣告 '：淘汰 *-訊息*（或「已被宣告為已淘汰」）|
|[編譯器警告（層級1） C4997](compiler-warning-level-1-c4997.md)|'*class*'： coclass 不會執行 COM 介面或虛擬介面|
|編譯器警告（層級1） C4998|預期失敗：*預期*（*值*）|
|[編譯器警告 C4999](compiler-warning-level-1-c4999.md)|不明警告請選擇視覺效果C++ [說明] 功能表上的 [技術支援] 命令，或開啟技術支援說明檔以取得詳細資訊|
|編譯器警告 C5022|'*type*'：指定了多個移動的構造函式|
|編譯器警告 C5023|'*type*'：指定了多個移動指派運算子|
|編譯器警告（層級4） C5024|'*type*'： move 函數已隱含定義為 deleted|
|編譯器警告（層級4） C5025|'*type*'：移動指派運算子已隱含定義為刪除|
|編譯器警告（層級1和層級4） C5026|'*type*'： move 函數已隱含定義為 deleted|
|編譯器警告（層級1和層級4） C5027|'*type*'：移動指派運算子已隱含定義為刪除|
|編譯器警告（層級1） C5028|'*name*'：定義中未指定先前宣告（*數位*）中指定的對齊|
|編譯器警告（層級4） C5029|使用非標準的擴充：中C++的對齊屬性僅適用于變數、資料成員和標記類型|
|編譯器警告（層級3） C5030|無法辨識屬性 '*attribute*'|
|編譯器警告（層級4） C5031|#pragma 警告（pop）：可能不相符，彈出的警告狀態推入了不同的檔案|
|編譯器警告（層級4） C5032|偵測到 #pragma 警告（push），但沒有對應的 #pragma 警告（pop）|
|編譯器警告（層級1） C5033|「*儲存類別*」已不再是支援的儲存類別|
|編譯器警告 C5034|使用內建的 '*內部*' 會導致函式函式*編譯為來賓*程式碼|
|編譯器警告 C5035|使用功能「*功能*」*會將函*式函式編譯為來賓程式碼|
|編譯器警告（層級1） C5036|以/hybrid： x86arm64 '*type1*' 編譯為 '*type2*' 時的 varargs 函數指標轉換|
|編譯器警告（錯誤） C5037|'*member 函數*'：類別樣板成員的非正規定義不能有預設引數|
|[編譯器警告（層級4） C5038](c5038.md)|資料成員 '*member1*' 將會在資料成員 '*member2*' 之後初始化|
|編譯器警告（層級4） C5039|'*function*'：可能擲回函式的指標或參考，而該函式會傳遞至-EHc 底下的 extern C 函數。 如果此函式擲回例外狀況，則可能會發生未定義的行為。|
|編譯器警告（層級3） C5040|動態例外狀況規格僅適用于 c + + 14 和更早版本;視為 noexcept （false）|
|編譯器警告（層級1） C5041|'*definition*'：不需要 constexpr 靜態資料成員的非正規定義，而且在 c + + 17 中已被取代|
|編譯器警告（層級3） C5042|'*宣告 '：* 在區塊範圍中的函式宣告不能在 standard C++中指定為 ' inline ';移除 ' inline ' 規範|
|編譯器警告（層級2） C5043|'*規格*'：例外狀況規格與上一個宣告不符|
|編譯器警告（層級4） C5044|命令列選項*選項*的引數指向不存在的路徑 '*path*'|
| [編譯器警告 C5045](c5045.md) | 如果指定/Qspectre 參數，編譯器會插入記憶體負載的 Spectre 緩和措施 |
| [編譯器警告（層級2） C5046](c5046.md) | '*function*'：包含未定義內部連結之類型的符號 |
| 編譯器警告（層級1） C5047 | 如果不支援\_存在模組，則使用非標準 \_\_ |
| 編譯器警告（層級1） C5048 | 使用宏 '*macroname*' 可能會導致不具決定性的輸出 |
| 編譯器警告（層級1） C5049 | '*string*'：內嵌完整路徑可能會導致電腦相依的輸出 |
| 編譯器警告（層級1） C5050 | 匯入模組 '*module_name*' 時可能不相容的環境：*問題* |
| 編譯器警告（層級1） C5100 | \_\_VA\_引數\_\_ 保留供 variadic 宏使用 |
| 編譯器警告（層級1） C5101 | 函式的宏引數清單中的預處理器指示詞使用未定義的行為 |
| 編譯器警告（層級1） C5102 | 忽略不正確命令列巨集定義 '*value*' |
| 編譯器警告（層級1） C5103 | 貼入 '*token1*' 和 '*token2*' 並不會產生有效的前置處理標記 |
| 編譯器警告（層級1） C5104 | 在宏取代清單中找到 '*string1*#*string2*'，您是指 '*string1*"" #*string2*' 嗎？ |
| [編譯器警告（層級1） C5105](c5105.md) | 產生 ' 已定義 ' 的宏展開具有未定義的行為 |
| 編譯器警告（層級1） C5106 | 以不同的參數名稱重新定義宏 |
| 編譯器警告（層級1） C5107 | 遺漏終止 '*char*' 字元 |

## <a name="see-also"></a>另請參閱

[C/C++編譯器和組建工具的錯誤和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[編譯器警告 C4000-至 c5999](compiler-warnings-c4000-c5999.md)
